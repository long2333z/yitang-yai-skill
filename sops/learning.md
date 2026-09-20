# 一堂 CLI 学习与知识 SOP

## SOP-10 课程与知识检索

适用：找课程、读课程章节、按分类浏览一堂知识，或判断某个方法是否存在。

1. 先明确要解决的问题和需要的产出；若只是想完成一件事，转到 [任务执行与资产](execution.md)，不要无目的浏览。
2. 关键词检索：`whyai yitang course search "关键词"`。
3. 分类浏览：`whyai yitang course catalog`，再用返回的真实 `NAV_NO` 执行 `whyai yitang course list --nav NAV_NO`。
4. 注意搜索结果可能同时返回课程候选和 lesson 候选：课程使用返回的课程 `id`，具体课节使用返回的 `lessonId`/章节 ID，不要把两类 ID 混用。
5. 选定真实 `COURSE_ID` 后，依次执行 `whyai yitang course info COURSE_ID`、`whyai yitang course sections COURSE_ID`。
6. 只读取需要的章节：`whyai yitang course section SECTION_ID`。
7. 课程命令不能覆盖任务所需能力时，转到 [访问与环境](access.md#sop-01-能力发现)。

完成标准：返回课程/lesson/章节的真实名称、对应 ID、与当前任务的关系和可直接使用的要点；保留服务返回的 `profile`、`capability`、`risk`、`source` 等证据字段。

## SOP-11 作业复盘

适用：查找一堂作业、读取答案、复盘训练结果并沉淀行动。

1. 优先按主题查找：`whyai yitang homework search "关键词"`；需要浏览时使用 `whyai yitang homework list`。
2. 注意 `homework list` 可能直接返回答案正文和分页信息；只保留匹配任务所需的条目，不把整页答案带入后续上下文。
3. 从返回结果取得真实 `ANSWER_ID`，再使用 `whyai yitang homework show ANSWER_ID` 读取选定答案的完整详情。
4. 复盘时区分题目要求、本人原答案、方法依据、缺口、可执行改进和下一次练习；不要只做摘要。
5. 需要保存复盘时转到 [任务执行与资产](execution.md#sop-31-笔记与资产沉淀)。
6. 用户提到 Candy 但当前 CLI 没有固定命令时，明确报告 CLI 能力缺口，不猜测接口。

完成标准：返回真实作业/答案标识和复盘结果；未找到、无权限、未登录和 CLI 未暴露能力分别说明。
