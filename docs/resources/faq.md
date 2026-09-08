> 🌐 本文档由 [google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli) 翻译,英文原版见原项目。

# 常见问题(FAQ)

本页汇总使用 Gemini CLI 时的常见问题解答与高频故障的处理办法。

## 一般问题

本节回答关于 Gemini CLI 使用、安全以及常见报错的问题。

### 为什么不能配合 Claude Code、OpenClaw、OpenCode 等第三方软件使用 Gemini CLI?

使用第三方软件、工具或服务,套用或搭便车复用 Gemini CLI 的 OAuth 认证来访问我们的
后端服务,直接违反我们的[相关条款与政策](tos-privacy.md)。这种行为绕过了我们
设计的认证与安全结构,可能成为立即暂停或终止你账号的依据。如果你想在 Gemini 上
使用第三方编码智能体,受支持且安全的方式是使用 Vertex AI 或 Google AI Studio 的
API key。

### 为什么会报 `API error: 429 - Resource exhausted`?

该错误表示你已超出 API 请求限额。Gemini API 设有速率限制,以防止滥用、保障公平
使用。

可以采取以下措施:

- **检查用量:** 在 Google AI Studio 或你的 Google Cloud 项目控制台中查看 API
  使用情况。
- **优化提示词:** 如果在短时间内发起了大量请求,尝试合并提示词或在请求之间加入
  延迟。
- **申请提升配额:** 如果你长期需要更高限额,可以向 Google 申请配额提升。

### 运行 `npm run start` 时为什么会报 `ERR_REQUIRE_ESM`?

该错误通常出现在 Node.js 项目中 CommonJS 与 ES Modules 不匹配的情况下。

多数情况是 `package.json` 或 `tsconfig.json` 配置有误。请确保:

1.  `package.json` 中有 `"type": "module"`。
2.  `tsconfig.json` 的 `compilerOptions` 中有 `"module": "NodeNext"`
    或兼容设置。

如果问题依旧,尝试删除 `node_modules` 目录和 `package-lock.json` 文件,
然后重新运行 `npm install`。

### 为什么统计输出里看不到缓存的 token 数量?

只有实际用到缓存 token 时才会显示缓存 token 信息。该功能对 API key 用户
(Gemini API key 或 Google Cloud Vertex AI)开放,但对 OAuth 用户
(例如 Google 个人/企业账号,分别对应 Google Gmail 或 Google Workspace)不开放,
因为 Gemini Code Assist API 不支持创建缓存内容。你仍然可以用 Gemini CLI 的
`/stats` 命令查看总 token 用量。

## 安装与更新

### 如何查看当前运行的 Gemini CLI 版本?

可用以下任一方式查看当前版本:

- 在终端运行 `gemini --version` 或 `gemini -v`
- 用包管理器查看全局安装的版本:
  - npm: `npm list -g @google/gemini-cli`
  - pnpm: `pnpm list -g @google/gemini-cli`
  - yarn: `yarn global list @google/gemini-cli`
  - bun: `bun pm ls -g @google/gemini-cli`
  - homebrew: `brew list --versions gemini-cli`
- 在 Gemini CLI 会话中使用 `/about` 命令

### 如何把 Gemini CLI 更新到最新版本?

如果通过 `npm` 全局安装,使用命令
`npm install -g @google/gemini-cli@latest` 更新。如果从源码编译,
先拉取仓库最新改动,再用 `npm run build` 重新构建。

## 平台相关问题

### 为什么在 Windows 上运行 `chmod +x` 之类的命令时 CLI 会崩溃?

`chmod` 等命令是类 Unix 操作系统(Linux、macOS)特有的,Windows 默认没有这些
命令。

解决办法:

- **使用 Windows 等价命令:** 在 Windows 上可以用 `icacls` 代替 `chmod`
  修改文件权限。
- **使用兼容层:** Git Bash 或 Windows Subsystem for Linux(WSL)等工具可以在
  Windows 上提供类 Unix 环境,这些命令在其中可以正常工作。

## 配置

### 如何配置 `GOOGLE_CLOUD_PROJECT`?

可以通过环境变量配置你的 Google Cloud 项目 ID。

在 shell 中设置 `GOOGLE_CLOUD_PROJECT` 环境变量:

**macOS/Linux**

```bash
export GOOGLE_CLOUD_PROJECT="your-project-id"
```

**Windows (PowerShell)**

```powershell
$env:GOOGLE_CLOUD_PROJECT="your-project-id"
```

要让设置永久生效,把这行加入 shell 的启动文件
(例如 `~/.bashrc`、`~/.zshrc`)。

### 如何安全地保存 API key?

把 API key 暴露在脚本里或提交进版本控制都有安全风险。

安全保存 API key 的方式:

- **使用 `.env` 文件:** 在项目的 `.gemini` 目录中创建 `.env` 文件
  (`.gemini/.env`)并把 key 存在里面,Gemini CLI 会自动加载这些变量。
- **使用系统密钥环:** 最安全的方式是使用操作系统自带的机密管理工具
  (如 macOS Keychain、Windows 凭据管理器或 Linux 上的 secret manager),
  再由脚本或环境在运行时从安全存储中读取 key。

### Gemini CLI 的配置与设置文件存放在哪里?

Gemini CLI 的配置保存在两个 `settings.json` 文件中:

1.  主目录:`~/.gemini/settings.json`。
2.  项目根目录:`./.gemini/settings.json`。

更多细节参见 [Gemini CLI 配置](../reference/configuration.md)。

## Google AI Pro/Ultra 与订阅相关 FAQ

### 在哪里可以了解更多 Google AI Pro 或 Google AI Ultra 订阅的信息?

要了解订阅详情,请访问[订阅设置](https://one.google.com)中的
**Manage subscription**。

### 怎么知道我是否拥有 Google AI Pro 或 Ultra 的更高限额?

订阅 Google AI Pro 或 Ultra 后,你会自动获得 Gemini Code Assist 和 Gemini CLI 的
更高限额。这些额度在 Gemini CLI 与 IDE 的 agent mode 之间共享。可以在
[订阅设置](https://one.google.com)中确认你是否仍在订阅 Google AI Pro 或 Ultra,
以此核实更高限额是否生效。

### 如果我订阅了 Google AI Pro 或 Ultra,使用 Gemini Code Assist 或 Gemini CLI 的隐私政策是什么?

要了解订阅所适用的隐私政策与服务条款,请访问
[Gemini Code Assist:服务条款与隐私政策](https://developers.google.com/gemini-code-assist/resources/privacy-notices)。

### 我已升级到 Google AI Pro 或 Ultra,但仍然提示达到配额上限,这是 bug 吗?

Google AI Pro 或 Ultra 订阅的更高额度针对 Gemini 2.5 家族
(涵盖 Gemini 2.5 Pro 和 Flash),并在 Gemini CLI 与 Gemini Code Assist IDE
扩展的 agent mode 之间共享。关于 Gemini CLI、Gemini Code Assist 及其 agent mode
的配额详情,见
[配额与限制](https://developers.google.com/gemini-code-assist/resources/quotas)。

### 如果我购买 Google AI Pro 或 Ultra 订阅来提升 Gemini CLI 和 Gemini Code Assist 的限额,Gemini 会不会用我的数据改进机器学习模型?

购买付费方案后,Google 不会使用你的数据改进其机器学习模型。注意:如果你继续使用
免费版 Gemini Code Assist(Gemini Code Assist for individuals),也可以选择退出
数据改进计划。详见
[Gemini Code Assist for individuals 隐私声明](https://developers.google.com/gemini-code-assist/resources/privacy-notice-gemini-code-assist-individuals)。

## 没有找到你的问题?

搜索
[Gemini CLI Q&A discussions on GitHub](https://github.com/google-gemini/gemini-cli/discussions/categories/q-a),
或
[在 GitHub 上发起新讨论](https://github.com/google-gemini/gemini-cli/discussions/new?category=q-a)
