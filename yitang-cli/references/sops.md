# 一堂 CLI 固定任务 SOP

这些 SOP 只保留执行顺序、决策点和完成标准。命令参数的完整说明以当前 CLI 的 `--help` 为准。

## SOP-00 环境准入

适用：任何需要实际调用一堂服务的任务。

1. 运行 `whyai --version`，确认命令可发现。
2. 根据任务运行 `whyai --help`、`whyai yitang help` 或 `whyai chat --help`，确认当前版本支持入口。
3. 运行 `whyai --json status`。
4. 核对 `gateway=https://ai.yitang.top`、`environment=prod` 和登录状态。
5. 未登录时，仅在用户明确要求登录后运行 `whyai login --gateway https://ai.yitang.top`，把授权交给用户完成。

完成标准：环境和登录状态有实际命令返回；缺少登录、权限或套餐时停止后续业务查询并说明原因。

## SOP-01 课程检索与阅读

适用：找课程、按分类浏览、阅读课程内容。

1. 用 `whyai yitang course search "关键词"` 按标题或标签定位候选。
2. 需要分类导航时，先运行 `whyai yitang course catalog`，再用返回的真实 `NAV_NO` 执行 `whyai yitang course list --nav NAV_NO`。
3. 从实际结果选定课程后，依次运行 `whyai yitang course info COURSE_ID` 和 `whyai yitang course sections COURSE_ID`。
4. 只读取任务需要的章节：`whyai yitang course section SECTION_ID`。

完成标准：返回课程、章节的真实名称和 ID，并区分可读取正文、无结果和权限不足。

## SOP-02 作业检索与阅读

适用：查找自己的作业、定位答案、读取答案详情。

1. 直接浏览使用 `whyai yitang homework list`；按主题定位使用 `whyai yitang homework search "关键词"`。
2. 从返回结果取得真实 `ANSWER_ID`。
3. 使用 `whyai yitang homework show ANSWER_ID` 读取选定答案。
4. 需要更多范围时，再按当前帮助支持的分页或时间参数扩大查询，不默认拉取全部历史。

完成标准：给出匹配作业和答案的实际内容或 ID；没有匹配时明确报告未找到，不改写为“没有权限”。

## SOP-03 笔记检索与阅读

适用：查找 YAI 笔记、读取指定笔记。

1. 运行 `whyai --json notes list`，必要时按实际支持的文件夹参数缩小范围。
2. 从列表中筛选目标笔记，取得真实 `NOTE_ID`。
3. 运行 `whyai --json notes get NOTE_ID` 读取正文。
4. 仅在用户明确要求保存成果时，使用 `whyai notes create --title "标题" --content @本地文件路径` 创建笔记。

完成标准：返回目标笔记的标题、ID 和所需正文；创建笔记时报告已创建的远端动作。

## SOP-04 官方 Partner 调用

适用：找 Partner、确认角色、发起一次新对话。

1. 运行 `whyai --json partners search "关键词" --scope official` 找候选。
2. 用返回的完整名称执行 `whyai --json partners resolve "完整名称"`；重名时使用实际返回的 `PARTNER_ID`。
3. 必要时运行 `whyai --json partners get PARTNER_ID` 核对角色和描述。
4. 运行 `whyai chat --help` 核对当前对话参数，再使用实际 `PARTNER_ID` 发起新对话。
5. 用户没有明确要求联网、记忆、上传文件或其他选项时，不额外开启；本地文件仅在用户明确指定文件和用途时通过 `--file` 上传。

完成标准：确认实际使用的 Partner；对话返回 `conversation_id` 或明确的服务端错误，并说明是否产生了远端会话和额度消耗。

## SOP-05 对话回看与成果沉淀

适用：回看历史会话、继续对话、导出内容或保存本地成果。

1. 运行 `whyai --json conversations list --page 1 --page-size 20` 定位目标会话。
2. 用真实 `CONVERSATION_ID` 执行 `whyai --json messages list CONVERSATION_ID --all` 回看消息。
3. 需要导出时执行 `whyai conversations export CONVERSATION_ID --format md --output 本地文件路径`。
4. 需要继续原会话时，保留实际 `conversation_id`，并按 `whyai chat --help` 当前参数传入；切换 Partner 时新建会话并重新提供必要材料。
5. 需要保存到一堂笔记时，仅在用户明确要求后执行笔记创建命令，并在执行前确认标题和本地内容来源。

完成标准：会话 ID、回看/导出结果和后续动作清晰可追溯；没有目标会话时停止并报告未找到。

## SOP-06 故障收敛

适用：命令失败、登录后仍不可用或查询结果异常。

1. 保留失败命令和原始错误。
2. 重新运行最小相关帮助命令，确认命令和参数不是当前版本不支持。
3. 运行 `whyai --json status`，核对登录状态、Gateway 和 environment。
4. 需要服务权限时，再查询与任务直接相关的权限/套餐信息；不把权限失败当成空结果。
5. 修正一个明确原因后最多重试一次；仍失败则交付诊断信息和下一步，不循环重试。

完成标准：要么得到目标结果，要么明确归类为命令、认证、环境、权限、参数/ID 或服务端故障，并保留证据。
