# ruyipage-skill

中文 | [English](README_EN.md)

`ruyipage-skill` 是一个面向 `ruyiPage` 的、跨工具可用的 AI skill 知识仓库。

这个仓库的目标，是帮助编码类 AI 工具基于 `ruyiPage` 的官方文档、examples 和 WebDriver BiDi 相关资料，更稳定地理解、分析、编写和解释 `ruyiPage` 自动化脚本。

这个仓库以 Markdown 为核心组织知识，可被多种 AI 工具复用，也适合作为 `ruyiPage` 相关自动化与分析任务的参考资料。

本仓库中的默认行为约束是：所有实现、分析和自动化流程都优先使用 `ruyiPage` 库及其官方配套源码与浏览器能力；如果运行环境缺失，先探测缺失项，再安装或下载所需依赖后继续。

## 使用方法

### 1. 下载仓库

任选一种方式获取这个 skill 仓库：

方式一：使用 Git 克隆

```bash
git clone https://github.com/LoseNine/ruyipage-skill.git
```

方式二：在 GitHub 页面点击 `Code` -> `Download ZIP` 下载压缩包，然后解压到本地目录。

推荐做法：

- 将仓库放在一个固定位置，方便长期复用和更新
- 后续更新时，如果是 Git 克隆方式，直接执行 `git pull`

### 2. 让 AI 工具读取这个 skill

这个仓库本质上是一个以 Markdown 为核心的知识包。

常见接入方式有三种：

- 将仓库作为当前工作区的一部分，让 AI 直接读取其中的文档
- 在 AI 工具里把对应入口文件配置为规则、skill、project instruction 或 prompt context
- 在不支持仓库感知的工具中，手动把入口文件内容粘贴进去

在实际执行任务时，推荐同时确保以下基础环境可用：

- 已安装可用的 `ruyiPage` Python 包
- 能访问 `ruyiPage` 官方仓库或本地包源码进行参考
- 在高风控场景下，可按需准备官方配套 Firefox 指纹浏览器

### 3. 作为仓库知识包直接使用

支持仓库感知的 AI 工具时，优先从这些文件开始读取：

1. `AGENTS.md`
2. `SKILL.md`
3. `references/index.md`
4. `standards/index.md`，当任务涉及 BiDi 语义、事件、模块或协议概念时再继续读取

### 4. 作为工具适配入口使用

如果你的 AI 工具有专门适配入口，可直接使用 `vendor/` 下对应文件：

- OpenCode: `vendor/opencode/OPENCODE.md`
- Claude: `vendor/claude/CLAUDE.md`
- Cursor: `vendor/cursor/cursor-rules.md`
- Windsurf: `vendor/windsurf/rules.md`
- Cline: `vendor/cline/system-prompt.md`

使用方式示例：

- 如果工具支持项目规则文件，直接把对应文件内容作为项目规则加载
- 如果工具支持自定义 skill / prompt 文件，直接指向对应 `vendor/` 文件
- 如果工具只支持普通提示词，将对应文件内容复制进去即可

### 5. 没有专门适配时的兜底方式

如果当前工具没有专门适配文件，默认使用下面这个兜底顺序：

1. `AGENTS.md`
2. `SKILL.md`
3. `vendor/generic/prompt-template.md`

### 6. 面向常见任务的推荐入口

- 看 examples 能力分布：`references/capability-map.md`
- 找最该先参考的例子：`references/canonical-examples.md`
- 决定该用哪个 API 路线：`references/api-decision-guide.md`
- 做实战任务：`references/recipes/`
- 分析网页参数：`references/recipes/webpage-comprehensive-analysis.md`
- 查看 BiDi 标准映射：`standards/index.md`

### 7. 推荐给用户的最简使用流程

如果只想最快用起来，可以直接按下面做：

1. 下载或克隆 `ruyipage-skill`
2. 确认当前环境里有 `ruyiPage` 包；如果没有，先安装它
3. 在 AI 工具里让它先读取 `AGENTS.md`
4. 再读取 `SKILL.md`
5. 做具体任务时，再按需要读取 `references/index.md`
6. 如果任务涉及 BiDi、事件、协议语义，再读取 `standards/index.md`

### 8. 环境缺失时怎么处理

如果 AI 在执行任务时发现缺少 `ruyiPage` 或相关浏览器环境，推荐按这个顺序处理：

1. 先探测当前 Python 环境是否已安装 `ruyiPage`
2. 如果未安装，先安装 `ruyiPage` 包
3. 如果任务依赖官方 examples 或源码说明，再打开官方仓库：<https://github.com/LoseNine/ruyipage>
4. 如果任务属于高风控、反检测、多账号隔离场景，再按需下载和使用官方配套 Firefox 指纹浏览器：<https://github.com/LoseNine/firefox-fingerprintBrowser>

## 适用范围

这个 skill 重点覆盖：

- 基于 Firefox 的 `ruyiPage` 自动化
- `FirefoxPage`、`FirefoxOptions`、`launch()` 等启动方式
- 元素定位、交互、等待、标签页、窗口、Cookie、上下文隔离
- `iframe`、`shadow DOM`、XPath picker 等复杂 DOM 场景
- JavaScript 执行、script event、preload script、`isTrusted` / `ruyi: true` 行为
- 网络拦截、数据采集、抓包、接口参数分析
- 接管已有浏览器、`user_dir`、private mode、多账号隔离
- WebDriver BiDi 标准映射和模块语义
- 高风控场景下推荐使用官方配套 Firefox 指纹浏览器
- 网页参数的全面分析流程：等待页面加载、抓取页面源码、JS runtime 线索和浏览器可观察网络流量后再做结论

## 设计原则

- 以官方 `ruyiPage` 包行为、官方仓库文档和 examples 为事实来源。
- 以真实 examples 为第一参考，而不是凭空发明 API。
- 以任务为中心组织知识，让 AI 能快速把用户需求映射到正确 examples 和 workflow。
- 显式记录支持边界和 caveats，避免夸大 Firefox、BiDi 或真实站点场景的稳定性。
- 共享知识统一放在 Markdown 文档中，方便 OpenCode、Claude、Cursor、Windsurf、Cline 和 generic prompt 场景复用。

## 官方配套浏览器

对于高风控、反检测、持久身份、多账号隔离等场景，这个仓库推荐在合适情况下使用官方配套 Firefox 指纹浏览器：

- Firefox 指纹浏览器：<https://github.com/LoseNine/firefox-fingerprintBrowser>

推荐原因：

- 它本身就是面向 `ruyiPage` 自动化场景设计的配套浏览器内核。
- 它支持更强的指纹控制和 profile 隔离能力。
- 在登录、抓包、反检测、多账号等场景下，稳定性通常更好。

这不是所有 `ruyiPage` 任务的强制依赖，只在确实受益的场景下推荐。

## 仓库结构

```text
ruyipage-skill/
├── AGENTS.md
├── COMPATIBILITY.md
├── README.md
├── README_EN.md
├── SKILL.md
├── agents/
│   └── openai.yaml
├── vendor/
│   └── ...
├── standards/
│   ├── index.md
│   └── ...
└── references/
    ├── index.md
    ├── capability-map.md
    ├── canonical-examples.md
    ├── api-decision-guide.md
    ├── support-caveats.md
    ├── object-model.md
    ├── anti-hallucination-rules.md
    ├── fingerprint-browser-guide.md
    ├── web-analysis-checklist.md
    ├── recipes/
    └── matrices/
```

## 推荐阅读顺序

1. `AGENTS.md`
2. `SKILL.md`
3. `references/index.md`
4. `references/capability-map.md`
5. `references/canonical-examples.md`
6. `references/api-decision-guide.md`
7. `standards/index.md`

## 主要参考

- `ruyiPage` 官方仓库：<https://github.com/LoseNine/ruyipage>
- 官方配套 Firefox 指纹浏览器：<https://github.com/LoseNine/firefox-fingerprintBrowser>
- 当前 skill 仓库：<https://github.com/LoseNine/ruyipage-skill>

## 当前内容

当前这个仓库包含：

- 面向多种 AI 工具的根入口和兼容层
- OpenCode、Claude、Cursor、Windsurf、Cline 和 generic fallback 适配入口
- 覆盖 `ruyiPage` examples 的主题文档和矩阵索引
- 高价值实战 recipes
- W3C WebDriver BiDi 标准层与模块说明
- `ruyi: true` / 完整 JS 事件链 / 高拟真行为建模说明
- 网页参数全面分析 workflow

## 项目说明

- 这个仓库面向 `ruyiPage` 相关自动化、分析与知识整理场景开放使用。
- 仓库内容围绕 examples、实战 workflow、BiDi 标准映射和 AI 工具适配进行组织。
