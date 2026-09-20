# 一堂 CLI 对话与故障 SOP

## SOP-40 对话管理

适用：回看、继续、导出、命名、收藏、分支或删除对话。

1. 定位会话：`whyai --json conversations list --page 1 --page-size 20`。
2. 查看会话：`whyai conversations get CONVERSATION_ID`；查看消息：`whyai --json messages list CONVERSATION_ID --all`。
3. 继续原会话时保留真实 ID，并按 `whyai chat --help` 当前参数使用 `--conversation CONVERSATION_ID`。
4. 导出时使用 `whyai conversations export CONVERSATION_ID --format md --output 本地文件路径`。
5. 需要整理时，再使用 `whyai conversations rename`、`star`、`branch` 等帮助中确认过的命令。
6. 删除前必须核对会话 ID、标题和删除范围；用户没有明确要求时只读，不执行 `delete`。

完成标准：目标会话、操作类型和返回结果清晰可追溯；导出文件路径或新分支 ID 已记录，删除动作有明确授权。

## SOP-41 故障收敛

适用：命令找不到、登录异常、Gateway 不符、查询为空、权限不足或参数不支持。

1. 保留失败命令和原始错误，不先改写成结论。
2. 按顺序检查：`whyai --version` → 相关 `--help` → `whyai --json status` → Gateway/environment → 资格/权限 → 参数和真实 ID。
3. 空结果与无权限分开判断；必要时用 `whyai --json billing access` 或对应资源的帮助/状态命令补证据。
4. 修正一个明确原因后最多重试一次；仍失败则交付诊断信息和下一步。
5. 页面资料与 CLI 行为冲突时，优先保留 CLI 原始输出，并引用 [官方资料](../references/official-sources.md) 说明背景差异。

完成标准：要么得到目标结果，要么将问题归类为命令、认证、环境、权限、参数/ID、服务端或资料差异，并保留证据；不循环重试。
