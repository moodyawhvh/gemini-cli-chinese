<div align="center">

# Gemini CLI 中文文档

**[中文翻译版] 把 Gemini 直接装进终端的开源 AI 智能体**

[![原项目](https://img.shields.io/badge/原项目-google--gemini--gemini--cli-blue?style=flat-square&logo=github)](https://github.com/google-gemini/gemini-cli)
[![微信联系](https://img.shields.io/badge/微信-uaycar-brightgreen?style=flat-square&logo=wechat)](#)

</div>

---

## 项目简介

Gemini CLI 是一个开源 AI 智能体,把 Gemini 的能力直接带进你的终端。它提供了对 Gemini 的轻量访问,是从你的提示词到模型之间最直接的路径。

完整文档请访问官方文档站:https://geminicli.com/docs/

## 为什么选 Gemini CLI?

- **🎯 免费额度**:个人 Google 账号每分钟 60 次请求、每天 1000 次请求
- **🧠 强大的 Gemini 3 模型**:更强的推理能力与 100 万 token 上下文窗口
- **🔧 内置工具**:Google 搜索接地、文件操作、Shell 命令、网页抓取
- **🔌 可扩展**:支持 MCP(Model Context Protocol)自定义集成
- **💻 终端优先**:为住在命令行里的开发者设计
- **🛡️ 开源**:Apache 2.0 许可证

## 安装

推荐系统配置与详细安装指南见官方文档 [installation 页面](https://geminicli.com/docs/get-started/installation)。

### 快速安装

#### 用 npx 直接运行(无需安装)

```bash
npx @google/gemini-cli
```

#### npm 全局安装

```bash
npm install -g @google/gemini-cli
```

#### Homebrew(macOS/Linux)

```bash
brew install gemini-cli
```

#### MacPorts(macOS)

```bash
sudo port install gemini-cli
```

#### Anaconda(受限网络环境)

```bash
# 创建并激活新环境
conda create -y -n gemini
conda activate gemini
# 安装
conda install -c conda-forge gemini-cli
```

## 使用示例

安装后直接在终端运行 `gemini`,首次会引导你用个人 Google 账号登录并授权免费额度。

常用操作:

- 直接输入自然语言让它解释代码、生成补丁、执行重构
- 用内置的 Google 搜索接地让它查最新资料
- 通过 MCP 接入你自己的工具与数据源

## 故障排查

遇到问题可查阅官方文档的 troubleshooting 章节或在 GitHub 仓库提 issue。

## 参与贡献

欢迎贡献代码、报告问题与翻译文档,详见[贡献指南](https://github.com/google-gemini/gemini-cli/blob/main/CONTRIBUTING.md)。

## 许可证

Apache 2.0 许可证,详见 [LICENSE](https://github.com/google-gemini/gemini-cli/blob/main/LICENSE)。

---

## 联系方式

**代部署 / 定制服务 / 技术咨询 请添加微信:uaycar**

---

本项目为 [google-gemini/gemini-cli](https://github.com/google-gemini/gemini-cli) 的中文翻译版本,所有代码版权归原项目作者所有,遵循其原始许可证(Apache 2.0)。

**如果觉得有用,请给原项目点个 Star!** ⭐
