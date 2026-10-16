# Quantumult X 定制综合配置

自用 Quantumult X 配置文件（去广告 + AIGC/Gemini + 节点位置显示 + DNS 深度优化与路由器内网防劫持）。

## 配置文件与客户端支持

- **Quantumult X 配置**：
  - **[QuantumultX_Custom.conf](./QuantumultX_Custom.conf)**：定制综合终极配置文件
- **Loon 配置（新）**：
  - **[loon/ 目录](./loon/)**：Loon 专属配置中心
  - **[loon/Kelee_Custom.conf](./loon/Kelee_Custom.conf)**：Loon 定制终极配置文件（可莉基底+QX全同构）
  - **[loon/README.md](./loon/README.md)**：Loon 导入指引与推荐资源
- **Surge 5 配置（新）**：
  - **[surge/ 目录](./surge/)**：Surge 5 专属配置中心
  - **[surge/Surge_Custom.conf](./surge/Surge_Custom.conf)**：Surge 5 定制终极配置文件
  - **[surge/README.md](./surge/README.md)**：Surge 导入指引与架构说明

---

## 导入链接

### 1. GitHub Raw 原生直链
```
https://raw.githubusercontent.com/Today-ddr/qx/main/QuantumultX_Custom.conf
```

### 2. jsDelivr CDN 加速链接（国内直连推荐，免代理极速下载）
```
https://cdn.jsdelivr.net/gh/Today-ddr/qx@main/QuantumultX_Custom.conf
```

---

## 导入与使用说明

1. 打开 **Quantumult X** 客户端。
2. 进入底部右下角 **风车图标（设置）**。
3. 找到 **「配置文件」** -> 点击 **「下载」**。
4. 粘贴上方任一链接，点击右上角 **「确定」** 下载并替换配置。
5. **MitM 证书提示**：
   - 若此前已生成并信任根证书，请将旧配置底部 `[mitm]` 下的 `passphrase` 和 `p12` 内容保留或复制粘贴到新配置文件中，避免重新安装和信任证书。
