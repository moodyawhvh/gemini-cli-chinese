> 🌐 本文档由 [google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli) 翻译,英文原版见原项目。

# 包结构总览

本 monorepo 包含两个主要包:`@google/gemini-cli` 和 `@google/gemini-cli-core`。

## `@google/gemini-cli`

这是 Gemini CLI 的主包,负责用户界面、命令解析以及所有面向用户的功能。

该包发布时会被打包成单个可执行文件。这个 bundle 包含了该包的全部依赖,
包括 `@google/gemini-cli-core`。也就是说,无论用户是通过
`npm install -g @google/gemini-cli` 安装,还是用 `npx @google/gemini-cli`
直接运行,用的都是同一个自包含的可执行文件。

## `@google/gemini-cli-core`

该包包含与 Gemini API 交互的核心逻辑,负责发起 API 请求、处理认证以及管理本地
缓存。

该包不做打包,发布时作为标准的 Node.js 包附带自己的依赖。因此如有需要,
它可以作为独立包在其他项目中使用。`dist` 目录下所有转译后的 js 代码都会包含在
包内。

## NPM workspaces

本项目使用
[NPM Workspaces](https://docs.npmjs.com/cli/v10/using-npm/workspaces)
管理 monorepo 中的各个包。这样可以从项目根目录统一管理依赖、跨包运行脚本,
简化开发。

### 工作原理

根目录的 `package.json` 定义了本项目的 workspaces:

```json
{
  "workspaces": ["packages/*"]
}
```

这告诉 NPM:`packages` 目录下的任何文件夹都是一个独立的包,
应作为 workspace 的一部分管理。

### workspaces 的优势

- **简化依赖管理**:在项目根目录运行 `npm install`,会安装 workspace 中所有包的
  全部依赖并把它们链接在一起,无需在每个包的目录里分别执行 `npm install`。
- **自动链接**:workspace 内的包可以互相依赖。运行 `npm install` 时,NPM 会自动在
  各包之间创建符号链接(symlink),因此你对某个包的修改会立即对依赖它的其他包生效。
- **简化脚本执行**:可以在项目根目录用 `--workspace` 标志运行任意包中的脚本。
  例如要运行 `cli` 包的 `build` 脚本,执行
  `npm run build --workspace @google/gemini-cli` 即可。
