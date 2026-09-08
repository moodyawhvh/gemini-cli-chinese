> 🌐 本文档由 [google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli) 翻译,英文原版见原项目。

# 卸载 CLI

卸载方式取决于你当初如何运行 CLI。请按照 npx 或全局 npm 安装对应的说明操作。

## 方式 1:使用 npx

npx 从临时缓存运行包,不做永久安装。要"卸载" CLI,必须清空这个缓存,
这会同时移除 gemini-cli 以及之前用 npx 执行过的其他包。

npx 缓存是 npm 主缓存目录下名为 `_npx` 的文件夹。运行 `npm config get cache`
可以找到你的 npm 缓存路径。

**macOS / Linux**

```bash
# The path is typically ~/.npm/_npx
rm -rf "$(npm config get cache)/_npx"
```

**Windows (PowerShell)**

```powershell
# The path is typically $env:LocalAppData\npm-cache\_npx
Remove-Item -Path (Join-Path $env:LocalAppData "npm-cache\_npx") -Recurse -Force
```

## 方式 2:使用 npm(全局安装)

如果通过全局方式安装了 CLI(例如 `npm install -g @google/gemini-cli`),
使用带 `-g` 标志的 `npm uninstall` 命令移除。

```bash
npm uninstall -g @google/gemini-cli
```

该命令会把包从系统中完全移除。

## 方式 3:Homebrew

如果通过 Homebrew 全局安装(例如 `brew install gemini-cli`),
使用 `brew uninstall` 命令移除。

```bash
brew uninstall gemini-cli
```

## 方式 4:MacPorts

如果通过 MacPorts 全局安装(例如 `sudo port install gemini-cli`),
使用 `port uninstall` 命令移除。

```bash
sudo port uninstall gemini-cli
```
