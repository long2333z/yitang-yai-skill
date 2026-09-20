# 先确认 whyai 能不能用

适用：第一次使用 CLI，检查版本、登录、Gateway、权益，或遇到命令错误。

## 按这个顺序做

1. 运行 `whyai --version`。如果找不到命令，先按[官方安装说明](https://ai.yitang.top/cli)检查安装和 PATH；这不是登录问题。
2. 运行 `whyai --help`，或本次要用的子命令帮助。帮助页面才是当前版本的参数说明。
3. 需要登录时，使用正式入口：`whyai login --gateway https://ai.yitang.top`。浏览器授权结束后，回到终端继续确认。
4. 运行 `whyai --json status`。正式环境应显示 Gateway `ai.yitang.top` 和 `prod`。
5. 要读取数据或调用 Partner 时，再运行 `whyai --json billing access` 查看 CLI 权益。
6. 最后做一次和任务有关的小范围只读查询。能登录不代表已经能正常调用。

## 常见情况

| 看到什么 | 接下来怎么做 |
| --- | --- |
| 找不到 `whyai` | 回到安装/PATH 检查，不要当成账号错误。 |
| 浏览器已授权，终端仍失败 | 重新看 status 和终端错误。 |
| Gateway 不是 `ai.yitang.top`，或环境不是 prod | 停止业务调用，重新登录后再确认。 |
| 提示权益不足 | 查看 account 和 billing access，把错误原文保留下来。 |
| 帮助与旧资料不同 | 以当前帮助为准，不猜参数。 |

## 做完后告诉用户

说明命令是否可用、版本、Gateway/环境、权益状态，以及实际查询是否成功；失败时说明卡在什么环节。

## 不确定命令怎么用时

先运行 `whyai yitang help` 或目标子命令的 `--help`，选一个只读功能试一次，再继续后续任务。
