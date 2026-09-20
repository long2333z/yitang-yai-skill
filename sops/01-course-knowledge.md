# SOP-01 课程与知识检索

适用：找课程、读课程章节、按分类浏览一堂知识，或判断某个方法是否存在。

## 操作

1. 先明确要解决的问题和需要的产出；若只是想完成一件事，优先转到 [单任务闭环](03-task-loop.md)，不要无目的浏览。
2. 关键词检索：`whyai yitang course search "关键词"`。
3. 分类浏览：`whyai yitang course catalog`，再用返回的真实 `NAV_NO` 执行 `whyai yitang course list --nav NAV_NO`。
4. 注意搜索结果可能同时返回课程候选和 lesson 候选：课程使用返回的课程 `id`，具体课节使用返回的 `lessonId`/章节 ID，不要把两类 ID 混用。
5. 选定真实 `COURSE_ID` 后，依次执行 `whyai yitang course info COURSE_ID`、`whyai yitang course sections COURSE_ID`。
6. 只读取需要的章节：`whyai yitang course section SECTION_ID`。
7. 课程命令不能覆盖任务所需能力时，执行 `whyai yitang capabilities --domain course --risk read --source yitang-fe`，再用 `describe` 核对能力契约；低层 `call` 只在用户明确需要且参数来自实际描述时使用。

## 判断与交付

- 返回课程/lesson/章节的真实名称、对应 ID、与当前任务的关系和正文中可直接使用的要点；保留服务返回的 `profile`、`capability`、`risk`、`source` 等证据字段。
- 区分“没有匹配”“内容不可读”“当前账号无权限”和“命令不支持”。
- 课程/知识检索是准备材料，不等于 Partner 已调用，也不等于业务结论已验证。

## 完成标准

已定位可用课程或明确报告缺口；如果继续进入 Partner 或单任务处理，传递真实课程/章节 ID和最小必要上下文。
