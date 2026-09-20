# 一堂 YAI Skill

用 `whyai` 连接一堂 YAI，把课程方法、Partner 协作和对话结果用在真实工作里。CLI 是入口，不是终点：先学会方法，再做成结果，最后留下能复用的资产。

## 从哪里开始

| 想做的事 | 打开哪一页 |
| --- | --- |
| 检查版本、登录、Gateway 或权益 | [先确认能不能用](references/sops/access.md) |
| 从课程里找到方法，再用到一个真实问题 | [课程到工作](references/sops/scenarios/course-to-work.md) |
| 用一个或多个 Partner 完成一项交付 | [Partner 协作交付](references/sops/scenarios/partner-delivery.md) |
| 把稳定的重复做法封装为 Partner 或工作流 | [稳定流程封装](references/sops/scenarios/workflow-productization.md) |
| 只需查课程、提炼方法或做一次小验证 | [课程单步路由](references/sops/learning.md) |
| 只需带着材料完成一次工作，并保存结果 | [任务执行与资产](references/sops/execution.md) |
| 继续、分支、导出、分享或清理对话 | [对话与故障](references/sops/conversation.md) |

## 三份官方资料

本仓库只引用三份官方资料：

- [一堂 CLI 使用指南](https://yitanger.feishu.cn/wiki/XoFcwMmotigm7Ikv4RQc9TfQn0g)
- [YAI 使用指南](https://yitanger.feishu.cn/wiki/WPJWwKwI3iUCzqkGUzvc6i5MnNg)
- [YAI 一堂第一课](https://yitang.top/fs-doc/217da0c5f7d334b601c53526ed06f90d/MZFMd7mYPofbJ2xQhdEcS3Xrnvd)

运行时通过[官方资料](references/official-sources.md)访问这三份来源。维护期的阅读整理放在 [docs/snapshots](docs/snapshots/)；实际操作时，以当前 `--help`、CLI 返回和官方页面为准。

所有运行资料都列在 [运行资料索引](references/index.md)；维护这项 Skill 时再看 [docs](docs/README.md)。

## 目录说明

```text
SKILL.md                         # 给 Codex 的任务入口
references/                      # 官方资料和任务地图
references/sops/                 # 原子 SOP 与核心场景编排
references/sops/scenarios/       # 跨多个阶段的核心场景
docs/                            # 设计、方案、架构和迭代记录，不参与运行
```
