# ruyipage-skill

中文 | [English](README_EN.md)

`ruyipage-skill` 是一个面向 `ruyiPage` 的开源 AI skill，让 AI 在编写 ruyiPage 自动化脚本时遵循正确的实践。

核心原则：

1. **BiDi 优先** — 优先使用 BiDi 原生行为；需要 JS 交互时，使用完整拟人事件链 + `ruyi` 通过 `isTrusted` 检测
2. **拟人化** — 随机延迟、自然节奏、真实交互顺序
3. **身份隔离** — 每个新身份使用独立 `user_dir`
4. **指纹一致** — 反风控场景下 WebRTC、语言、时区、地理位置与 IP 保持一致
5. **API 可溯源** — 不确定的 API 必须核对官方仓库，禁止编造

## 使用方法

### 1. 下载仓库

```bash
git clone https://github.com/LoseNine/ruyipage-skill.git
```

或者直接在 GitHub 页面下载 ZIP。

### 2. 让 AI 读取 skill

AI 只需先读取 `SKILL.md`，其中包含核心规则和快速 API 参考。

`SKILL.md` 会根据当前任务场景，指引 AI 按需读取对应的 docs 文件：

| 场景 | 文档 |
|------|------|
| 优先级体系 | `docs/core-principle.md` |
| 拟人化交互 | `docs/humanized-automation.md` |
| 指纹浏览器 | `docs/fingerprint-browser.md` |
| 环境探测 | `docs/environment-detection.md` |
| 网络抓包协同 | `docs/data-capture-coordination.md` |
| 复杂页面定位 | `docs/complex-page-location.md` |
| 页面分析与定位 | `docs/page-analysis-and-location.md` |

### 3. 环境要求

- `ruyiPage` Python 包（`pip install ruyipage`）
- 官方 `ruyiPage` 仓库与 examples
- 风控场景下按需配合官方 Firefox 指纹浏览器

### 4. 官方相关项目

- `ruyiPage`: <https://github.com/LoseNine/ruyipage>
- Firefox 指纹浏览器: <https://github.com/LoseNine/firefox-fingerprintBrowser>
