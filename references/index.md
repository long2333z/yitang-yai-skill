# 运行资料索引

这份索引只列出运行 Skill 时可能需要的资料。先按任务打开一份 SOP；只有遇到相应问题时，再继续读它链接的资料。不要把 `docs/` 当作运行说明。

## 第一层：通用准入

| 什么时候读 | 读取 |
| --- | --- |
| 本次还未验证 CLI，或要检查版本、登录、Gateway、权益、命令错误 | [环境准入](sops/access.md) |

## 第二层：核心场景

核心场景负责把一项完整任务按阶段编排；先选一个场景，再只打开其中当前阶段的原子 SOP。

| 完整任务 | 读取 | 最终得到 |
| --- | --- | --- |
| 从课程中提炼方法，再用于一个真实问题 | [课程到工作](sops/scenarios/course-to-work.md) | 有边界的实践结果 |
| 使用一个或多个 Partner 完成一项交付 | [Partner 协作交付](sops/scenarios/partner-delivery.md) | 可追溯的交付与交接 |
| 将反复验证的做法封装为长期 Partner 或工作流 | [稳定流程封装](sops/scenarios/workflow-productization.md) | 经过私有验证的封装 |

## 第三层：原子 SOP

只需要完成场景中的一个阶段，或任务还不构成完整场景时，从这里进入。

| 任务 | 先读 | 需要时再读 |
| --- | --- | --- |
| 从课程中提炼方法 | [课程研究](sops/course-research.md) | [官方资料](official-sources.md) |
| 用课程方法解决真实小任务 | [课程应用](sops/course-application.md) | [任务执行](sops/execution.md) |
| 只查询课程、章节、作业或笔记 | [课程查询](sops/course-lookup.md) | [官方资料](official-sources.md) |
| 还不确定课程任务属于研究、应用还是查询 | [课程与知识路由](sops/learning.md) | [官方资料](official-sources.md) |
| 选择、接力或自建 Partner | [Partner 工作](sops/partner.md) | [官方资料](official-sources.md) |
| 带材料完成任务并保存结果 | [任务执行与资产](sops/execution.md) | [官方资料](official-sources.md) |
| 继续、分支、导出、分享、删除或排错 | [对话与故障](sops/conversation.md) | [官方资料](official-sources.md) |

## 理解整体时再读

| 资料 | 用途 |
| --- | --- |
| [任务地图](core-sop-map.md) | 看课程、Partner、任务、资产之间如何衔接。 |
| [官方资料](official-sources.md) | 找到三份官方资料和对应的本地整理。 |

资料里的命令、账号、Gateway、权限和对象 ID 都以本次 CLI 返回和官方实时页面为准。
