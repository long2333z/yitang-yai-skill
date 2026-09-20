# 一堂 / YAI CLI Skill

把一堂的 `whyai` CLI、课程知识、Partner 对话和资产沉淀组织为可路由的独立 SOP。它适合在 Codex 中处理“一堂/YAI/whyai、课程、作业、Partner、笔记、会话”相关任务，而不是把所有 CLI 说明堆进一个入口文件。

## 能解决什么

| 你想做的事 | 从哪里开始 | 最终得到什么 |
| --- | --- | --- |
| 检查安装、版本、登录、Gateway 或权益 | [SOP-00 准入](sops/access.md) | 已验证的可用状态，或可复现的阻断点 |
| 查课程、概念、作业或既有笔记 | [学习与知识](sops/learning.md) | 有真实 ID、查询范围与来源的结果 |
| 选择官方 Partner、做多 Partner 接力或设计自建 Partner | [Partner 工作](sops/partner.md) | 明确的角色、任务契约、交接包或可验证设计 |
| 用 Partner 完成真实任务、上传材料、保存可复用结论 | [任务执行与资产](sops/execution.md) | 结果、来源、限制、下一步与可定位资产 |
| 续聊、改写、分支、导出、分享、删除或排错 | [对话与故障](sops/conversation.md) | 边界清楚且可回查的会话处理结果 |

## 使用方式

将仓库根目录安装为 Codex 的一个 Skill，例如放入：

```text
<CODEX_HOME>/skills/yitang-cli/
```

仓库根目录就是 Skill 根目录；不要再套一层 `yitang-cli/`。安装后，可以直接说：

```text
使用 $yitang-cli 查一下某课程的方法，并给出能用于当前项目的步骤。
```

或直接提出自然语言任务，例如“帮我选择适合梳理需求的 Partner”“继续这段一堂对话并导出”“检查 whyai 是否在正式环境可用”。Skill 会先判断目标，再加载一条匹配 SOP；跨阶段任务才顺序加载多条。

## 首次使用 whyai

CLI 的完整安装和登录说明以 [一堂 CLI 使用指南](https://yitanger.feishu.cn/wiki/XoFcwMmotigm7Ikv4RQc9TfQn0g) 为准。开始真实任务前，按 [SOP-00](sops/access.md) 完成以下验证链：

1. `whyai --version`：确认命令可执行。
2. `whyai --help`、`whyai yitang help` 或目标子命令的 `--help`：确认当前版本的命令契约。
3. `whyai --json status`：确认正式 Gateway 为 `ai.yitang.top`，环境为 `prod`。
4. 有读取/调用需求时运行 `whyai --json billing access`：确认 CLI 权益，而不是只看通用额度。
5. 用范围最小的只读查询验证真实调用；浏览器授权成功不等于业务调用成功。

登录、上传、创建消息或笔记、分享、删除、发布 Partner 等会产生外部影响或消耗权益的动作，均应在明确目标和授权后执行。

## 推荐的任务链

```text
准入 R0
  ├─ 方法与学习 R1 ──> 实际执行 R4 ──> 会话控制 R5 ──> 资产/封装 R6
  └─ Partner 选择 R2 ──> 实际执行 R4
                       └─ 多阶段接力 R3 ──> 实际执行 R4
```

复杂任务的实用顺序是：先确定问题和来源范围 → 选择课程知识或 Partner → 补齐任务、材料、目标输出、约束 → 执行与精确修订 → 区分事实、推断、未决项 → 保存可复用资产。

## 资料与事实边界

本仓库只引用三份官方资料：

- [一堂 CLI 使用指南](https://yitanger.feishu.cn/wiki/XoFcwMmotigm7Ikv4RQc9TfQn0g)
- [YAI 使用指南](https://yitanger.feishu.cn/wiki/WPJWwKwI3iUCzqkGUzvc6i5MnNg)
- [YAI 一堂第一课](https://yitang.top/fs-doc/217da0c5f7d334b601c53526ed06f90d/MZFMd7mYPofbJ2xQhdEcS3Xrnvd)

它们的 [本地结构化语义快照](references/official-sources.md) 用于离线分析与 SOP 设计，并非逐字全文导出。当前命令参数、Gateway、权限、账号状态与真实结果必须以本次 `--help`、CLI 返回和官方实时页面为准。若三者冲突，优先运行时事实，并记录差异后再修订 SOP。

## 仓库结构

```text
SKILL.md                         # 只做任务路由与共享护栏
agents/openai.yaml               # Codex 展示信息
sops/                            # 按任务独立加载的执行 SOP
references/core-sop-map.md       # 来源证据到核心任务链的映射
references/official-sources.md   # 三份官方来源和本地快照入口
references/snapshots/            # 带章节锚点的结构化语义快照
skill-optimizer-records/         # 维护/优化记录，不参与运行时加载
```

## 维护规则

更新流程遵循“官方资料 → 结构化快照 → 证据地图 → 匹配 SOP → 校验”的单向链路。不要把详细 CLI 手册复制进 `SKILL.md`，也不要用历史快照覆盖当前 `--help` 或 CLI 返回。修改后运行 Skill Creator 的 `quick_validate.py`，再同步到实际安装目录。
