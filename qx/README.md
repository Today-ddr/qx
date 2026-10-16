# Quantumult X 定制综合终极配置指南

本项目包含适用于 **Quantumult X**（iOS / macOS）的高性能定制综合配置文件，深度融合全网去广告规则、AIGC / Gemini 独立分流、B站原生去广告净化、节点自动化测速与内网防劫持 DNS 优化。

---

## 📁 目录文件说明

- **[QuantumultX_Custom.conf](./QuantumultX_Custom.conf)**：**⭐ Quantumult X 定制终极配置文件**。
- **[bilibili.snippet](./bilibili.snippet)**：B站（Bilibili）全功能去广告与动态流净化重写分流规则片段。
- **[scripts/](./scripts/)**：B站去广告与辅助处理脚本。

---

## 🚀 导入链接

### 专属定制配置（QuantumultX_Custom.conf）
- **GitHub Raw 原生直链**：
  ```
  https://raw.githubusercontent.com/Today-ddr/qx/main/qx/QuantumultX_Custom.conf
  ```
- **jsDelivr CDN 极速直链**（国内免代理直连）：
  ```
  https://cdn.jsdelivr.net/gh/Today-ddr/qx@main/qx/QuantumultX_Custom.conf
  ```

---

## 🎯 核心特性与策略设计

1. **AIGC 专属策略（默认日本节点置顶）**
   * **`🤖 AIGC`**：包含 OpenAI (ChatGPT)、Claude、Google Gemini、Copilot 等，默认首选 **`🇯🇵 日本节点`**，剔除香港节点防封号与 403 地区阻断。
2. **Bilibili 深度净化**
   * 内置本地 `bilibili.snippet`，深度移除开屏广告、首页推荐牛皮癣、竖屏视频流广告与青少年弹窗，仅保留纯净视频内容。
3. **分流金字塔结构**
   * 微信国内直连防转圈、网银与运营商免密直连。
   * 流媒体整合分流（YouTube、Netflix、Disney+、Spotify）。
   * Apple / Microsoft CDN 极速直连。
4. **全自动化测速策略组**
   * 包含香港、台湾、日本、狮城、美国、韩国、英国专属正则智能分组，以及全节点最低延迟自动优选（`♻️ 自动选择`）。
5. **DNS 深度防泄漏**
   * 拦截 UDP 53，内网路由器后台（ASUS、小米、TP-Link 等）免 Fake-IP 直接穿透。

---

## 📲 导入与使用步骤

1. 打开 **Quantumult X**。
2. 点击右下角 **风车图标** 进入设置。
3. 滑动至底部 **「配置文件」** 区域，点击 **「下载」**。
4. 粘贴上方的直链 URL，点击确认下载覆盖。
5. 如需解密 HTTPS，请在 **「MitM」** 中生成并信任自签 CA 证书。
