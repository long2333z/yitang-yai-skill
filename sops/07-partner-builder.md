# SOP-07 自有 Partner 封装

适用：创建、准备、调试、优化或发布一位自己的 Partner。

这是远端写入流程，必须由用户明确提出；普通任务只使用官方 Partner。

## 操作

1. 先定义 Partner 的服务对象、问题边界、输入、输出、专业知识来源和固定工作流。
2. 运行 `whyai partners --help`、`whyai partners temporary --help`、`whyai partners create --help`，确认当前版本的草稿入口。
3. 先建立/更新草稿，补齐提示词、知识和工作流程，再用实际任务做最小调试；不直接发布未经验证的角色。
4. 需要优化提示词时先阅读 `whyai partners optimize-prompt --help`，保留修改前后目标和验证样例。
5. 只有用户明确要求发布时才执行 `whyai partners publish --help` 对应的发布动作；发布前报告名称、范围、版本/草稿状态和不可逆影响。

## 完成标准

草稿、调试样例和发布状态可核对；如果只完成草稿或调试，不表述为已发布或已生效。
