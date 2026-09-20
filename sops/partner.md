# 一堂 CLI Partner 工作 SOP

## SOP-20 Partner 选择与调用

适用：选择官方 Partner 并完成一次具体任务。

1. 先写清背景、目标、约束和期望产出；不要只按 Partner 名称盲选。
2. 用当前帮助确认搜索入口，再执行 `whyai --json partners search "关键词" --scope official`。
3. 用实际返回的完整名称执行 `whyai --json partners resolve "完整名称"`；重名时使用真实 `PARTNER_ID`。
4. 必要时 `whyai --json partners get PARTNER_ID`，核对角色、描述和适用边界。
5. `whyai chat --help` 核对参数，再以真实 `PARTNER_ID` 发起新对话：`whyai --json chat "任务说明" --partner PARTNER_ID`。
6. 只有用户明确要求时才加 `--knowledge-base`、`--web-search`、`--file` 或 `--no-memory`；文件上传前确认文件和用途。
7. 保存返回的 `conversation_id`，将回答中的事实、假设、待确认项和下一步分开。

第一轮没有达到“可用”时，在同一会话中提出一个聚焦追问；需要换 Partner 时新建会话，不用另一个 `--partner` 试图切换旧会话角色。

完成标准：真实 Partner 已确认，任务回答已返回，`conversation_id` 已保留，并明确说明远端会话、额度消耗或文件上传。

## SOP-21 多 Partner 接力

适用：一个任务需要研究、方案、审查、改写等不同角色协作。

1. 把总任务拆成有顺序的子任务，每个子任务只指定一个角色和一个交付物。
2. 分别建立独立会话；不在旧会话上追加另一个 Partner 切换角色。
3. 每轮只传递上一轮的必要结果、依据和未决问题，不重复上传无关历史。
4. 最后一轮指定汇总角色，输入前序产出并要求统一口径、指出冲突和列出待确认项。
5. 用 [任务执行与资产](execution.md#sop-30-单任务闭环) 验收最终产出；需要长期复用时保存为笔记。

完成标准：每个子任务都有 Partner、会话 ID、产出和输入边界；汇总结果能追溯到各轮。

## SOP-22 自有 Partner 封装

适用：创建、准备、调试、优化或发布一位自己的 Partner。

这是远端写入流程，必须由用户明确提出；普通任务只使用官方 Partner。

1. 定义服务对象、问题边界、输入、输出、专业知识来源和固定工作流。
2. 运行 `whyai partners --help`、`whyai partners temporary --help`、`whyai partners create --help`，确认当前草稿入口。
3. 先建立/更新草稿，补齐提示词、知识和工作流程，再用最小任务调试；不直接发布未经验证的角色。
4. 需要优化提示词时先阅读 `whyai partners optimize-prompt --help`，保留修改前后目标和验证样例。
5. 只有用户明确要求发布时才执行当前帮助对应的发布动作；发布前报告名称、范围、草稿状态和外部影响。

完成标准：草稿、调试样例和发布状态可核对；只完成草稿或调试时，不表述为已发布或已生效。
