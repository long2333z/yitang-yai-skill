# SOP-08 对话管理

适用：回看、继续、导出、命名、收藏、分支或删除对话。

## 操作

1. 定位会话：`whyai --json conversations list --page 1 --page-size 20`。
2. 查看会话：`whyai conversations get CONVERSATION_ID`；查看消息：`whyai --json messages list CONVERSATION_ID --all`。
3. 继续原会话时保留真实 ID，并按 `whyai chat --help` 当前参数使用 `--conversation CONVERSATION_ID`。
4. 导出时使用 `whyai conversations export CONVERSATION_ID --format md --output 本地文件路径`。
5. 需要整理时，再使用 `whyai conversations rename`、`star`、`branch` 等帮助中确认过的命令。
6. 删除前必须核对会话 ID、标题和删除范围；用户没有明确要求时只读，不执行 `delete`。

## 完成标准

目标会话、操作类型和返回结果清晰可追溯；导出文件路径或新分支 ID 已记录，删除动作有明确授权。
