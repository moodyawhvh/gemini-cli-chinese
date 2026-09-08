> 🌐 本文档由 [google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli) 翻译,英文原版见原项目。

# 本地开发指南

本指南介绍如何搭建和使用 Gemini CLI 的本地开发功能。

## 追踪(Tracing)

Gemini CLI 使用 OpenTelemetry(OTel)记录追踪信息,帮助你调试智能体行为。
追踪覆盖了模型调用、工具调度器操作、工具调用等关键事件。

追踪让你深入洞察智能体行为,便于排查复杂问题。启用遥测后会自动采集。

### 查看追踪

你可以通过 Genkit Developer UI、Jaeger 或 Google Cloud 查看追踪。

#### 使用 Genkit

Genkit 提供基于网页的 UI,可查看追踪及其他遥测数据。

1.  **启动 Genkit 遥测服务器:**

    运行以下命令启动 Genkit 服务器:

    ```bash
    npm run telemetry -- --target=genkit
    ```

    脚本会输出 Genkit Developer UI 的地址。例如:
    `Genkit Developer UI: http://localhost:4000`

2.  **运行 Gemini CLI:**

    在另一个终端运行你的 Gemini CLI 命令:

    ```bash
    gemini
    ```

3.  **查看追踪:**

    在浏览器中打开 Genkit Developer UI 地址,进入 **Traces** 标签页查看追踪。

#### 使用 Jaeger

本地开发时可以在 Jaeger UI 中查看追踪。

1.  **启动遥测收集器:**

    在终端运行以下命令,下载并启动 Jaeger 与 OTel 收集器:

    ```bash
    npm run telemetry -- --target=local
    ```

    该命令会为本地遥测配置工作区,并给出 Jaeger UI 链接
    (通常是 `http://localhost:16686`)。

    - **收集器日志:** `~/.gemini/tmp/<projectHash>/otel/collector.log`

2.  **运行 Gemini CLI:**

    在另一个终端运行你的 Gemini CLI 命令:

    ```bash
    gemini
    ```

3.  **查看追踪:**

    运行命令后,在浏览器中打开 Jaeger UI 链接查看追踪。

#### 使用 Google Cloud

你可以用 OpenTelemetry 收集器把遥测数据转发到 Google Cloud Trace,
进行自定义处理或路由。

<!-- prettier-ignore -->
> [!WARNING]
> 使用此方式前,请先完成
> [Google Cloud 遥测前置条件](./cli/telemetry.md#prerequisites)
>(项目 ID、认证、IAM 角色与 API)。

1.  **配置 `.gemini/settings.json`:**

    ```json
    {
      "telemetry": {
        "enabled": true,
        "target": "gcp",
        "useCollector": true
      }
    }
    ```

2.  **启动遥测收集器:**

    运行以下命令启动转发到 Google Cloud 的本地 OTel 收集器:

    ```bash
    npm run telemetry -- --target=gcp
    ```

    脚本会输出在 Google Cloud Console 中查看追踪、指标和日志的链接。

    - **收集器日志:** `~/.gemini/tmp/<projectHash>/otel/collector-gcp.log`

3.  **运行 Gemini CLI:**

    在另一个终端运行你的 Gemini CLI 命令:

    ```bash
    gemini
    ```

4.  **查看日志、指标与追踪:**

    发送提示词后,在 Google Cloud Console 中查看数据。Logs、Metrics 与
    Trace 浏览器的入口链接见
    [遥测文档](./cli/telemetry.md#view-google-cloud-telemetry)。

遥测的更多细节见[遥测文档](./cli/telemetry.md)。

### 在代码中添加追踪

你可以给自己的代码添加追踪,获得更细粒度的埋点。

添加追踪有助于调试和理解执行流程。使用 `runInDevTraceSpan` 函数可以把任意代码段
包进一个追踪 span。

一个基本示例:

```typescript
import { runInDevTraceSpan } from '@google/gemini-cli-core';
import { GeminiCliOperation } from '@google/gemini-cli-core/lib/telemetry/constants.js';

await runInDevTraceSpan(
  {
    operation: GeminiCliOperation.ToolCall,
    attributes: {
      [GEN_AI_AGENT_NAME]: 'gemini-cli',
    },
  },
  async ({ metadata }) => {
    // metadata allows you to record the input and output of the
    // operation as well as other attributes.
    metadata.input = { key: 'value' };
    // Set custom attributes.
    metadata.attributes['custom.attribute'] = 'custom.value';

    // Your code to be traced goes here.
    try {
      const output = await somethingRisky();
      metadata.output = output;
      return output;
    } catch (e) {
      metadata.error = e;
      throw e;
    }
  },
);
```

示例说明:

- `operation`:span 的操作类型,由 `GeminiCliOperation` 枚举表示。
- `metadata.input`:(可选)被追踪操作的输入数据对象。
- `metadata.output`:(可选)被追踪操作的输出数据对象。
- `metadata.attributes`:(可选)要附加到 span 的自定义属性记录。
- `metadata.error`:(可选)操作失败时记录的错误对象。
