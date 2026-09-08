> 🌐 本文档由 [google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli) 翻译,英文原版见原项目。

# Gemini CLI 入门

欢迎来到 Gemini CLI!本指南将帮助你在终端中安装、配置并开始使用 Gemini CLI,
直接提升你的工作效率。

## 快速上手:安装、认证、配置并使用 Gemini CLI

Gemini CLI 把先进语言模型的能力直接带到你的命令行界面。作为 AI 驱动的助手,
Gemini CLI 可以帮你完成各种任务,从理解和生成代码,到审阅和编辑文档。

## 安装

安装并运行 Gemini CLI 的标准方式是使用 `npm`:

```bash
npm install -g @google/gemini-cli
```

安装完成后,在命令行中运行 Gemini CLI:

```bash
gemini
```

更多安装选项请参考 [Gemini CLI 安装](./installation.mdx)。

## 认证

要开始使用 Gemini CLI,必须先通过某个 Google 服务完成认证。大多数情况下,
直接用你现有的 Google 账号登录即可:

1. 安装后运行 Gemini CLI:

   ```bash
   gemini
   ```

2. 当被问到 "How would you like to authenticate for this project?" 时,
   选择 **1. Sign in with Google**。

3. 选择你的 Google 账号。

4. 点击 **Sign in**。

某些账号类型可能需要你配置一个 Google Cloud 项目。包括其他认证方式在内的更多信息,
请参考 [Gemini CLI 认证设置](./authentication.mdx)。

## 配置

Gemini CLI 提供多种配置方式,包括环境变量、命令行参数和设置文件。

想了解全部配置选项,请参考 [Gemini CLI 配置](../reference/configuration.md)。

## 使用

安装并认证完成后,你就可以在终端中输入命令和提示词来使用 Gemini CLI 了。
可以让它生成代码、解释文件,等等。

<!-- prettier-ignore -->
> [!NOTE]
> 以下示例展示的是潜在能力。实际结果会因所用模型和你的项目环境而有所不同。

### 根据照片内容重命名照片

你可以用 Gemini CLI 自动完成需要视觉分析的文件管理任务。本例中,Gemini CLI
会根据图片的实际内容重命名图像。

场景:你有一个包含如下文件的文件夹:

```bash
photos/photo1.png
photos/photo2.png
photos/photo3.png
```

给 Gemini 以下提示词:

```cli
Rename the photos in my "photos" directory based on their contents.
```

结果:Gemini 会请求重命名文件的权限。

选择 **Allow once** 后,你的文件会被重命名为:

```bash
photos/yellow_flowers.png
photos/antique_dresser.png
photos/green_android_robot.png
```

### 通过阅读代码解释一个仓库

Gemini CLI 非常适合快速探索代码库。下面的例子展示如何让 Gemini CLI 抓取、
分析并总结一个远程项目。

场景:你想通过阅读代码(而不只是 README)搞清楚一个流行的开源工具是如何工作的。

给 Gemini CLI 以下提示词:

```cli
Clone the 'chalk' repository from https://github.com/chalk/chalk, read its key source files, and explain how it works.
```

结果:Gemini 会执行一系列操作来回答你的请求。

1.  首先,它请求运行 `git clone` 下载仓库的权限。
2.  接着,它找到关键的源码文件并请求读取权限。
3.  最后,在分析完代码后给出总结。

Gemini CLI 会基于真实源码返回解释:

```markdown
The `chalk` library is a popular npm package for styling terminal output with
colors. After analyzing the source code, here's how it works:

- **Core functionality:** The main file sets up a chainable API. Each color or
  modifier (like `bold` or `italic`) is a getter that appends the corresponding
  ANSI escape code to an internal stack.

- **Chainable API:** When you call `chalk.red.bold('Hello')`, you are accessing
  getters. The `red` getter adds the red color code, and the `bold` getter adds
  the bold code.

- **Output generation:** When the chain is treated as a string (for example, in
  `console.log`), a final `toString()` method is called. This method joins all
  the stored ANSI codes, wraps them around the input string ('Hello'), and adds
  a reset code at the end. This produces the final, styled string that the
  terminal can render.
```

### 把两个电子表格合并成一个

Gemini CLI 可以跨多个文件处理和转换数据。利用这个能力,无需手动复制即可合并报表
或重排数据集。

场景:你有两个 .csv 文件:`Revenue - 2023.csv` 和 `Revenue - 2024.csv`,
每个文件包含按月统计的收入数据。

给 Gemini CLI 以下提示词:

```cli
Combine the two .csv files into a single .csv file, with each year a different column.
```

结果:Gemini CLI 会先读取每个文件,然后请求写入新文件的权限。授权后,
Gemini CLI 会给出合并后的数据:

```csv
Month,2023,2024
January,0,1000
February,0,1200
March,0,2400
April,900,500
May,1000,800
June,1000,900
July,1200,1000
August,1800,400
September,2000,2000
October,2400,3400
November,3400,1800
December,2100,9000
```

### 运行单元测试

Gemini CLI 可以基于你现有的实现生成样板代码和测试。这个例子演示如何为一个
JavaScript 组件申请代码覆盖测试。

场景:你写了一个简单的登录页面,希望编写单元测试来保证它有代码覆盖。

给 Gemini CLI 以下提示词:

```cli
Write unit tests for Login.js.
```

结果:Gemini CLI 会请求写入新文件的权限,并为你的登录页面创建测试。

## 查看用量与配额

你可以使用 `/stats model` 命令查看当前的 token 用量和配额信息。该命令会给出
当前会话 token 用量的快照,以及所支持模型的整体配额和使用情况。

关于 `/stats` 命令及其子命令的更多信息,请参考
[命令参考](../reference/commands.md#stats)。

## 下一步

- 跟随[文件管理](../cli/tutorials/file-management.md)指南开始处理你的代码库。
- 阅读 [Shell 命令](../cli/tutorials/shell-commands.md)了解终端集成。
