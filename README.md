# ruyipage-skill

中文 | [English](README_EN.md)

`ruyipage-skill` 是一个面向 `ruyiPage` 的开源 AI skill。

当前版本先聚焦一个核心原则：

- 在进行自动化行为时，优先使用 BiDi 原生行为，或使用完整的 JS 拟人事件链加 `ruyi` 属性通过 `isTrusted` 检测
- 所有自动化行为默认追求拟人化、随机化、节奏自然化
- 默认优先新建独立 `user_dir` 做身份隔离
- 如果进入风控场景，优先学会配合官方 Firefox 指纹浏览器进行指纹变换
- 指纹变换必须注意一致性，尤其是 WebRTC、语言、时区、地理位置、speech 与 IP 对应关系
- 在实际网页数据采集时，自动化行为与网络包监听必须协同设计，自动化负责触发真实页面行为，网络监听负责按 `request_id` 等链路证据抓取请求与响应
- 面对复杂页面时，要能够处理 iframe 嵌套、复杂输入入口、甚至 closed shadow_root 一类高难定位场景，并参考 `quickstart_cloudfare.py` 这类真实页面处理方式持续探测定位点
- 在具体写代码时，如果对 `ruyiPage` API 不够确定，必须先核对官方 GitHub 仓库与 examples，必要时再核对本地源码，禁止编写虚假 API
- 源码核对的最高优先级是官方开源地址：<https://github.com/LoseNine/ruyipage>；如果本地副本落后，应该先更新到较新版本后再继续判断 API

## 使用方法

### 1. 下载仓库

```bash
git clone https://github.com/LoseNine/ruyipage-skill.git
```

或者直接在 GitHub 页面下载 ZIP。

### 2. 让 AI 读取 skill

推荐让 AI 先读取：

1. `SKILL.md`
2. `docs/core-principle.md`
3. `docs/humanized-automation.md`
4. `docs/fingerprint-browser.md`
5. `docs/data-capture-coordination.md`
6. `docs/complex-page-location.md`

### 3. 环境要求

默认要求自动化行为基于以下环境：

- `ruyiPage` Python 包
- 官方 `ruyiPage` 仓库与 examples
- 风控场景下按需配合官方 Firefox 指纹浏览器

如果环境缺失，先探测再安装或下载后继续；如果本地参考副本落后，优先同步官方仓库后再继续。

### 4. 官方相关项目

- `ruyiPage`: <https://github.com/LoseNine/ruyipage>
- Firefox 指纹浏览器: <https://github.com/LoseNine/firefox-fingerprintBrowser>

### 5. 指纹浏览器默认路径

默认约定：

- Windows `C` 盘默认安装路径的 Firefox 浏览器，就是这里约定使用的指纹浏览器

如果实际环境不同，先探测真实浏览器路径，再决定是否需要显式指定。
