> 🌐 本文档由 [google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli) 翻译,英文原版见原项目。

# Gemini CLI:配额与定价

Gemini CLI 提供了覆盖大多数个人开发者使用场景的慷慨免费额度。对于企业或专业用途,
或者需要更高配额时,可以根据认证账号类型选择多种方案。

各订阅方案的高层次对比与配额选择,请见
[套餐页面](https://geminicli.com/plans/)。

## 概览

本文介绍使用不同认证方式时,Gemini CLI 适用的具体配额与定价。

下表汇总了各配额及其限制:

| 认证方式              | 层级 / 订阅                     | 每用户每日最大请求数              |
| :-------------------- | :------------------------------ | :-------------------------------- |
| **Google 账号**       | Gemini Code Assist(个人版)    | 1,000 次请求                      |
|                       | Google AI Pro                   | 1,500 次请求                      |
|                       | Google AI Ultra                 | 2,000 次请求                      |
| **Gemini API key**    | 免费层(未付费)                | 250 次请求                        |
|                       | 按量付费(付费)                | 不定                              |
| **Vertex AI**         | Express 模式(免费)            | 不定                              |
|                       | 按量付费(付费)                | 不定                              |
| **Google Workspace**  | Code Assist Standard            | 1,500 次请求                      |
|                       | Code Assist Enterprise          | 2,000 次请求                      |
|                       | Workspace AI Ultra              | 2,000 次请求                      |

总体上有三类可选:

- 免费使用:适合实验和轻度使用。
- 付费层(固定价格):适合需要更宽裕的每日配额和可预测成本的个人开发者或企业。
- 按量付费:最灵活的方案,适合专业用途、长时间运行的任务,或需要完全掌控用量的
  场景。

请求按每用户每分钟限制,并在高负载时段受服务可用性影响。

## 免费使用

Gemini CLI 从慷慨的免费层起步,非常适合实验和轻度使用。

免费使用受以下限制约束,具体取决于你的授权类型。

### 使用 Google 账号登录(Gemini Code Assist for individuals)

适用于用 Google 账号认证、访问个人版 Gemini Code Assist 的用户,包括:

- 每用户每日最多 1000 次模型请求
- 模型请求由 Gemini CLI 决定,分布在 Gemini 模型家族中

更多信息见
[Gemini Code Assist for Individuals 限额](https://developers.google.com/gemini-code-assist/resources/quotas#quotas-for-agent-mode-gemini-cli)。

### 使用 Gemini API Key 登录(未付费)

使用 Gemini API key 同样可以享受免费层,包括:

- 每用户每日最多 250 次模型请求
- 仅限对 Flash 模型的请求

更多信息见
[Gemini API 速率限制](https://ai.google.dev/gemini-api/docs/rate-limits)。

### 使用 Vertex AI 登录(Express 模式)

Vertex AI 提供无需开通结算的 Express 模式,包括:

- 90 天后需开通结算
- 配额与模型因账号而异,限制各不相同

更多信息见
[Vertex AI Express 模式限额](https://cloud.google.com/vertex-ai/generative-ai/docs/start/express-mode/overview#quotas)。

## 付费层:固定成本获得更高限额

如果初始请求次数用完,可以升级到以下订阅之一,继续使用 Gemini CLI:

### 个人

这些层级适用于个人账号登录。可以访问
[Google One](https://one.google.com/about/plans?hl=en-US&g1_landing_page=0)
核实是否为个人账号:

- 如果是个人账号,你会看到个人控制面板。
- 如果不是,你会看到:"You're currently signed in to your Google Workspace Account."

**支持的层级:** _- 未列出的层级(包括 Google AI Plus)不受支持。_

- [Google AI Pro 与 AI Ultra](https://gemini.google/subscriptions/)。
  推荐个人开发者使用。配额与定价基于固定价格订阅。

  要获得可预测的成本,可以使用 Google 账号登录。

  更多信息见
  [Gemini Code Assist 配额与限制](https://developers.google.com/gemini-code-assist/resources/quotas)

### 通过组织

这些层级适用于使用 Google Workspace 账号登录的场景。

- 核实账号类型:访问
  [Google One 页面](https://one.google.com/about/plans?hl=en-US&g1_landing_page=0)。
- 如果看到 "You're currently signed in to your Google Workspace Account",
  说明你使用的是 workspace 账号。

**支持的层级:** _- 未列出的层级(包括 Workspace AI Standard/Plus 与
AI Expanded)不受支持。_

- [Workspace AI Ultra 访问权限](https://workspace.google.com/products/ai-ultra/)。
- [通过 Google Cloud 购买 Gemini Code Assist 订阅](https://cloud.google.com/gemini/docs/codeassist/overview)。

  配额与定价基于固定价格订阅并分配许可席位。要获得可预测的成本,
  可以使用 Google 账号登录。

  请求限额如下:

  - Gemini Code Assist Standard 版:
    - 每用户每日最多 1500 次模型请求
  - Gemini Code Assist Enterprise 版:
    - 每用户每日最多 2000 次模型请求
  - 模型请求由 Gemini CLI 决定,分布在 Gemini 模型家族中

  [了解更多 Gemini Code Assist 许可限额](https://developers.google.com/gemini-code-assist/resources/quotas#quotas-for-agent-mode-gemini-cli)。

## 按量付费

如果达到每日请求上限,或在升级后仍耗尽了 Gemini Pro 配额,最灵活的方案是切换到
按量付费模式——为实际使用的处理量付费。这是保证服务不中断的推荐路径。

为此,请使用 Gemini API key 或 Vertex AI 登录。

### Vertex AI(常规模式)

面向构建、部署和管理 AI 模型(包括 Gemini)的企业级平台,提供增强的安全性、
数据治理以及与其他 Google Cloud 服务的集成。

- 配额:由动态共享配额系统或预先购买的预配吞吐量决定。
- 成本:按模型与 token 用量计费。

更多信息见
[Vertex AI 动态共享配额](https://cloud.google.com/vertex-ai/generative-ai/docs/resources/dynamic-shared-quota)
和 [Vertex AI 定价](https://cloud.google.com/vertex-ai/pricing)。

### Gemini API key

适合想用 Gemini 模型快速构建应用的开发者,是使用模型最直接的方式。

- 配额:因定价层级而异。
- 成本:因定价层级及模型/token 用量而异。

更多信息见
[Gemini API 速率限制](https://ai.google.dev/gemini-api/docs/rate-limits)、
[Gemini API 定价](https://ai.google.dev/gemini-api/docs/pricing)

需要强调:使用 API key 时按 token/调用付费。对于大量小调用的场景可能更贵,
但它是确保工作流不因配额上限而中断的唯一方式。

## Gemini for Workspace 套餐

这些套餐目前仅适用于 Google 体验提供的 Gemini 网页产品
(例如 Gemini 网页应用或 Flow 视频编辑器),不适用于驱动 Gemini CLI 的 API
使用。未来是否会支持这些套餐仍在积极评估中。

## 查看用量与限额

可以使用 `/stats model` 命令查看当前 token 用量与适用限额。该命令给出当前会话
token 用量的快照,以及当前配额对应的限额信息。

关于 `/stats` 命令及其子命令的更多信息,见
[命令参考](../reference/commands.md#stats)。

会话结束时也会展示一份模型用量摘要。

## 避免高额成本的技巧

使用按量付费方案时,留意用量以避免意外开销。

- **谨慎采纳建议**:在采纳建议之前(尤其是重构大型代码库这类计算密集型任务),
  先想想这是否是性价比最高的做法。
- **使用精确的提示词**:按调用付费,所以要思考获得目标结果的最有效方式。
  一条打磨好的提示词往往能一次调用拿到答案,省去多轮来回交互。
- **监控用量**:会话中使用 `/stats model` 命令跟踪 token 用量,
  实时掌握支出情况。
