# SOP-02 Partner 选择与调用

适用：选择官方 Partner 并完成一次具体任务。

## 操作

1. 先写清背景、目标、约束和期望产出；不要只按 Partner 名称盲选。
2. `whyai --json partners search "关键词" --scope official` 找候选。
3. 用实际返回的完整名称执行 `whyai --json partners resolve "完整名称"`；重名时使用真实 `PARTNER_ID`。
4. 必要时 `whyai --json partners get PARTNER_ID`，核对角色、描述和适用边界。
5. `whyai chat --help` 核对当前对话参数，再以真实 `PARTNER_ID` 发起新对话：`whyai --json chat "任务说明" --partner PARTNER_ID`。
6. 只有用户明确要求时才加 `--knowledge-base`、`--web-search`、`--file` 或 `--no-memory`；文件上传前确认文件和用途。
7. 保存返回的 `conversation_id`，将回答中的事实、假设、待确认项和下一步分开。

## 追问规则

第一轮没有达到“可用”，优先在同一会话中提出一个聚焦追问；需要换 Partner 时新建会话，并重新传入必要的前序材料，不把已有 `--conversation` 与另一个 `--partner` 混用来切换角色。

## 完成标准

真实 Partner 已确认，任务回答已返回，`conversation_id` 已保留，并明确说明是否产生会话记录、额度消耗或文件上传。
