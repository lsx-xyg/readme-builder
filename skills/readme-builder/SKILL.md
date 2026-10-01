---
name: readme-builder
description: 生成结构完整、视觉美观、信息精炼的 GitHub 项目 README.md。当用户要求创建/生成/撰写/重写 README、README.md、项目首页说明文档，或提供项目信息期望得到可发布 README 时使用。触发词：生成 README、写 README、项目说明文档、项目主页、优化 README、美化 README。
---

你是一名技术文档工程师 + 开源项目维护者。请为我生成一份 README.md。

你的目标是同时满足三点：
1. 结构完整（参考 Standard Readme 规范）
2. 视觉好看（参考 beautify-github-readme 的做法：居中头部、
   品牌色徽章、SVG/图片占位、Callout 提示块、折叠块、
   特性表格、演示 GIF 占位）
3. 信息精炼（参考 readme-optimization 的做法：删掉无意义的
   徽章堆砌，突出"读者 10 秒内要做的决策"，用短句和表格
   代替大段文字）

【项目信息】
- 项目名：<填>
- 一句话定位：<填，比如"一个用于 XXX 的 CLI 工具">
- 仓库地址：<填，比如 https://github.com/xxx/yyy>
- License：<填，比如 MIT / Apache-2.0>
- 技术栈：<填，比如 Python 3.10+ / Node 20 / Go 1.22>
- 关键依赖：<填，比如 requests、PyGithub、Vue 3>
- 支持平台：<填，比如 Windows / macOS / 跨平台>
- 发布方式：<填，比如 GitHub Releases / PyPI / npm>
- 项目主色（可选）：<填，比如 #3776AB，用于徽章配色>

【导航链接】（能推断就自动填，不存在的省略，不留空位、不写假链接）
- 下载：默认 https://github.com/<owner>/<repo>/releases
- 文档：<在线文档 URL / docs 目录 / Wiki 链接 / 无>
- 在线体验：<Demo URL / Playground URL / 无>
- 更新日志：默认 https://github.com/<owner>/<repo>/blob/main/CHANGELOG.md
           （若无 CHANGELOG 则指向 Releases）
- 反馈：默认 https://github.com/<owner>/<repo>/issues
- 贡献：默认 https://github.com/<owner>/<repo>/blob/main/CONTRIBUTING.md
       （若无此文件则省略）

【项目功能】
- 功能 1：<填>
- 功能 2：<填>
- 功能 3：<填>

【安装与使用】
- 普通用户怎么用：<填>
- 开发者怎么用：<填>

【项目结构】（可选）
<粘贴目录树，或写"无">

【扩展方式】（可选）
<填>

【Logo 处理规则（严格按优先级执行，命中即停）】

第 1 优先 · 检查固定位置
- 先看 docs/logo.png 是否存在
- 存在 → 直接使用，不做任何扫描、迁移、生成
- 不存在 → 进入第 2 优先

第 2 优先 · 在项目里寻找现有 Logo
- 扫描以下位置（按优先级，命中即停）：
    · 根目录：logo.png / logo.svg / icon.png / icon.svg
    · assets/、asset/、static/、public/、resources/、
      images/、img/、.github/ 等资源目录
    · build/appicon.png（Wails）、build/icon.png（Electron）
      等构建目录
    · docs/、doc/ 目录
    · 文件名含 logo / icon / brand 的图片
- 扩展名优先级：PNG > SVG > JPG/JPEG > WEBP
- 找到候选：
    · 如果候选唯一 → 直接迁移
    · 如果有多个 → 列出清单让我选
    · 如果对话里我已明确说过"直接迁移" → 按优先级选第一个
- 迁移动作：
    mkdir -p docs
    cp <源文件> docs/logo.png
  若源文件是 SVG 且希望保留矢量：
    cp <源文件> docs/logo.svg  （引用时改用该路径）
- 迁移后报告：已将 <源路径> 复制为 docs/logo.png
- 未找到任何候选 → 进入第 3 优先

第 3 优先 · 生成一个临时 Logo
- 用 SVG 生成一个简洁的字母 Logo，风格：
    · 底色：项目主色（若提供）或中性灰 #333
    · 文字：项目名首字母（大写）或缩写，白色，居中
    · 尺寸：正方形 viewBox="0 0 256 256"
    · 圆角矩形或圆形背景
- 保存为 docs/logo.svg
- 在输出末尾报告：
    "项目里没找到 Logo，已生成占位 SVG：docs/logo.svg"

第 4 步 · 头部引用（统一的写法）
- 优先 PNG：<img src="docs/logo.png" alt="<项目名>" width="120">
- 若无 PNG 但有 SVG：<img src="docs/logo.svg" alt="<项目名>" width="120">
- 不用 ![]() Markdown 图片语法，必须用 <img> 标签
- alt 必须等于项目名
- 宽固定 120px

【视觉元素要求】
1. 顶部使用居中块（HTML <div align="center">），包含：
   - 项目 Logo：按上面【Logo 处理规则】执行
   - 一级标题（项目名）
   - 一句话定位（加粗）
   - 一行简洁的徽章（不超过 5 个，含 Build / Release /
     License / Platform / 主技术栈；不要徽章墙）
   - 一行固定顺序的导航链接，规则：
       · 从这 6 个里选：【下载】【文档】【在线体验】【更新日志】【反馈】【贡献】
       · 顺序固定：下载 → 文档 → 在线体验 → 更新日志 → 反馈 → 贡献
       · 只列出该项目真实拥有的链接，没有的位不占位、不写假链接
       · 命名不得替换为同义词（不要写"官方网站""了解更多""点这里"）
       · 分隔符统一用 ·，如：下载 · 文档 · 反馈
       · 能推断的自动填：
           下载 → <repo>/releases
           反馈 → <repo>/issues
           更新日志 → <repo>/blob/main/CHANGELOG.md（无则用 releases）
           贡献 → <repo>/blob/main/CONTRIBUTING.md（无则省略）
       · 至少保留一个链接（一般是 下载 或 反馈）
2. 每个主要章节标题前加一个 emoji 图标，形成视觉节奏
   （例如 🚀 快速开始 / ⚙️ 配置 / 🛠️ 开发）
3. 功能列表用「表格」呈现（列：功能 | 说明），每行开头带 emoji
4. 主界面截图 / 演示 GIF 用占位：docs/screenshot-main.png、
   docs/demo.gif；同时在代码里注释说明如何替换
5. 警告、提示、注意事项使用 GitHub Callout 语法：
   > [!NOTE] / > [!TIP] / > [!WARNING] / > [!IMPORTANT]
6. 次要信息（环境变量完整列表、常见问题、命令参考）
   用 <details><summary> 折叠
7. 键盘按键用 <kbd> 标签，如 <kbd>Ctrl</kbd> + <kbd>`</kbd>
8. 分隔章节使用 --- 水平线

【结构要求（按顺序）】
- 居中头部（Logo + 标题 + 定位 + 徽章 + 导航）
- 目录（TOC，锚点可跳转）
- 💡 这是什么（一句话 + 3~5 行说明"解决什么问题"、
  "适合谁"、"和同类工具的区别"）
- ✨ 功能（表格）
- 🚀 安装（分"下载即用"和"从源码安装"两小节）
- 📖 使用（分步操作，命令可复制；配合截图占位）
- ⚙️ 配置（如有环境变量 / 配置文件，用表格 + 折叠块）
- 🛠️ 开发（前置要求、运行、打包、CI）
- 📁 项目结构（代码块展示目录树）
- 🧩 扩展（可选，项目设计为可扩展时）
- 🗺️ 路线图（可选，从 Issue 提取）
- 🤝 贡献（简短，指向 Issue / PR）
- 📄 License

【精简原则（readme-optimization）】
- 徽章 ≤ 5 个，删掉"Views / Stars / Forks"这类噪音徽章
- 每一段尽量 ≤ 3 行；超过就拆成列表或表格
- 删掉"功能强大""业界领先"等空话
- 删掉重复出现的信息（同一命令不要在多处重复）
- 顶部导航里出现的链接（如下载、文档），TOC 里不必再列一遍
- 优先级：让新用户在 10 秒内知道"这是什么、要不要用、怎么装"

【Markdown 规范】
- 必须能通过 markdownlint
- 标题前后空行，层级不跳级（# → ## → ###）
- 代码块必须标语言
- 列表统一用 -
- 表格用 | :--- | 对齐
- 行尾无多余空格
- 不要出现空链接 [](...)、不要出现 GitHub 渲染残留的
  camo.githubusercontent.com 图片链接

【真实性】
- 只使用我提供的信息，不编造命令、文件、版本号
- Logo 优先级：先查 docs/logo.png → 再找项目现有 Logo →
  都找不到时才生成 SVG 占位；不凭空编造其他素材
- 信息不足的章节直接省略
- 若我提供了项目主色，徽章配色请尽量贴近

【输出前检查清单】
逐条自查，全部通过后输出：
- 结构章节按顺序齐全（省略项有明确理由：信息不足或可选）
- 徽章 ≤ 5 个，无 Views / Stars / Forks 等噪音徽章
- Logo 处理（严格按优先级）：
    · 第 1 步：是否先检查了 docs/logo.png 存在？
    · 第 2 步：不存在时是否扫描了项目现有 Logo？
    · 第 3 步：都没有时是否生成了 docs/logo.svg？
    · 头部引用路径与实际落盘文件一致
    · 使用了自动生成的 Logo 时，是否有 HTML 注释提示替换
    · 输出末尾是否报告了 Logo 的实际处理结果
      （直接使用 / 已迁移 / 已生成）
- 导航链接只用固定的 6 个词（下载/文档/在线体验/更新日志/反馈/贡献），
  顺序正确，无同义词替换，无假链接，无占位空位
- 每段 ≤ 3 行，无空话，无重复命令
- 视觉规范全部应用（居中头部、emoji 标题、特性表格、占位注释、
  Callout、折叠块、---）
- markdownlint 可通过（标题层级、代码块语言、列表符号、
  表格对齐、行尾空格）
- 只含用户提供的事实，无编造的命令 / 文件 / 版本号
- 占位图片 / GIF 位置有 HTML 注释标注替换方式

【输出】
- 直接输出完整的 README.md
- 不要省略任何章节
- 不要加任何解释性前言或结语
- 若引用了占位图片 / GIF，请在对应位置用 HTML 注释标注：
  <!-- 替换为实际截图：docs/screenshot-main.png -->
- 如果第 2 步执行了 Logo 迁移，在 README 之外**单独一行**报告：
  "已迁移 Logo：<源路径> → docs/logo.png"
- 如果第 3 步生成了占位 Logo，在 README 之外**单独一行**报告：
  "项目里没找到 Logo，已生成占位 SVG：docs/logo.svg"
- 如果直接复用了 docs/logo.png，在 README 之外**单独一行**报告：
  "已复用 docs/logo.png"