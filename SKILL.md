---
name: yitang-cli
description: "路由一堂/YAI 的 whyai CLI 任务；用户提到一堂、YAI、whyai、课程、Partner、作业、笔记或希望按固定 SOP 完成一项工作时使用。"
---

# 一堂 CLI 路由 Skill

本入口只做意图识别、准入检查和 SOP 路由。不要在这里展开课程、Partner 或笔记的完整操作；按下表只读取一个匹配的独立 SOP。

## 路由表

| 用户意图 | 读取的 SOP |
|---|---|
| 检查 CLI、Gateway、登录、套餐资格 | [环境准入](sops/00-access.md) |
| 找课程、读课程章节、查一堂知识 | [课程与知识检索](sops/01-course-knowledge.md) |
| 找官方 Partner 并完成一次任务 | [Partner 选择与调用](sops/02-partner.md) |
| 有一个真实问题，希望从背景走到可用结果 | [单任务闭环](sops/03-task-loop.md) |
| 需要多个 Partner 分工、接力或汇总 | [多 Partner 接力](sops/04-multi-partner.md) |
| 保存、读取、下载或整理笔记/成果 | [笔记与资产沉淀](sops/05-notes-assets.md) |
| 查作业、读答案、复盘训练结果 | [作业复盘](sops/06-homework-review.md) |
| 创建、调试、优化或发布自己的 Partner | [自有 Partner 封装](sops/07-partner-builder.md) |
| 回看、继续、导出、命名或分支对话 | [对话管理](sops/08-conversation.md) |
| 命令失败、结果为空、权限或环境异常 | [故障收敛](sops/09-troubleshooting.md) |

## 共享准入

1. 先运行 `whyai --version`；需要确认当前入口时运行最小的 `whyai --help`、`whyai yitang help` 或 `whyai chat --help`。
2. 需要业务调用时运行 `whyai --json status`，确认 `gateway=https://ai.yitang.top`、`environment=prod` 和登录状态。
3. 只有用户明确要求登录/认证时，才运行 `whyai login --gateway https://ai.yitang.top`；浏览器授权由用户完成。
4. 命令帮助和实际返回是当前版本的执行事实；官方资料只用于解释产品意图、场景和背景。资料入口见 [官方资料引用](references/official-sources.md)。

## 共享边界

- 先取真实 ID，再执行下一步；不猜课程、Partner、笔记、作业或会话 ID。
- `chat`、文件上传、笔记创建、Partner 创建/发布、删除和其他会产生远端记录或额度消耗的操作，只有在用户明确要求后执行。
- 复杂任务优先拆成“背景与目标 → 选择入口/Partner → 完成一件事 → 追问修正 → 结果验收 → 资产沉淀”。
- 不把“命令成功”“登录成功”“得到回答”直接表述成业务结果已验证；交付时说明实际执行、返回、未完成项和权限/额度影响。

## 使用原则

本 Skill 是模型可自动调用的路由入口。正常场景只加载一个匹配 SOP；只有跨 SOP 的任务才按顺序加载多个，并保留每个阶段的真实返回和完成标准。
