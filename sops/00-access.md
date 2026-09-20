# SOP-00 环境准入

适用：任何需要实际调用一堂服务的任务。

## 操作

1. `whyai --version`：确认命令可发现。
2. 按任务运行一个最小帮助命令：`whyai --help`、`whyai yitang help` 或 `whyai chat --help`。
3. `whyai --json status`：核对 Gateway、环境和登录状态。
4. 未登录时，只有用户明确要求登录才运行 `whyai login --gateway https://ai.yitang.top`，把浏览器授权交给用户。
5. 任务涉及额度或 CLI 资格时，再运行 `whyai --json billing access`；不要用普通账号登录成功推断 CLI 有资格。

## 完成标准

环境和登录状态有实际返回；Gateway 为 `https://ai.yitang.top`、环境为 `prod`。缺少登录、权限或套餐资格时停止业务 SOP，并交付具体原因。
