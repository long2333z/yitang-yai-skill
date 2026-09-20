# SOP-06 作业复盘

适用：查找一堂作业、读取答案、复盘训练结果并沉淀行动。

## 操作

1. 优先按主题查找：`whyai yitang homework search "关键词"`；需要浏览时使用 `whyai yitang homework list`。
2. 注意 `homework list` 可能直接返回答案正文和分页信息；只保留匹配任务所需的条目，不把整页答案带入后续上下文。
3. 从返回结果取得真实 `ANSWER_ID`，再使用 `whyai yitang homework show ANSWER_ID` 读取选定答案的完整详情。
3. 复盘时区分题目要求、本人原答案、方法依据、缺口、可执行改进和下一次练习；不要只做摘要。
4. 需要保存复盘时转到 [笔记与资产沉淀](05-notes-assets.md)。
5. 用户提到 Candy 但当前 CLI 没有固定命令时，明确报告 CLI 能力缺口；不要猜测接口，必要时按 [课程与知识检索](01-course-knowledge.md) 做能力发现。

## 完成标准

返回真实作业/答案标识和复盘结果；未找到、无权限、未登录和 CLI 未暴露能力分别说明。
