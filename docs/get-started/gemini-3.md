> 🌐 本文档由 [google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli) 翻译,英文原版见原项目。

# 在 Gemini CLI 上使用 Gemini 3 Pro 与 Gemini 3 Flash

了解如何在 Gemini CLI 上使用 Gemini 3 Pro 和 Gemini 3 Flash。

<!-- prettier-ignore -->
> [!NOTE]
> Gemini 3.1 Pro Preview 正在逐步推出。要判断你是否拥有 Gemini 3.1 的访问权限,
> 请使用 `/model` 命令并选择 **Manual**。如果有权限,你会看到
> `gemini-3.1-pro-preview`。
>
> 如果你拥有 Gemini 3.1 的访问权限,在选择 **Auto (Gemini 3)** 时它会被纳入模型
> 路由。你也可以用 `-m` 标志直接启动 Gemini 3.1 模型:
>
> ```
> gemini -m gemini-3.1-pro-preview
> ```
>
> 更多信息请参考[模型](../cli/model.md)与[模型路由](../cli/model-routing.md)。

## 如何在 Gemini CLI 上开始使用 Gemini 3

先把 Gemini CLI 升级到最新版本:

```bash
npm install -g @google/gemini-cli@latest
```

如果你的版本是 0.21.1 或更高:

1. 运行 `/model`。
2. 选择 **Auto (Gemini 3)**。

更多信息请参考 [Gemini CLI 模型选择](../cli/model.md)。

### 用量限制与回退

当你达到 Gemini 3 Pro 的每日用量上限时,Gemini CLI 会提示你。此时你可以选择
切换到 Gemini 2.5 Pro、升级以获得更高额度,或者停止使用。同时也会告诉你用量限制
何时重置、何时可以继续使用 Gemini 3 Pro。

<!-- prettier-ignore -->
> [!TIP]
> 想升级获得更高额度?请访问[套餐页面](https://geminicli.com/plans/)
> 对比各订阅方案,选择适合你的配额。

同样,当你达到 Gemini 2.5 Pro 的每日用量上限时,会看到提示你回退到
Gemini 2.5 Flash 的消息。

### 容量错误

Gemini 3 Pro 模型偶尔会过载。发生这种情况时,Gemini CLI 会让你选择是继续尝试
Gemini 3 Pro,还是回退到 Gemini 2.5 Pro。

<!-- prettier-ignore -->
> [!NOTE]
> **Keep trying**(继续尝试)选项在系统繁忙时采用指数退避策略,
> 即 Gemini CLI 每次重试之间的等待时间会逐渐变长。如果重试没有立即发生,
> 请等待几分钟让请求处理完成。

### 模型选择与路由类型

使用 Gemini CLI 时,你可能希望控制请求在不同模型之间的路由方式。默认情况下,
Gemini CLI 使用 **Auto**(自动)路由。

使用 Gemini 3 Pro 时,你可以选择 Auto 路由或 Pro 路由来管理用量额度:

- **Auto 路由:** Auto 路由会先判断提示词对应的是复杂操作还是简单操作。简单提示词
  会自动使用 Gemini 2.5 Flash;复杂提示词在 Gemini 3 Pro 可用时会使用
  Gemini 3 Pro,否则使用 Gemini 2.5 Pro。
- **Pro 路由:** 如果你想确保任务由能力最强的模型处理,使用 `/model` 并选择
  **Pro**。Gemini CLI 会优先使用能力最强的可用模型,包括已启用的 Gemini 3 Pro。

想进一步了解模型选择与路由,请参考 [Gemini CLI 模型选择](../cli/model.md)。

## 如何在 Gemini Code Assist 上为 Gemini CLI 启用 Gemini 3

如果你使用的是 Gemini Code Assist Standard 或 Gemini Code Assist Enterprise,
在 Gemini CLI 上启用 Gemini 3 Pro 需要配置发布渠道。使用 Gemini 3 Pro 需要两步:
管理员启用和用户启用。

关于这些设置的更多信息,请参考
[配置 Gemini Code Assist 发布渠道](https://developers.google.com/gemini-code-assist/docs/configure-release-channels)。

### 管理员操作

拥有 **Google Cloud Settings Admin** 权限的管理员需按以下步骤操作:

- 进入你在 Code Assist 中配合 Gemini CLI 使用的 Google Cloud 项目。
- 前往 **Admin for Gemini** > **Settings**。
- 在 **Release channels for Gemini Code Assist in local IDEs** 下选择
  **Preview**。
- 点击 **Save changes**。

### 用户操作

管理员启用 **Preview** 后等待两到三分钟,然后:

- 打开 Gemini CLI。
- 使用 `/settings` 命令。
- 将 **Preview Features** 设置为 `true`。

重启 Gemini CLI 后即可使用 Gemini 3。

## 下一步

如果需要帮助,我们建议先搜索已有的
[GitHub issue](https://github.com/google-gemini/gemini-cli/issues)。如果找不到
与你问题相符的 issue,可以[新建一个 issue](https://github.com/google-gemini/gemini-cli/issues/new/choose)。
如需评论与反馈,可以在
[GitHub discussion](https://github.com/google-gemini/gemini-cli/discussions) 中发起讨论。
