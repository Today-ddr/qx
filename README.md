# Quantumult X 配置文件集合

自用 Quantumult X 配置文件存储库。

## 文件列表

- **[QuantumultX_Custom.conf](./QuantumultX_Custom.conf)**：定制综合终极配置（去广告 + AIGC/Gemini + 节点位置显示 + DNS 深度优化与路由器内网防劫持）
- **[QuantumultX.conf](./QuantumultX.conf)**：墨鱼原版配置（来源：`ddgksf2013`）
- **[qx.conf](./qx.conf)**：纯净分流与多区域测速配置（来源：`yfamilys`）
- **[QuanX.conf](./QuanX.conf)**：Boringahhh 改良版配置

---

## 导入链接（QuantumultX_Custom.conf）

### GitHub Raw 原始链接
```
https://raw.githubusercontent.com/Today-ddr/qx/main/QuantumultX_Custom.conf
```

### jsDelivr CDN 加速链接（国内直连快速拉取）
```
https://cdn.jsdelivr.net/gh/Today-ddr/qx@main/QuantumultX_Custom.conf
```

---

## 导入与使用说明

1. 打开 **Quantumult X** 客户端。
2. 进入底部右下角 **风车图标（设置）**。
3. 找到 **「配置文件」** -> 点击 **「下载」**。
4. 粘贴上方任一链接，点击确定下载并替换配置。
5. **MitM 证书提示**：
   - 若此前已生成并信任根证书，请将旧配置底部 `[mitm]` 下的 `passphrase` 和 `p12` 内容保留或复制粘贴到新配置文件中，避免重新安装和信任证书。
