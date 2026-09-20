---
name: yitang-cli
description: "使用本机 whyai CLI 完成一堂/YAI 的账号状态、课程、作业、笔记、Partner 和对话任务；用户提到一堂、YAI、whyai，或要求按固定 SOP 操作时使用。"
---

# 一堂 CLI Skill

本 Skill 只负责把一堂 CLI 的基础入口和固定任务 SOP 组织起来。CLI 的完整能力以当前安装版本的 `--help` 和服务端返回为准；飞书文档只作为外部权威引用，按需读取 [官方引用说明](references/official-guide.md)，不复制其正文。

## 固定环境

- 正式 Gateway：`https://ai.yitang.top`
- 正式环境标识：`prod`
- 默认使用本机可发现的 `whyai`；命令找不到时先检查 CLI 安装和 PATH。
- 未经用户明确指定，不切换 Gateway、环境或账号。

## CLI 基本入口

先按任务需要执行最少的基础检查：

```text
whyai --version
whyai --help
whyai yitang help
whyai chat --help
whyai --json status
whyai login --gateway https://ai.yitang.top
```

- `--help`：确认当前版本真实支持的顶层参数。
- `yitang help`：查看一堂课程、作业等命令入口。
- `chat --help`：发起 Partner 对话前核对参数。
- `--json status`：确认 `gateway` 为 `https://ai.yitang.top`、`environment` 为 `prod`，并判断是否已登录。
- `login`：只在用户明确要求登录或认证时执行；浏览器授权需要用户完成，命令输出的授权链接失效时重新发起登录。

## SOP 路由

用户提出具体业务任务时，读取 [固定任务 SOP](references/sops.md)，只加载匹配的 SOP：

- 账号、环境、CLI 是否可用 → 环境准入 SOP
- 找课程、读课程章节 → 课程检索 SOP
- 找作业、读作业答案 → 作业检索 SOP
- 找或读 YAI 笔记 → 笔记检索 SOP
- 找 Partner、发起对话 → Partner 调用 SOP
- 回看、导出或继续对话，保存结果 → 结果回看与沉淀 SOP

## 执行边界

- 先完成环境准入，再执行对应 SOP；每个查询只取完成任务所需的最小数据。
- 课程、作业、笔记、Partner 和会话的 ID 只能来自本次实际返回，不能猜测或沿用不明来源的 ID。
- `chat`、`--file` 文件上传、笔记创建和其他会产生远端记录或额度消耗的动作，必须由用户明确提出后执行；涉及本地文件时再次核对目标文件和用途。
- 查询失败时保留原始错误，优先按“命令帮助 → 登录状态 → Gateway/环境 → 权限/套餐 → 参数/ID”的顺序排查；不通过盲目重试掩盖失败。

## 结果交付

说明实际执行的命令、关键返回和未完成项；区分“没有查到结果”“没有权限”“未登录”和“命令不支持”。涉及额度、授权或文件上传时，明确告诉用户已发生或尚未发生的远端动作。

需要核对文档背景、授权说明或 CLI 版本变化时，按需读取 [官方引用说明](references/official-guide.md)。
