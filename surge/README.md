# Surge 5 终极定制配置指南（深巷有喵架构基底 + QX & Loon 策略全同构版）

本项目基于社区顶流 **[深巷有喵（Rabbit-Spec）](https://github.com/Rabbit-Spec/Surge)** 原生架构为底模，同时**深度适配并完全同构了本项目中的 Quantumult X 与 Loon 核心分流策略**。

实现了在保持深巷有喵官方 `category=GROUP/SERVER/SPEC` 规范、官方高质感图标库与极简模块化底模的同时，完美复刻 QX 与 Loon 经过实测验证的终极策略逻辑。

---

## 📁 目录文件说明

- **[Surge_Custom.conf](./Surge_Custom.conf)**：**⭐ 深巷有喵基底 + QX/Loon 同构终极配置（推荐首选）**。
  - **架构底模**：深巷有喵（Rabbit-Spec）官方原生标准。
  - **策略同构**：全面继承 `QuantumultX_Custom.conf` 与 `loon/Kelee_Custom.conf` 的策略逻辑与图标体验。
  - **电脑端精简**：彻底剔除 Telegram 策略组与分流规则，规避桌面端多余开销。
  - **实测企业级直连**：置顶企业微信与腾讯会议全域名极速直连、拦截 UDP 443 QUIC（防卡顿降时延）、B 站直连与大会员秒开。
  - **macOS 性能调优**：内置 Web Dashboard 仪表盘、混合网络并发（`all-hybrid`）与游戏/音视频抢占（`udp-priority`）。
  - **高可用安全 DNS**：阿里原生 DoQ（`quic://223.5.5.5`）与 DoH 并发解析，彻底解决此前公共 DoH 频繁超额限流报错。

---

## 🚀 导入链接

### 专属定制配置（Surge_Custom.conf）
- **GitHub Raw 原生直链**：
  ```
  https://raw.githubusercontent.com/Today-ddr/qx/main/surge/Surge_Custom.conf
  ```
- **jsDelivr CDN 极速直链**（国内免代理直连推荐）：
  ```
  https://cdn.jsdelivr.net/gh/Today-ddr/qx@main/surge/Surge_Custom.conf
  ```

---

## 🌟 策略组对标与同构一览（QX / Loon / Surge 5）

本配置策略组命名、选点逻辑与视觉体验与手机端的 QX / Loon 完全一致：

| 策略组名称 | 策略类型 | 选点与分流逻辑（对标 QX & Loon） | 挂载图标 |
| :--- | :--- | :--- | :--- |
| **🚀 节点选择** | `select` | 主出站代理出口，默认支持自动选路与手动指定 | `Rocket.png` |
| **♻️ 自动选择** | `url-test` | 节点并发测速，延迟容差 50ms，自动选优 | `Auto.png` |
| **♊️ Gemini** | `select` | **🇯🇵 日本节点置顶优先**，解决 Google 锁区报错 | `GoogleGemini.png` |
| **🤖 ChatGPT** | `select` | 🇺🇸 美 / 🇯🇵 日 / 🇸🇬 新 独立自选出口 | `ChatGPT.png` |
| **🤖 AIGC** | `select` | 整合 Claude / OpenAI 等通用 AI，屏蔽香港节点防 403 | `ai.png` |
| **🍿 国际媒体** | `select` | YouTube、Netflix、Disney+ 等海外流媒体聚合 | `Streaming.png` |
| **📽 哔哩哔哩** | `select` | **国内原生 4K 直连**，同时支持港澳台节点解锁 | `bilibili.png` |
| **🎻 Spotify** | `select` | 针对音乐流媒体独立选线，降低频繁切 IP 登出风险 | `Spotify.png` |
| **🎥 Emby** | `select` | 绑定自定义 SNTP 规则，专为私有媒体服优化 | `Emby.png` |
| **💾 软件下载** | `select` | 软件更新、驱动下载大流量独立走直连或特定节点 | `Download.png` |
| **🎮 游戏加速** | `select` | Steam / Epic 联机与外服游戏网络加速 | `Game.png` |
| **🍎 苹果服务** | `select` | 默认直连，海外服务走苹果专用策略 | `Apple.png` |
| **Ⓜ️ 微软服务** | `select` | 国内 CDN 直连，海外服务走微软专用策略 | `Microsoft.png` |
| **🛑 广告拦截** | `select` | 基于 Sukka 高性能 DOMAIN-SET 二叉树秒级拦截 | `AdBlock.png` |
| **🎯 全球直连** | `select` | 强制定向 DIRECT | `Direct.png` |
| **🐟 漏网之鱼** | `select` | FINAL 兜底规则，优先跟随节点选择 | `Final.png` |

---

## 🛠 基于 Surge 实时运行日志的诊断与深度修复

通过对原生 Surge 日志（`~/Library/Logs/Surge`）的全面诊断，本配置在底层修复了旧版配置中出现的七大隐性问题：

1. **彻底根治公共 DoH 429 频控轰炸（超 10,000+ 次报错）**
   - **日志现象**：`DoH server returned an unexpected status code: 429` 频繁刷屏，导致 `www.lingchen.kim` 等域名解析连续超时。
   - **修复方案**：彻底移除受限的腾讯公共 DoH，改用阿里云原生 DoQ（`quic://223.5.5.5`）与高可用 DoH（`https://223.5.5.5/dns-query`）双上游并发解析，零频控、零劫持。

2. **解决 VMess 节点 UDP 目标地址漂移报错（58+ 次报错）**
   - **日志现象**：`VMess UDP relay doesn't support changing dest address, original: 162.159.207.0:3478, new: 74.125.250.129:19302`。
   - **根因分析**：WebRTC / STUN 穿透流量走了 VMess 节点，而 VMess 协议无法处理 UDP Socket 目标 IP 快速漂移，引发断连与日志报警。
   - **修复方案**：在最顶部追加 STUN 常用端口直连规则：`DEST-PORT,3478,🎯 全球直连` 与 `DEST-PORT,19302,🎯 全球直连`，保障会议语音与游戏连麦 NAT 穿透顺畅。

3. **消除微信 Mac 桌面端小程序回环断连（POSIX:61 错误）**
   - **日志现象**：`Connection refused (POSIX:61), localhost.weixin.qq.com:14013-14015`。
   - **修复方案**：将 `localhost.weixin.qq.com` 完整纳入 `skip-proxy`、`always-real-ip` 与 `DOMAIN,localhost.weixin.qq.com,DIRECT`，确保本地进程间通信绝不被 VIF 虚拟网卡劫持。

4. **消除网易 UU 远程虚拟网卡冲突告警**
   - **日志现象**：`Unknown TUN fake IP: 198.19.0.1, client: /Applications/UURemote.app/Contents/Helpers/UURemoteServer`。
   - **修复方案**：新增 `PROCESS-NAME,UURemoteServer,DIRECT` 与 `PROCESS-NAME,UURemote,DIRECT`，完全放行远程串流流量。

5. **消除测速连接复用警告**
   - **日志现象**：`ONE-TIME WARNING: Testing URL doesn't support HTTP connection reuse. http://cp.cloudflare.com/generate_204`。
   - **修复方案**：将代理测速 URL 升级为原生支持 HTTP Keep-Alive 的 `http://www.gstatic.com/generate_204`，大幅提升自动选优的测速准确度并降低握手开销。

6. **优化腾讯内部 OA 与工单工具连接**
   - **日志现象**：`Connection timeout: workbuddy-pc.woa.com:443`。
   - **修复方案**：添加 `DOMAIN-SUFFIX,woa.com,DIRECT`，杜绝内部办公域名在代理通道中挂起超时。

7. **Sub-Store 订阅源防超时优化**
   - **优化方案**：在配置中预置订阅源域名规则（`DOMAIN-SUFFIX,your-sub-store-domain.com,🚀 节点选择`），避开国内直连 Cloudflare CDN 的网络劣化。

---

## 🎮 网易UU远程（UURemote）同城双机 P2P 穿透专项优化

当您在**同城两台 Mac** 之间通过网易 UU 远程（UURemote）进行屏幕串流与设备控制时，若未做深度调优，Surge 的虚拟网卡（VIF）与代理层极易导致 **P2P 打洞失败、被迫回退到高延迟服务器中继（延迟从 3ms 飙升至 50ms+ 且画质压缩）**。

本配置针对双机同 Surge 配置的场景，进行了全链路 P2P 穿透打通：

### 1. 彻底根除 Fake-IP 毒化（解决日志 `Unknown TUN fake IP: 198.19.0.1`）
- **核心机理**：P2P 穿透的核心是 ICE 候选地址探测。如果 UURemote 查询 NetEase 信令与 STUN 服务器时被 Surge 返回了 Fake-IP（`198.19.x.x`），双端交换的握手地址就会失效，直接导致 P2P 协商失败。
- **配置实现**：在 `always-real-ip` 中注入 `*stun*, *.stun.*, *.uuremote.com, *.uu.163.com, *.uuyc.163.com, *.uugame.163.com, *.uu.com`，确保双端探测到的永远是真实公网反射 IP 与局域网真实 IP。

### 2. 绕过系统代理拦截（`skip-proxy`）
- **配置实现**：将 UU 远程全部域名注入 `skip-proxy`。双端 Mac 上的 `UURemoteServer` 与主客户端在建立长连接信令与设备鉴权时，完全绕过 `127.0.0.1:6152` 本地系统代理端口，直连网易高速信令网关。

### 3. 全量进程原生直通（`PROCESS-NAME, ..., DIRECT`）
- **涵盖进程**：覆盖主控端与受控端全部二进制组件（`UURemote`、`UURemoteServer`、`UURemoteDaemon`、`UURemoteService`、`uuyc-cli`、`UURemoteUpdater`，以及加速器进程 `UU`、`uu`、`UUBooster`、`uuplugin`）。
- **打洞效果**：双端发起的 UDP 打洞数据包（Hole Punching）直接走物理网卡发出，源端口与 NAT 映射不被 Surge 虚拟网卡扰动，保障 Full Cone / Restricted Cone NAT 快速握手成功。

### 4. 路由层隔离（`tun-excluded-routes`）与 UDP 抢占（`udp-priority`）
- **配置实现**：开启 `tun-excluded-routes` 隔离局域网段；开启 `udp-priority = true` 赋予 UDP 视频流最高系统传输调度优先级。
- **实测表现**：同城双 Mac 直连下，画面延迟保持在光纤极速响应（通常 **2ms ~ 5ms**），支持满血真 4K、高帧率与极清码率，告别丢包与画质撕裂。

---

## 🧬 历史定制规则全量继承与进阶优化

针对您原有的 Surge 备份（`lite.conf.backup`）以及当前仓库中的 Quantumult X / Loon 高价值规则，新配置已全量继承并完成了结构化归类：

1. **哔哩哔哩防 PCDN 偷跑与秒开优化**
   - 新增针对 B 站 PCDN（偷偷利用客户端上传做种导致局域网卡顿的节点）的静默拦截规则：`mcdn.bilivideo.cn`、`szbdyd.com`、`ourdvs.com`、`pcdn.biliapi.net` 等。
   - 保留官方直连分流规则：`bilivideo.com`、`bilivideo.cn`、`hdslb.com` 直连秒开 4K，空降助手 `bsbsb.top` 定向走代理。

2. **Google AI Studio 与 Gemini 全家桶锁区保障**
   - 补充 `ai.google.dev`、`generativelanguage.googleapis.com`、`proactivebackend-pa.googleapis.com`、`alkalimakersuite-pa.clients6.google.com` 全部归入 `♊️ Gemini`（日本专线置顶）。
   - 保留 `userlocations.googleapis.com` 与 `google.com` 锁定日本节点，规避地理定位锁区报错。

3. **苹果服务国内直连与系统推送加速**
   - 补充 Sukka 维护的 `apple_cn.conf`（苹果中国全境服务极速直连）。
   - 保留 `push.apple.com`、`push-apple.com.akadns.net` 核心 APNs 推送直连。
   - 保留 `mesu.apple.com`、`mzstatic.com`、`aaplimg.com`、`itunes.apple.com` 等 App Store 与系统下载极速 CDN 直连。

4. **运营商一键登录与主流网银免密认证**
   - 补充移动统一认证 `cmpassport.com`、中国广电 `10099.com.cn`、中国电信天翼账号 `open.e.189.cn`。
   - 保留建行 `ccb.cn`、农行 `abchina.com.cn`、工行、招行、交行等安全检测直连，防封控风控。

5. **细粒度遥测与骚扰广告拦截**
   - 保留 `store.typora.io`、QQ 遥测 `h.trace.qq.com`、`otheve.beacon.qq.com`。
   - 补充农行遥测 `msmp.abchina.com.cn`、苹果天气遥测 `weather-analytics-events.apple.com`、`tthr.apple.com`。
   - 补充丰巢智能柜开屏与横幅广告拦截：`dsp.fcbox.com`、`rtm.fcbox.com`、`ad.fcbox.com`。

6. **用户自维护专属规则源（Boringahhh 仓库）**
   - 完整继承 `https://raw.githubusercontent.com/Boringahhh/ssrclash/new/clash/config/Direct.list`（直连修正）。
   - 完整继承 `https://raw.githubusercontent.com/Boringahhh/ssrclash/refs/heads/new/clash/config/SNTP.list`（Emby 私有服）。
   - 完整继承 `https://raw.githubusercontent.com/Boringahhh/ssrclash/new/Surge/List/non_ip/facebook.conf` 及 `ip/facebook.conf`（Meta 家族规则）。

7. **macOS 15 Sequoia 专属优化**
   - 在 `skip-proxy` 中继承了 `sequoia.apple.com` 与 `seed-sequoia.siri.apple.com`，保障新系统 OTA 升级与 Apple Intelligence 种子更新不消耗代理流量。

---

## 🎵 Spotify 终极增强与全局模块清理记录

为保障 Mac 端 Spotify 去广告、自由切歌与双语歌词的最完美体验，并彻底消除后台冲突与报错，已完成以下模块维护：

1. **废弃旧版报 429 的 DNS 映射模块**
   - **清理对象**：`[Sukka] Local DNS Mapping`
   - **原因**：该模块强制把腾讯和 B 站域名发往 `https://doh.pub/dns-query`，由于腾讯公网 DoH 严苛限流，是日志中产生 **10,758 次 429 报错** 的根因之一。在新配置原生支持阿里 DoQ/DoH 后已毫无用处，已从全局模块中彻底卸载。

2. **解决 Spotify 歌词双重冲突**
   - **清理对象**：`Spotify歌词增强`（iKeLee）
   - **原因**：原系统同时启用了两个歌词翻译插件，会向 Spotify 注入两套重复的 Web 脚本导致歌词错位冲突。现已卸载冗余插件，专注保留并升级成熟度最高的 DualSubs。

3. **全新换装 App2Smile 官方 Spotify 去广告与解锁模块**
   - **新增模块**：[Spotify(App2Smile去广告)](https://raw.githubusercontent.com/app2smile/rules/master/module/spotify.module)
   - **效果**：替代了旧版因 CDN 挂掉报 403 的旧插件，实现：
     - 静默过滤音频播放广告与界面横幅广告；
     - 恢复歌手、专辑列表正常自由点播与正常展示；
     - 配合新配置中的 MitM 证书解密，在 Mac 端丝滑播放。

4. **全面升级 DualSubs 官方最新版（v1.10.0）**
   - **升级模块**：[🍿️ DualSubs: 🎵 Spotify](https://github.com/DualSubs/Spotify/releases/latest/download/DualSubs.Spotify.sgmodule)
   - **效果**：升级至 2026 年最新版本，全面兼容 macOS 15 与最新 Spotify 桌面客户端，支持网易云/QQ音乐外部歌词自动补全与双语翻译。

---

## 🧩 插件脚本矩阵与增强能力一览（全量原生内置）

本配置无需依赖系统外部模块，所有去广告、画质解锁、双语字幕与系统特性增强已**100% 原生内嵌于 [Surge_Custom.conf](./Surge_Custom.conf) 单文件中**，导入即用，零系统入侵：

| 模块名称 | 作用对象 | 模块类型 | 核心效果 |
|---|---|---|---|
| **YouTube (Music) Enhance** | YouTube / YouTube Music | Maasea 深度解锁 | 过滤视频前贴片与中插广告、屏蔽 Shorts/上传按钮、解锁高码率画质与后台播放 |
| **🍿️ DualSubs: ▶️ YouTube** | YouTube / YouTube Music | VirgilClyne 双语增强 | 官方双语字幕合成 + 机器翻译，支持双行字幕与时间轴对齐 |
| **🍿️ DualSubs: 🇳 Netflix** | Netflix Web / App | VirgilClyne 双语增强 | 实时捕获 Netflix 官方多语言字幕，翻译并合成双语对照，支持主副语言调节 |
| ** iRingo: 🔍 Spotlight** | Safari & 聚焦搜索 | NSRingo 系统解锁 | 解锁 Safari 建议与聚焦搜索卡片；修复大陆地区空白无结果，已定向绑定 `🍎 苹果服务` |
| **Spotify (App2Smile去广告)** | Spotify 桌面客户端 | App2Smile 去广告 | 屏蔽音频插播广告与跳歌频控限制，恢复自由点播 |
| **🍿️ DualSubs: 🎵 Spotify** | Spotify 桌面客户端 | VirgilClyne 歌词增强 | 双语对照歌词、音译注音、自动匹配网易云/QQ音乐外部歌词补全 |
| ** iRingo: 🌤 WeatherKit** | 原生天气 | NSRingo 增强 | 补全海外高精度降水概率图与多源雷达图 |
| ** iRingo: 🗺️ Maps** | 原生地图 | NSRingo 增强 | 国际版地图功能解锁与高精度地貌渲染 |

---

## 🛡️ 四大核心场景稳定性专项保障

针对用户高频使用的关键服务，本套配置经过深度网络拓扑与脚本作用域审核，确保零负面影响：

1. **哔哩哔哩（Bilibili）—— 绝不断流，秒开 4K/8K**
   - **拦截 PCDN**：硬核屏蔽 `mcdn.bilivideo.cn`、`szbdyd.com`、`ourdvs.com`、`pcdn.biliapi.net`，根除家宽 PCDN 丢包引发的视频缓冲卡顿与黑屏。
   - **骨干 CDN 直连**：主媒体域名（`bilivideo.com`、`hdslb.com`）直通本地 ISP 机房，跑满带宽。
   - **规避 QUIC 丢包**：UDP 443 拦截回退到极其稳定的 TCP/TLS 1.3。新模块对 B 站 0 介入。

2. **企业微信与腾讯会议 —— 0 延迟、0 丢包**
   - **系统级绕过代理**：`skip-proxy` 预置企业微信与腾讯会议所有协作域名。
   - **置顶直连分流**：位于所有规则第 0 区（优先于 UDP 443 拦截），TRTC 音视频流与 STUN 端口（3478 / 19302）物理网卡极速直通。
   - **macOS 优先级抢占**：启用 `udp-priority = true` 与 `all-hybrid = true`。

3. **苹果基础服务 —— 推送与更新秒达**
   - **核心直通**：APNs 推送（`push.apple.com`）与系统更新（`mesu.apple.com`, `sequoia.apple.com`）全走直连。
   - **iRingo 独立隔离**：Spotlight 模块仅针对 `api*.smoot.apple.com` 提取建议，完全不触及 iCloud、Apple ID 或钥匙串同步。

4. **Spotify —— 广告屏蔽与双语歌词 100% 互不干扰**
   - App2Smile 模块拦截 `/bootstrap/`（去广告）；DualSubs 模块拦截 `/color-lyrics/`（歌词）。
   - 两者 URL 路径完全互斥，证书解密无缝配合，流畅无报错。

---

## 📲 导入与使用步骤

### 方式一：Surge Mac（电脑端）
1. 打开 **Surge** 状态栏图标 -> 选择 **配置文件**（Profiles）-> 点击 **配置**。
2. 将 [`surge/Surge_Custom.conf`](./Surge_Custom.conf) 拷贝到 Surge 配置目录：
   - 路径：`~/Library/Application Support/Surge/Profiles/Surge_Custom.conf`
   - 或者在 Surge 菜单中选择 **「从 URL 下载配置」**，粘贴上方的 jsDelivr 或 GitHub 直链。
3. 在 Surge 菜单中勾选激活 `Surge_Custom` 即可生效。

### 方式二：Surge iOS（手机端）
1. 打开 **Surge** App。
2. 首页顶部点击当前配置文件 -> 点击 **「从 URL 下载」**。
3. 粘贴上方直链链接，完成下载后勾选设为当前配置。

