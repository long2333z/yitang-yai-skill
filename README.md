# 一堂 / YAI CLI Skill

面向一堂/YAI/whyai 的 Codex 路由 Skill：按任务选择独立 SOP。

## 能解决什么

| 你想做的事 | 从哪里开始 | 最终得到什么 |
| --- | --- | --- |
| 检查安装、版本、登录、Gateway 或权益 | [SOP-00 准入](sops/access.md) | 已验证的可用状态，或可复现的阻断点 |
| 查课程、概念、作业或既有笔记 | [学习与知识](sops/learning.md) | 有真实 ID、查询范围与来源的结果 |
| 选择官方 Partner、做多 Partner 接力或设计自建 Partner | [Partner 工作](sops/partner.md) | 明确的角色、任务契约、交接包或可验证设计 |
| 用 Partner 完成真实任务、上传材料、保存可复用结论 | [任务执行与资产](sops/execution.md) | 结果、来源、限制、下一步与可定位资产 |
| 续聊、改写、分支、导出、分享、删除或排错 | [对话与故障](sops/conversation.md) | 边界清楚且可回查的会话处理结果 |

## 资料与事实边界

本仓库只引用三份官方资料：

- [一堂 CLI 使用指南](https://yitanger.feishu.cn/wiki/XoFcwMmotigm7Ikv4RQc9TfQn0g)
- [YAI 使用指南](https://yitanger.feishu.cn/wiki/WPJWwKwI3iUCzqkGUzvc6i5MnNg)
- [YAI 一堂第一课](https://yitang.top/fs-doc/217da0c5f7d334b601c53526ed06f90d/MZFMd7mYPofbJ2xQhdEcS3Xrnvd)

它们的 [本地结构化语义快照](references/official-sources.md) 用于离线分析与 SOP 设计，并非逐字全文导出。当前命令参数、Gateway、权限、账号状态与真实结果必须以本次 `--help`、CLI 返回和官方实时页面为准。若三者冲突，优先运行时事实，并记录差异后再修订 SOP。

## 仓库结构

```text
SKILL.md                         # 只做任务路由与共享护栏
agents/openai.yaml               # Codex 展示信息
sops/                            # 按任务独立加载的执行 SOP
references/core-sop-map.md       # 来源证据到核心任务链的映射
references/official-sources.md   # 三份官方来源和本地快照入口
references/snapshots/            # 带章节锚点的结构化语义快照
skill-optimizer-records/         # 维护/优化记录，不参与运行时加载
```
