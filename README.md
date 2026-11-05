# 京东 CK 工具集

三个配套的京东 Cookie 工具，全部 APK 从本仓库 Releases 下载，App 内置自动更新检查。

## 包含的 App

| App | 应用名 | Tag 前缀 | 说明 |
|---|---|---|---|
| **JdCookieLsp** | 豆豆管家 | `lsp-v*` | LSPosed 插件。注入京东进程直接读取 CookieStore（支持 root LSPosed 与 LSPatch 无 root 双框架），支持多账号。v1.33 起内置**脚本仓库**（20+ 京东活动脚本，云端一键更新）、**日志折叠与一键分享反馈**、**测试版通道自选**。 |
| **JdCkCapture** | JD CK 抓取器 | `capture-v*` | VPN 抓取器。基于 hev-socks5-tunnel + 本地 CA 解密京东流量，自动从 WebView 请求中提取 `pt_key`/`pt_pin` 并写入青龙面板，也可一键复制。**不需要 root**。 |
| **JdQlPush** | 青龙推送器 | `push-v*` | 手动提交/校验 CK 并推送到青龙面板，含失效检测。 |

## 最新版本

| App | 版本 | Tag |
|---|---|---|
| 豆豆管家 | **v1.33.0**（2026-11-05） | `lsp-v1.33.0` |
| JdCkCapture | v1.10.2 | `capture-v1.10.2` |
| JdQlPush | v1.0.0 | `push-v1.0.0` |

## 下载

到 [Releases](https://github.com/qq329192/jd-ck-tools/releases) 页面按 Tag 前缀找对应 App 的 APK。

## 自动更新

三个 App 启动时会静默查询本仓库的 Releases API：

1. 按 tag 前缀过滤出自己的版本序列（如 `lsp-v1.33.0`）
2. 与当前 `versionName` 做版本比较（能正确区分正式版与 beta）
3. 有新版 → 弹窗提示，点「去下载」跳转 APK 直链

只要在 GitHub 上发新 Release，手机端下次打开就会收到提醒。

**测试版通道**（豆豆管家 v1.33.0 起支持）：收到测试版弹窗时可自行选择「加入测试通道 / 仅下载一次 / 不加入」，不加入则永远只收正式版提醒。

## 使用提示

- 豆豆管家（JdCookieLsp）：
  - root 用户：LSPosed 勾选模块 + 作用域选京东，强停京东后生效。
  - 无 root：可用 LSPatch 修补京东（内置/便携模式 + 嵌入本模块，签名绕过选 `pm+openat`），或使用 App 内「H5 登录提取」「手动粘贴 Cookie」两条免 root 通道。
  - 运行日志支持重复行折叠，点「分享」可一键把日志（自带版本/机型/系统信息）发给开发者反馈问题。
- JdCkCapture 首次使用需安装其生成的 CA 证书（应用内引导）。
- 三个 App 抓取的 CK 格式统一为 `pt_key=xxx;pt_pin=xxx;`，可直接用于青龙 `JD_COOKIE`。

## 重要提醒

- **请使用你自己搭建的青龙面板**：Cookie 等同账号登录凭证，不要填入任何他人提供的服务器地址。
- **仅供学习交流**，使用本工具产生的一切账号风控、封禁风险由使用者自行承担。
- 请勿将本工具用于商业用途或二次分发收费。
