<div align="center">

<img src="docs/logo.svg" alt="readme-builder" width="120">

<!-- 占位 Logo，替换为项目真实 Logo：docs/logo.png -->

# readme-builder

**一个自动生成「结构完整、视觉美观、信息精炼」的 GitHub 项目 README 的 AI Agent 技能**

![License: MIT](https://img.shields.io/badge/license-MIT-green)
![Type: Agent Skill](https://img.shields.io/badge/type-Agent%20Skill-blue)
![Spec: Standard Readme](https://img.shields.io/badge/spec-Standard%20Readme-brightgreen)
![Language: Markdown](https://img.shields.io/badge/language-Markdown-000000)

[反馈](https://github.com/lsx-xyg/readme-builder/issues)

</div>

## 📚 目录

- [💡 这是什么](#-这是什么)
- [✨ 功能](#-功能)
- [🚀 安装](#-安装)
- [📖 使用](#-使用)
- [⚙️ 配置](#-配置)
- [🛠️ 开发](#-开发)
- [📁 项目结构](#-项目结构)
- [🤝 贡献](#-贡献)
- [📄 License](#-license)

---

## 💡 这是什么

readme-builder 是一个 AI Agent 技能：当用户要求生成、重写或美化 README 时，它按一套固定规范自动产出可直接发布到 GitHub 的 `README.md`。

- **解决什么问题**：README 常要么结构不全、要么堆砌无意义的徽章和空话，维护者难写、读者难读。
- **适合谁**：开源项目维护者、独立开发者、需要项目首页说明文档的个人或团队。
- **和同类工具的区别**：不只是套模板——同时约束「结构（Standard Readme）+ 视觉（居中头部、徽章、Callout、折叠块）+ 精简（10 秒决策）」，并内置 Logo 处理与输出前自查清单。

## ✨ 功能

| 功能 | 说明 |
| :--- | :--- |
| 📐 结构完整 | 遵循 Standard Readme 规范输出固定章节顺序，信息不足的章节直接省略、不编造 |
| 🎨 视觉美观 | 居中头部、品牌色徽章、Callout 提示块、折叠块、特性表格、截图/GIF 占位 |
| ✂️ 信息精炼 | 徽章 ≤5 个，短句与表格代替长段落，让读者 10 秒内做「要不要用、怎么装」的决策 |
| 🖼️ Logo 三级处理 | `docs/logo.png` → 项目现有 Logo → 自动生成占位 SVG，头部引用统一 |
| 🧭 固定导航规范 | 仅用「下载/文档/在线体验/更新日志/反馈/贡献」六词导航，无同义词替换、无假链接 |
| ✅ 输出前自查 | 逐条对照检查清单（徽章数、Logo 路径、导航词、markdownlint）通过后再交付 |

## 🚀 安装

### 下载即用

将本仓库的 `skills/readme-builder` 目录复制到宿主 Agent 的技能根目录，例如豆包的 `.user_skills/` 或 Claude Code 的 `.claude/skills/`。

### 从源码安装

```bash
git clone https://github.com/lsx-xyg/readme-builder.git
```

克隆后把 `skills/readme-builder` 放到 Agent 的技能根目录。

> [!NOTE]
> 具体安装路径与生效方式取决于宿主 Agent 平台，请以其技能安装文档为准。

## 📖 使用

1. 对 Agent 说出触发词：**生成 README / 写 README / README.md / 项目说明文档 / 项目主页**。
2. 简单描述项目，例如：

```text
生成 README.md：项目名 foo-cli，Python 3.10+，MIT，PyPI 发布，跨平台。
功能：批量重命名、路径映射、日志输出。
安装：pip install foo-cli；使用：foo-cli rename <dir>。
```

3. Agent 先按「项目信息表单」补齐缺失信息（一次最多追问 3 个问题），再按规范输出完整 README。

<!-- 替换为实际使用截图：docs/screenshot-main.png -->

## ⚙️ 配置

技能读取以下「项目信息表单」字段；未提供的字段留空，**不编造命令、文件、版本号或指标**：

| 字段 | 说明 |
| :--- | :--- |
| 项目名 / 一句话定位 | 必填；缺失且无法从上下文推断时向用户追问 |
| 仓库地址 / License | 用于导航链接与 License 章节 |
| 技术栈 / 关键依赖 / 支持平台 / 发布方式 | 用于徽章与安装章节 |
| 项目主色（可选） | 用于徽章与 Logo 配色 |
| 导航链接 | 仅从固定 6 词中选择，按固定顺序输出 |
| 项目功能 / 安装与使用 / 项目结构 / 扩展方式 | 逐章落内容，信息不足即省略 |

<details>
<summary>更多规范细节</summary>

- 徽章 ≤5 个，删除 Views / Stars / Forks 等噪音徽章。
- 每段 ≤3 行，删除「功能强大」「业界领先」等空话。
- 警告与提示使用 GitHub Callout 语法（`> [!NOTE]` / `> [!TIP]` / `> [!WARNING]`）。
- 输出符合 markdownlint：标题层级不跳级、代码块标注语言、列表统一 `-`、表格对齐、行尾无多余空格。

</details>

## 🛠️ 开发

本项目为纯 Markdown 规范型技能：

- **前置要求**：无代码依赖，无需构建环境。
- **运行**：作为 Agent 技能触发，无独立运行入口。
- **打包 / CI**：无构建产物，未配置 CI。

## 📁 项目结构

```text
readme-builder/
├── README.md                        # 项目说明（本文件）
├── LICENSE                          # MIT License
├── docs/
│   └── logo.svg                     # 占位 Logo（可替换为 docs/logo.png）
└── skills/
    └── readme-builder/
        └── SKILL.md                 # 技能定义：信息表单、章节规范、Logo 规则、检查清单
```

## 🤝 贡献

欢迎通过 [Issues](https://github.com/lsx-xyg/readme-builder/issues) 反馈问题或提出改进建议，也可以直接提交 Pull Request。

## 📄 License

本项目采用 [MIT License](LICENSE)。
