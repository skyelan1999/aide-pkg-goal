# Goal · Aide 目标能力预设

Aide 的 `goal` 插件独立分发仓库，版本 **1.0.0**。MIT 许可证。

本版本保持原有预设内容不变，来自
[`skyelan1999/aide` 的 `f795a240`](https://github.com/skyelan1999/aide/tree/f795a240cdb37e9b92a37d91664bd1bb3053b809/plugins/goal)。

## 当前能力与边界

插件向 Aide 注册 `goal` 服务名、`goal-panel` 面板槽位，以及以下工具声明：

| 工具 | 声明用途 | 当前状态 |
| --- | --- | --- |
| `goal-create` | 创建并跟踪长程目标 | 仅声明，未提供 handler |
| `goal-status` | 查询目标阶段状态 | 仅声明，未提供 handler |

本插件没有独立的目标存储、创建或状态查询实现。Aide v1 插件宿主收集这些声明，但不渲染通用 UI 槽位；安装此包不会新增可执行的目标管理工具或独立面板。

## 安装

需要支持插件导入的 Aide，市场兼容基线为 `0.1.17.0 RC2`，以及宿主 Node.js 插件运行环境。没有 npm 依赖。

从 [Release](https://github.com/skyelan1999/aide-pkg-goal/releases/tag/v1.0.0) 下载 `aide-pkg-goal-v1.0.0.zip` 和 `SHA256SUMS`，核对摘要后，在 Aide 插件管理中上传 ZIP。也可在[官方插件市场](https://skyelan1999.github.io/aide-pkg-shop/)搜索 `goal`。

```sh
sha256sum -c SHA256SUMS
```

已有同 ID、同版本插件时无需重复导入。独立发布没有改变原包版本或运行行为，也不会给已安装的 1.0.0 强制提供升级。

## 包内容与验证

安装 ZIP 根目录包含 `manifest.json`、`index.js`、`LICENSE`，与市场已有 1.0.0 安装包逐字节一致。发布附带的 SHA-256 用于完整性校验，不是发布者签名。

开发时可以运行 `node --check index.js`；发布时还应使用 Aide 的 `internal/server/plugin_host.js` 执行独立入口校验和 surface 加载，确认两个工具仍标记为不可执行。不得把成功加载写成目标管理功能验收通过。

## 权限

此预设自身不读取项目文件、不执行命令、不连接网络。Node 插件运行于可信宿主环境，不能把宿主插件机制视为权限沙箱。不要将密钥或用户设置打包进仓库或安装 ZIP。
