> 🌐 本文档由 [google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli) 翻译,英文原版见原项目。

# Gemini CLI 文档

Gemini CLI 把 Gemini 模型的能力直接带进你的终端。可以用它理解代码、自动化任务,
并结合本地项目上下文构建工作流。

## 安装

```bash
npm install -g @google/gemini-cli
```

## 快速上手

即刻开始使用 Gemini CLI。

- **[快速入门](./get-started/index.md):** 你的第一次 Gemini CLI 会话。
- **[安装](./get-started/installation.mdx):** 如何在你的系统上安装 Gemini CLI。
- **[认证](./get-started/authentication.mdx):** 个人账号与企业账号的配置说明。
- **[CLI 速查表](./cli/cli-reference.md):** 常用命令与选项的快速参考。
- **[Gemini CLI 上的 Gemini 3](./get-started/gemini-3.md):** 了解 Gemini CLI 对
  Gemini 3 的支持。

## 使用 Gemini CLI

面向日常开发工作流的用户指南与教程。

- **[文件管理](./cli/tutorials/file-management.md):** 如何处理本地文件与目录。
- **[Agent Skills 入门](./cli/tutorials/skills-getting-started.md):**
  开始使用专业化技能。
- **[管理上下文与记忆](./cli/tutorials/memory-management.md):**
  管理持久化的指令与事实。
- **[执行 Shell 命令](./cli/tutorials/shell-commands.md):** 安全地执行系统命令。
- **[管理会话与历史](./cli/tutorials/session-management.md):**
  恢复、管理与回溯对话。
- **[用 todos 规划任务](./cli/tutorials/task-planning.md):** 在复杂工作流中使用
  todos。
- **[网页搜索与抓取](./cli/tutorials/web-tools.md):** 搜索并抓取网络内容。
- **[设置 MCP 服务器](./cli/tutorials/mcp-setup.md):** 配置 MCP 服务器。
- **[自动化任务](./cli/tutorials/automation.md):** 让任务自动跑起来。

## 功能特性

Gemini CLI 各项能力的技术文档。

- **[扩展](./extensions/index.md):** 用新工具与新能力扩展 Gemini CLI。
- **[Agent Skills](./cli/skills.md):** 针对特定任务使用专业化智能体。
- **[检查点](./cli/checkpointing.md):** 自动会话快照。
- **[无头模式](./cli/headless.md):** 程序化与脚本化接口。
- **[Hooks](./hooks/index.md):** 用脚本自定义 Gemini CLI 行为。
- **[IDE 集成](./ide-integration/index.md):** 把 Gemini CLI 接入你常用的 IDE。
- **[MCP 服务器](./tools/mcp-server.md):** 连接并使用远程智能体。
- **[模型路由](./cli/model-routing.md):** 自动回退的韧性保障。
- **[模型选择](./cli/model.md):** 为需求挑选最合适的模型。
- **[计划模式 🔬](./cli/plan-mode.md):** 以安全的只读模式规划复杂变更。
- **[子智能体 🔬](./core/subagents.md):** 用专门的智能体处理特定任务。
- **[远程子智能体 🔬](./core/remote-agents.md):** 连接并使用远程智能体。
- **[回溯](./cli/rewind.md):** 回退并重放会话。
- **[沙箱](./cli/sandbox.md):** 隔离工具执行。
- **[设置](./cli/settings.md):** 完整配置参考。
- **[遥测](./cli/telemetry.md):** 用量与性能指标详情。
- **[Token 缓存](./cli/token-caching.md):** 性能优化。

## 配置

Gemini CLI 的设置与自定义选项。

- **[自定义命令](./cli/custom-commands.md):** 个性化快捷方式。
- **[企业配置](./cli/enterprise.md):** 专业环境管控。
- **[忽略文件(.geminiignore)](./cli/gemini-ignore.md):** 排除模式参考。
- **[模型配置](./cli/generation-settings.md):** 微调温度、思考预算等生成参数。
- **[项目上下文(GEMINI.md)](./cli/gemini-md.md):** 上下文文件的技术层级。
- **[系统提示词覆盖](./cli/system-prompt.md):** 指令替换逻辑。
- **[主题](./cli/themes.md):** UI 个性化技术指南。
- **[受信任文件夹](./cli/trusted-folders.md):** 安全权限逻辑。

## 参考

深度技术文档与 API 规范。

- **[命令参考](./reference/commands.md):** 详细的斜杠命令指南。
- **[配置参考](./reference/configuration.md):** 设置项与环境变量。
- **[键盘快捷键](./reference/keyboard-shortcuts.md):** 效率技巧。
- **[记忆导入处理器](./reference/memport.md):** Gemini CLI 如何处理来自各处的
  记忆内容。
- **[策略引擎](./reference/policy-engine.md):** 细粒度执行控制。
- **[工具参考](./reference/tools.md):** 工具的定义、注册与使用说明。

## 资源

支持、发布历史与法律信息。

- **[常见问题](./resources/faq.md):** 高频问题解答。
- **[配额与定价](./resources/quota-and-pricing.md):** 限额与计费细节。
- **[条款与隐私](./resources/tos-privacy.md):** 官方声明与条款。
- **[故障排查](./resources/troubleshooting.md):** 常见问题与解决方案。
- **[卸载](./resources/uninstall.md):** 如何卸载 Gemini CLI。

## 开发

- **[贡献指南](/docs/contributing):** 如何为 Gemini CLI 做贡献。
- **[集成测试](./integration-tests.md):** 运行集成测试。
- **[Issue 与 PR 自动化](./issue-and-pr-automation.md):** issue 与 PR 的自动化。
- **[本地开发](./local-development.md):** 搭建本地开发环境。
- **[NPM 包结构](./npm.md):** NPM 包的结构说明。

## 发布版本

- **[发布说明](./changelogs/index.md):** 所有版本的发布说明。
- **[稳定版](./changelogs/latest.md):** 最新稳定版。
- **[预览版](./changelogs/preview.md):** 最新预览版。
