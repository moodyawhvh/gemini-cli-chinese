> 🌐 本文档由 [google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli) 翻译,英文原版见原项目。
>
> 📌 原文超过 10000 字符,本译文聚焦核心章节;"沙箱细节 / 手动发布"等次要章节仅保留中文摘要,细节见英文原版。

# 如何参与贡献

我们非常欢迎你为本项目提交补丁与贡献。本文档包括:

- **[开始之前](#开始之前):** 成为 Gemini CLI 贡献者前的必要步骤。
- **[代码贡献流程](#代码贡献流程):** 如何向 Gemini CLI 贡献代码。
- **[开发环境与工作流](#开发环境与工作流):** 如何搭建开发环境与日常工作流。
- **[文档贡献流程](#文档贡献流程):** 如何向 Gemini CLI 贡献文档。

期待看到你的贡献!

## 开始之前

### 签署贡献者许可协议(CLA)

对本项目的贡献必须附带
[贡献者许可协议](https://cla.developers.google.com/about)(CLA)。
你(或你的雇主)保留贡献的版权;CLA 只是授予我们使用和再分发你贡献的许可。

如果你或你现在的雇主已经签署过 Google CLA(即使是为其他项目签的),
通常无需重复签署。

访问 <https://cla.developers.google.com/> 查看现有协议或签署新协议。

### 阅读社区准则

本项目遵循
[Google 开源社区准则](https://opensource.google/conduct/)。

## 代码贡献流程

### 快速上手

代码贡献流程如下:

1.  **找到你想处理的 issue。** 如果 issue 被标记为 `🔒Maintainers only`,
    表示它保留给项目维护者,我们不会接受与之相关的 pull request。近期我们会用
    `help-wanted` 标签明确标记欢迎社区贡献的 issue。如果你认为某个 issue 适合
    社区贡献,可以在 issue 下留言,维护者会审阅并在合适时打上 `help-wanted`。
    只有维护者才应尝试为 issue 添加该标签。
2.  **Fork 仓库**并创建新分支。
3.  在 `packages/` 目录中**完成你的修改**。
4.  运行 `npm run preflight`,**确保所有检查通过**。
5.  **发起 pull request**。

### 代码评审

所有提交(包括项目成员的提交)都需要评审。我们使用
[GitHub pull requests](https://docs.github.com/articles/about-pull-requests)
完成评审。

为辅助评审,我们提供了一个自动化评审工具,用于发现常见的反模式、测试问题
以及其他容易忽略的最佳实践问题。

#### 使用自动化评审工具

有两种运行方式:

1.  **使用辅助脚本(推荐):** 我们提供一条脚本,自动完成把 PR 检出到独立
    worktree、安装依赖、构建项目并启动评审工具。

    ```bash
    ./scripts/review.sh <PR_NUMBER> [model]
    ```

    **警告:** 运行 `scripts/review.sh` 前,你必须先确认被评审 PR 的代码可以安全
    执行,且不包含数据外泄攻击。

    **强烈建议作者在创建 PR 后立即在自己的 PR 上运行该脚本**,
    以便在维护者完整评审之前,先在本地发现并修复简单问题。

    **关于模型:** 默认使用最新 Pro 模型(`gemini-3.1-pro-preview`)。
    如果 Pro 配额不足,可改用最新 Flash 模型运行:
    `./scripts/review.sh <PR_NUMBER> gemini-3-flash-preview`。

2.  **在 Gemini CLI 内手动运行:** 如果你已检出并构建好该 PR,
    可直接在 CLI 提示符中运行:

    ```text
    /review-frontend <PR_NUMBER>
    ```

将 `<PR_NUMBER>` 替换为你的 PR 编号。评审者应把该工具作为人工评审的补充,
而非替代。

### 认领与取消认领 issue

要认领 issue,只需发表内容为 `/assign` 的评论;要取消认领,
发表内容为 `/unassign` 的评论。

评论中只能包含该文本,不能有其他内容。在满足条件的前提下(例如 issue 必须处于
未被认领状态才能认领),这些命令会按要求分配或取消分配 issue。

注意:每个人同时最多认领 3 个 issue,且只有
[带 "help wanted" 标签的 issue](https://github.com/google-gemini/gemini-cli/issues?q=is%3Aissue%20state%3Aopen%20label%3A%22help%20wanted%22)
才能自行认领。

### Pull request 规范

为帮助我们快速评审并合并你的 PR,请遵守以下规范。不符合标准的 PR 可能被直接关闭。

#### 1. 关联已有 issue

所有 PR 都必须关联追踪系统中的已有 issue,确保每一处改动都经过讨论、
与项目目标一致,再动手写代码。

- **bug 修复:** PR 应关联对应的 bug 报告 issue。
- **新功能:** PR 应关联经维护者认可的功能请求或提案 issue。

如果对应的 issue 不存在,我们会自动关闭你的 PR,并提醒你先关联 issue。
理想的工作流是:**先开 issue**,获得维护者反馈后,再开始编码。

#### 2. 保持小而聚焦

我们偏好解决单一 issue 或添加单一自包含功能的小型原子 PR。

- **应该:** 一个 PR 只修一个具体的 bug,或只加一个具体的功能。
- **不要:** 把多个不相关的改动(例如 bug 修复、新功能、重构)塞进同一个 PR。

大改动应拆分为一系列更小的、可独立评审与合并的逻辑 PR。

#### 3. 进行中的工作使用草稿 PR

想尽早获得反馈时,请使用 GitHub 的 **Draft Pull Request** 功能。
这向维护者表明该 PR 尚未准备好正式评审,但欢迎讨论与初步反馈。

#### 4. 确保所有检查通过

提交 PR 前,运行 `npm run preflight` 确保所有自动化检查通过。
该命令会运行全部测试、lint 和其他风格检查。

#### 5. 更新文档

如果你的 PR 引入了用户可见的变更(例如新命令、修改的标志或行为变化),
必须同时更新 `/docs` 目录下的相关文档。

更多写文档的信息见[文档贡献流程](#文档贡献流程)。

#### 6. 写清晰的提交信息与 PR 描述

PR 标题要清晰、有描述性,并附上详细的改动说明。提交信息请遵循
[Conventional Commits](https://www.conventionalcommits.org/) 标准。

- **好的 PR 标题:** `feat(cli): Add --json flag to 'config get' command`
- **差的 PR 标题:** `Made some changes`

在 PR 描述中解释改动背后的"为什么",并关联相关 issue(例如 `Fixes #123`)。

### Fork 仓库

Fork 仓库后,你可以运行 Build、Test 和 Integration test 工作流。但要让集成测试
跑起来,需要添加一个值为 `GEMINI_API_KEY` 的
[GitHub Repository Secret](https://docs.github.com/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions#creating-secrets-for-a-repository),
并设置为你可用的有效 API key。你的密钥只对你自己的仓库可见;无权限者看不到,
你也看不到本仓库的其他 secret。

另外,你需要点击 `Actions` 标签页并为仓库启用工作流(屏幕中央的蓝色大按钮)。

## 开发环境与工作流

本节指导贡献者构建、修改并理解本项目的开发环境。

### 搭建开发环境

**前置要求:**

1.  **Node.js**:
    - **开发:** 请使用 Node.js `~20.19.0`。因上游开发依赖的问题,必须使用该特定
      版本。可用 [nvm](https://github.com/nvm-sh/nvm) 等工具管理 Node.js 版本。
    - **生产:** 在生产环境运行 CLI 时,任何 `>=20` 的 Node.js 版本均可。
2.  **Git**

### 构建流程

克隆仓库:

```bash
git clone https://github.com/google-gemini/gemini-cli.git # Or your fork's URL
cd gemini-cli
```

安装 `package.json` 中定义的依赖以及根依赖:

```bash
npm install
```

构建整个项目(所有包):

```bash
npm run build
```

该命令通常会把 TypeScript 编译为 JavaScript、打包资源并为各包的执行做准备。
构建过程的更多细节参见 `scripts/build.js` 与 `package.json` 中的脚本。

### 启用沙箱

强烈建议启用[沙箱](#沙箱摘要),至少需要在 `~/.env` 中设置
`GEMINI_SANDBOX=true`,并确保有可用的沙箱提供程序(如 `macOS Seatbelt`、
`docker` 或 `podman`)。细节见英文原版 Sandboxing 一节。

要同时构建 `gemini` CLI 工具和沙箱容器,在根目录运行 `build:all`:

```bash
npm run build:all
```

若要跳过沙箱容器构建,改用 `npm run build` 即可。

### 运行 CLI

构建完成后,在根目录运行以下命令从源码启动 Gemini CLI:

```bash
npm start
```

如果想在 gemini-cli 目录之外运行源码构建,可以使用
`npm link path/to/gemini-cli/packages/cli`
(参见:[文档](https://docs.npmjs.com/cli/v9/commands/npm-link)),或
`alias gemini="node path/to/gemini-cli/packages/cli"`,之后即可用 `gemini` 运行。

### 运行测试

本项目包含两类测试:单元测试和集成测试。

#### 单元测试

运行项目的单元测试套件:

```bash
npm run test
```

它会运行 `packages/core` 和 `packages/cli` 目录下的测试。提交任何改动前请确保
测试通过。更全面的检查推荐运行 `npm run preflight`。

#### 集成测试

集成测试用于验证 Gemini CLI 的端到端功能,不包含在默认的 `npm run test` 中。

运行集成测试:

```bash
npm run test:e2e
```

集成测试框架的更多细节,参见
[集成测试文档](https://geminicli.com/docs/integration-tests)。

### Lint 与 preflight 检查

为保证代码质量与格式一致,运行 preflight 检查:

```bash
npm run preflight
```

该命令会按项目 `package.json` 中的定义运行 ESLint、Prettier、全部测试及其他检查。

_ProTip_

克隆仓库后,可以创建一个 git pre-commit 钩子,确保每次提交都是干净的:

```bash
echo "
# Run npm build and check for errors
if ! npm run preflight; then
  echo "npm build failed. Commit aborted."
  exit 1
fi
" > .git/hooks/pre-commit && chmod +x .git/hooks/pre-commit
```

#### 格式化

单独格式化本项目代码,在根目录运行:

```bash
npm run format
```

该命令使用 Prettier 按项目风格规范格式化代码。

#### Lint

单独对项目代码运行 lint,在根目录运行:

```bash
npm run lint
```

### 编码约定

- 请遵循现有代码库中的编码风格、模式与约定。
- 关于 AI 辅助开发的专用约定(React、注释、Git 使用等),
  请查阅 [GEMINI.md](https://github.com/google-gemini/gemini-cli/blob/main/GEMINI.md)
  (通常位于项目根目录)。
- **导入路径:** 特别注意 import 路径。项目用 ESLint 限制包之间的相对导入。

### 调试

#### VS Code

0.  在 VS Code 中按 `F5` 以交互方式调试运行 CLI。
1.  在根目录以调试模式启动 CLI:
    ```bash
    npm run debug
    ```
    该命令在 `packages/cli` 目录内运行 `node --inspect-brk dist/gemini.js`,
    并暂停执行直到调试器连接。随后可在 Chrome 中打开 `chrome://inspect`
    连接调试器。
2.  在 VS Code 中使用 "Attach" 启动配置(见 `.vscode/launch.json`)。

也可以使用 "Launch Program" 配置直接启动当前打开的文件,但一般推荐 `F5`。

要在沙箱容器内命中断点,运行:

```bash
DEBUG=1 gemini
```

**注意:** 项目 `.env` 文件中的 `DEBUG=true` 会被自动排除,不影响 gemini-cli。
gemini-cli 专用的调试设置请放在 `.gemini/.env` 文件中。

### 次要章节摘要(沙箱细节 / React DevTools / 手动发布)

- **React DevTools:** 用 `DEV=true npm start` 以开发模式启动 CLI,再运行
  `npx react-devtools@6`,运行中的 CLI 会自动连接 DevTools。
- **沙箱摘要:** macOS 使用 Seatbelt(`sandbox-exec`),默认
  `permissive-open` 配置(默认拒绝写操作,仅限项目目录写入,放宽读取与出站网络);
  可通过 `SEATBELT_PROFILE=strict-open` 切换严格配置。所有平台均可设置
  `GEMINI_SANDBOX=true|docker|podman|<command>` 使用容器沙箱,项目目录与系统临时
  目录以读写方式挂载,随 CLI 启停自动管理;可用 `SANDBOX_{MOUNTS,PORTS,ENV}`
  附加挂载、端口与环境变量,也可用 `.gemini/sandbox.Dockerfile` 与
  `.gemini/sandbox.bashrc` 自定义沙箱(配合 `BUILD_SANDBOX=1` 构建)。
- **代理网络:** 各类沙箱(含 `*-proxied` 配置)支持通过
  `GEMINI_SANDBOX_PROXY_COMMAND=<command>` 指定自定义代理,代理须监听
  `:::8877`;最小示例见 `docs/examples/proxy-script.md`(仅放行到
  `example.com:443` 的 HTTPS)。
- **手动发布:** 每个提交都会自动发布到内部 registry。如需手动出本地构建:
  依次运行 `npm run clean`、`npm install`、`npm run auth`、
  `npm run prerelease:dev`、`npm publish --workspaces`。

## 文档贡献流程

文档必须与代码贡献保持同步更新。我们希望文档清晰、简洁、对用户有帮助。我们重视:

- **清晰:** 用简单直接的语言,尽量避免行话。
- **准确:** 确保所有信息正确且最新。
- **完整:** 覆盖功能或主题的各个方面。
- **示例:** 提供实用示例,帮助用户理解如何使用 Gemini CLI。

### 快速上手

文档贡献流程与代码贡献类似:

1. **Fork 仓库**并创建新分支。
2. 在 `/docs` 目录中**完成修改**。
3. 在本地**预览** Markdown 渲染效果。
4. **对改动运行 lint 与格式化。** preflight 检查包含文档文件的 lint 与格式检查。
   ```bash
   npm run preflight
   ```
5. **发起 pull request**。

### 文档结构

我们的文档使用
[sidebar.json](https://github.com/google-gemini/gemini-cli/blob/main/docs/sidebar.json)
作为目录组织。新增文档时:

1. 在 `/docs` 下**合适的目录**中创建 markdown 文件。
2. 在 `sidebar.json` 的对应小节中添加条目。
3. 确保所有内部链接使用相对路径并指向存在的文件。

### 风格指南

我们遵循
[Google 开发者文档风格指南](https://developers.google.com/style)。
写作风格、语气与格式请参考该指南。

#### 关键风格要点

- 标题使用 sentence case。
- 以第二人称("you")称呼读者。
- 使用现在时。
- 段落保持简短聚焦。
- 代码块加上合适的语言标签以获得语法高亮。
- 尽量提供实际示例。

### Lint 与格式化

我们用 `prettier` 保证文档风格一致。`npm run preflight` 会检查 lint 问题。

也可以单独运行:

- `npm run lint` - 检查 lint 问题
- `npm run format` - 自动格式化 markdown 文件
- `npm run lint:fix` - 尽可能自动修复 lint 问题

提交 pull request 前,请确保贡献内容没有 lint 错误。

### 提交前检查

提交文档 PR 前,请:

1. 运行 `npm run preflight` 确保所有检查通过。
2. 通读改动,确认清晰且准确。
3. 检查所有链接是否有效。
4. 确保代码示例经过测试、可正常运行。
5. 如尚未签署,请签署
   [贡献者许可协议(CLA)](https://cla.developers.google.com/)。

### 需要帮助?

关于文档贡献的疑问:

- 查看[常见问题](https://geminicli.com/docs/resources/faq)。
- 参考现有文档中的写法。
- 发起 [issue](https://github.com/google-gemini/gemini-cli/issues) 讨论你的改动。
- 联系维护者。

感谢你为改进 Gemini CLI 文档做出的贡献!
