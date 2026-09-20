# 一堂 CLI 访问与环境 SOP

## SOP-00 环境准入

适用：任何需要实际调用一堂服务的任务。

1. `whyai --version`：确认命令可发现。
2. 按任务运行一个最小帮助命令：`whyai --help`、`whyai yitang help` 或 `whyai chat --help`。
3. `whyai --json status`：核对 Gateway、环境和登录状态。
4. 未登录时，只有用户明确要求登录才运行 `whyai login --gateway https://ai.yitang.top`，把浏览器授权交给用户。
5. 任务涉及额度或 CLI 资格时，再运行 `whyai --json billing access`；不要用普通账号登录成功推断 CLI 有资格。

完成标准：环境和登录状态有实际返回；Gateway 为 `https://ai.yitang.top`、环境为 `prod`。缺少登录、权限或套餐资格时停止业务 SOP，并交付具体原因。

## SOP-01 能力发现

适用：固定业务命令不足以覆盖任务，需要确认当前 YAI CLI 暴露的能力。

1. 先阅读对应的 `whyai ... --help`。
2. 只读能力发现使用 `whyai yitang capabilities --domain course --risk read --source yitang-fe` 或当前帮助支持的筛选条件。
3. 用实际返回的 capability ID 执行 `whyai yitang describe CAPABILITY_ID`。
4. 只有用户明确要求调用、且参数来自实际描述时，才执行 `whyai yitang call CAPABILITY_ID --param key=value`；涉及写入时遵守确认边界。

完成标准：能力名称、风险、来源和参数契约都有实际返回；不把“能力可发现”表述为“业务已完成”。
