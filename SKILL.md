---
name: yitang-yai-skill
description: "当用户希望把一堂 YAI 的课程方法、Partner 协作和个人知识资产用于真实工作时使用。先按任务挖课程和方法，再通过 whyai CLI 读取或调用一堂服务，完成小范围验证、复盘与沉淀。"
---

# 一堂 YAI Skill

先判断要完成什么，再打开一份对应的 SOP。详细命令、示例和官方资料都留在各自页面，不在这里重复。

## 路由表

| 你要做什么 | 先读这里 |
|---|---|
| 检查 CLI、Gateway、登录、套餐资格 | [环境准入](references/sops/access.md) |
| 从课程中找到方法，并用于一个真实问题 | [课程到工作](references/sops/scenarios/course-to-work.md) |
| 用一个或多个 Partner 把材料做成结果 | [Partner 协作交付](references/sops/scenarios/partner-delivery.md) |
| 把已经验证的重复做法封装为 Partner 或工作流 | [稳定流程封装](references/sops/scenarios/workflow-productization.md) |
| 只查询课程、提炼方法或做一次小验证 | [课程单步路由](references/sops/learning.md) |
| 只需用已选 Partner 完成一次工作，或保存结果/笔记 | [任务执行与资产](references/sops/execution.md) |
| 回看、继续、导出对话，或处理命令异常 | [对话与故障](references/sops/conversation.md) |

## 所有任务都遵守

1. 先走 [环境准入](references/sops/access.md)，再做真实 CLI 调用；浏览器授权完成不代表 CLI 已可用。
2. 课程、作业、笔记、Partner 和会话的 ID 都从本次返回中取得，不靠猜测。
3. 上传、创建、分享、删除或发布前，先说清对象和影响，取得用户同意。
4. 交付时说清三件事：已经确认的事实、自己的判断、还需要确认的内容。

想了解为什么这样做，再看 [任务地图](references/core-sop-map.md) 或 [官方资料](references/official-sources.md)。

读取课程时遇到 ID 不匹配或内容为空，先看当前 CLI 帮助，确认对象类型和对应的只读能力。

需要按主题查找全部运行资料时，读 [运行资料索引](references/index.md)。`docs/` 只用于维护和迭代，不参与运行。
