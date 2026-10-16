# Loon 定制与进阶配置指南

本项目包含适用于 **Loon**（iOS / macOS）的高性能自用与通用配置模版，涵盖主流流媒体分流、AIGC/Gemini独立策略、节点自动化正则分组、QUIC拦截、DNS优化与常用插件生态。

---

## 📁 主配置文件说明

- **[Kelee_Custom.conf](./Kelee_Custom.conf)**：**⭐ Loon 定制终极配置（可莉基底 + QX 全同构）**。以可莉最小基础配置为模板基底，完美融合您专属的策略分流（AIGC日本置顶、Google、Telegram、Spotify去广告与双语歌词、YouTube、Netflix、苹果、微软、漏网之鱼与完整插件生态）。

---

## 🚀 导入链接

### 专属定制配置（Kelee_Custom.conf）
- **GitHub Raw 直链**：
  ```
  https://raw.githubusercontent.com/Today-ddr/qx/main/loon/Kelee_Custom.conf
  ```
- **jsDelivr CDN 极速直链**（国内免代理直连）：
  ```
  https://cdn.jsdelivr.net/gh/Today-ddr/qx@main/loon/Kelee_Custom.conf
  ```

---

## 📲 导入与使用步骤

1. 打开 **Loon** App。
2. 进入底部标签页 **「配置」**（Config）。
3. 点击右上角的 **「+」** 号，选择 **「从 URL 下载」**。
4. 粘贴上方直链链接，点击确定下载并激活配置。
5. **添加节点订阅**：
   - 方式 A：进入 **「配置」** -> **「节点订阅」** -> 点击右上角加号填入您的机场订阅链接。
   - 方式 B：在文本模式下编辑 `[Remote Proxy]` 段落，填入订阅链接。
6. **安装并信任 MitM CA 证书**（如需去广告与脚本）：
   - 进入 **「配置」** -> **「证书管理」** -> **「生成新的 CA 证书」**。
   - 点击 **「安装 CA 证书」**，前往系统【设置】->【已下载描述文件】完成安装。
   - 前往系统【设置】->【通用】->【关于本机】->【证书信任设置】开启完全信任。

---

## 🌟 社区主流开源模版与参考推荐

| 项目名称 / 作者 | 说明与特点 | GitHub 链接 |
| :--- | :--- | :--- |
| **Loon 官方示例库** | 官方全语法与字段参数示例，规范标准 | [Loon0x00/LoonExampleConfig](https://github.com/Loon0x00/LoonExampleConfig) |
| **可莉的资源库 (luestr)** | 国内外分流与策略组极佳，更新勤快 | [luestr/ProxyResource](https://github.com/luestr/ProxyResource) |
| **fmz200 / wool_scripts** | 知名懒人去广告、活动签到与插件库 | [fmz200/wool_scripts](https://github.com/fmz200/wool_scripts) |
| **YueChan / Loon** | 经典个人自用配置，结构清晰规范 | [YueChan/Loon](https://github.com/YueChan/Loon) |
| **Sub-Store** | 必备订阅管理与节点清洗神器 | [Peng-YM/Sub-Store](https://github.com/Peng-YM/Sub-Store) |

---

## 🧩 常用推荐插件（可在 Loon 插件中心一键安装）

1. **Sub-Store**：订阅转换、节点去广告、重命名与组合（已默认内置在 `Loon_Custom.conf` 的 `[Plugin]` 中）。
2. **BoxJs**：脚本参数管理与持久化 Web UI。
3. **Bilibili 净化 / 微信公众号去广告**：各大去广告作者（ddgksf2013、chxm1023、可莉等）均提供一键 `.plugin` 插件。
