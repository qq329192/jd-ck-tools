# 京东 CK 工具集

三个配套的京东 Cookie 工具，全部 APK 从本仓库 Releases 下载，App 内置自动更新检查。

## 包含的 App

| App | Tag 前缀 | 说明 |
|---|---|---|
| **JdCkCapture** | `capture-v*` | VPN 抓取器。基于 hev-socks5-tunnel + 本地 CA 解密京东流量，自动从 WebView 请求中提取 `pt_key`/`pt_pin` 并写入青龙面板，也可一键复制。**不需要 root**。 |
| **JdCookieLsp** | `lsp-v*` | LSPosed 插件。注入京东进程直接读取 CookieStore（支持 root LSPosed 与 LSPatch 无 root 双框架），支持多账号。 |
| **JdQlPush** | `push-v*` | 青龙推送器。手动提交/校验 CK 并推送到青龙面板，含失效检测。 |

## 下载

到 [Releases](https://github.com/qq329192/jd-ck-tools/releases) 页面按 Tag 前缀找对应 App 的 APK。

## 自动更新

三个 App 启动时会静默查询本仓库的 Releases API：

1. 按 tag 前缀过滤出自己的版本序列（如 `capture-v1.9.0`）
2. 与当前 `versionName` 做 semver 比较
3. 有新版 → 弹窗提示，点「去下载」跳转 APK 直链

只要在 GitHub 上发新 Release，手机端下次打开就会收到提醒。

## 使用提示

- JdCkCapture 首次使用需安装其生成的 CA 证书（应用内引导）。
- JdCookieLsp 无 root 模式需要用 LSPatch 修补京东（内置/便携模式 + 嵌入本模块，签名绕过选 `pm+openat`）。
- 三个 App 抓取的 CK 格式统一为 `pt_key=xxx;pt_pin=xxx;`，可直接用于青龙 `JD_COOKIE`。
