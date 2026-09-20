# 官方资料索引与证据使用规则

本 Skill 的产品与 CLI 规则只引用下列三份官方资料。对应本地文件是**浏览器渲染后的结构化语义快照**，用于离线分析和 SOP 路由，并非逐字全文导出；命令参数、平台状态、权限和界面行为以实时官方页面、`--help` 与本次运行结果为准。

| 来源 | 适用事实 | 本地语义快照 |
| --- | --- | --- |
| [一堂 CLI 使用指南](https://yitanger.feishu.cn/wiki/XoFcwMmotigm7Ikv4RQc9TfQn0g) | 正式 Gateway、CLI 登录/状态/权益、课程/作业/笔记/Partner/会话命令与故障分流 | [cli-guide-2026-09-20.md](snapshots/cli-guide-2026-09-20.md) |
| [YAI 使用指南](https://yitanger.feishu.cn/wiki/WPJWwKwI3iUCzqkGUzvc6i5MnNg) | 知识检索、先训再聊、T/C/P/R Partner、输入、迭代、资产、会话与笔记 | [yai-guide-2026-09-20.md](snapshots/yai-guide-2026-09-20.md) |
| [YAI 一堂第一课](https://yitang.top/fs-doc/217da0c5f7d334b601c53526ed06f90d/MZFMd7mYPofbJ2xQhdEcS3Xrnvd) | 可调用知识、复杂协作、人审节点、CLI 工作流和稳定流程封装边界 | [yai-first-class-2026-09-20.md](snapshots/yai-first-class-2026-09-20.md) |

阅读顺序：先读 [核心 SOP 证据地图](core-sop-map.md) 选择任务链，再只加载目标 SOP 和它指向的快照锚点。

## 证据优先级

1. **本次 CLI 返回、`--help`、错误原文**：当前命令与账号事实。
2. **官方实时页面**：当前产品规则与正式环境说明。
3. **本地语义快照**：离线分析、路由与历史证据锚点。
4. **Skill 的 SOP**：将已提取规则变成执行次序；不能覆盖上面三层事实。

若快照、实时帮助和运行结果冲突，停止沿用旧命令，记录差异，并以当前帮助/官方页面重新校准 SOP。
