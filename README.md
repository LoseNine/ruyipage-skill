# ruyipage-skill

中文 | [English](README_EN.md)

`ruyipage-skill` 是一个面向 `ruyiPage` 的、跨工具可用的 AI skill 知识仓库。

这个仓库的目标，是帮助编码类 AI 工具基于 `ruyiPage` 的官方文档、examples 和 WebDriver BiDi 相关资料，更稳定地理解、分析、编写和解释 `ruyiPage` 自动化脚本。

这个仓库以 Markdown 为核心组织知识，可被多种 AI 工具复用，也适合作为 `ruyiPage` 相关自动化与分析任务的参考资料。

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
