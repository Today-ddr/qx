# 全平台代理定制终极配置库 (Quantumult X · Loon · Surge 5)

自用全平台代理配置同步与分流工程。全面同构策略逻辑，涵盖去开屏/信息流广告、应用净化、AIGC (Gemini/ChatGPT/Claude) 独立分流（默认日本置顶）、原生 DoQ/DoH 加密解析、国内微信/会议极速直连、流媒体整合与内网防劫持。

---

## 📁 目录架构与客户端支持

```text
Today-ddr/qx/
├── qx/       # 🚀 Quantumult X 专区 (定制终极配置 + B站净化规则片段 + 脚本)
├── loon/     # 🎈 Loon 专区 (可莉极简基底 + QX 全同构终极配置)
└── surge/    # ⚡️ Surge 5 专区 (深巷有喵基底 + QX 全同构 + 极简菜单 + 4大原生插件)
```

---

## 🚀 极速导入直链

### 1. Quantumult X 专区
* 详细说明与规则片段：[查看 qx/README.md](./qx/README.md)
* **GitHub Raw 直链**：
  ```text
  https://raw.githubusercontent.com/Today-ddr/qx/main/qx/QuantumultX_Custom.conf
  ```
* **jsDelivr CDN 直链**（国内免代理秒开）：
  ```text
  https://cdn.jsdelivr.net/gh/Today-ddr/qx@main/qx/QuantumultX_Custom.conf
  ```

---

### 2. Loon 专区
* 详细说明与插件配置：[查看 loon/README.md](./loon/README.md)
* **GitHub Raw 直链**：
  ```text
  https://raw.githubusercontent.com/Today-ddr/qx/main/loon/Kelee_Custom.conf
  ```
* **jsDelivr CDN 直链**（国内免代理秒开）：
  ```text
  https://cdn.jsdelivr.net/gh/Today-ddr/qx@main/loon/Kelee_Custom.conf
  ```

---

### 3. Surge 5 专区
* 详细说明与架构文档：[查看 surge/README.md](./surge/README.md)
* **GitHub Raw 直链**：
  ```text
  https://raw.githubusercontent.com/Today-ddr/qx/main/surge/Surge_Custom.conf
  ```
* **jsDelivr CDN 直链**（国内免代理秒开）：
  ```text
  https://cdn.jsdelivr.net/gh/Today-ddr/qx@main/surge/Surge_Custom.conf
  ```

---

## 🌟 核心特色与三端同构亮点

1. **AIGC 策略同构（默认日本节点置顶优先）**：
   * 三端统一设置 `🤖 AIGC`（OpenAI / Claude / Gemini / Copilot），默认首选 **`🇯🇵 日本节点`**，剔除香港节点，彻底避免 403 地区阻断与封号风险。
2. **多端原生去广告与净化**：
   * **QX**：内置 `bilibili.snippet` 深度净化 B 站，搭配墨鱼、RuCu6、fmz200 去广告规则；
   * **Loon**：精选可莉生态插件，涵盖 B站、YouTube、Spotify、网易云等全量去广告；
   * **Surge**：原生嵌入 Maasea YouTube 深度去广告、DualSubs 双语字幕、Spotify 电脑端去广告与歌词增强。
3. **极简优雅体验**：
   * Surge 顶栏菜单极简折叠（方案 B，仅保留 9 项高频策略，底层节点折叠至二级子菜单）；
   * 精简规范化 `skip-proxy`，杜绝 macOS 字符截断警告与切网断连。
4. **隐私与安全安全脱敏**：
   * 公开仓库 100% 移除私有 Sub-Store 订阅 Token 与自签 CA 证书凭据，即开即用、安全纯净。
