# 一堂官方资料引用

## 权威来源

| 来源 | 用途 | 本地快照 |
| --- | --- | --- |
| [一堂 CLI 使用指南](https://yitanger.feishu.cn/wiki/XoFcwMmotigm7Ikv4RQc9TfQn0g) | CLI 安装、登录、基础命令和业务入口 | [CLI 快照](snapshots/cli-guide-2026-09-20.md) |
| [一堂 YAI 使用指南](https://yitanger.feishu.cn/wiki/WPJWwKwI3iUCzqkGUzvc6i5MnNg) | 随聊随调、先训再聊、存成资产、Partner、追问、对话管理和笔记 | [YAI 快照](snapshots/yai-guide-2026-09-20.md) |
| [一堂 YAI 第一课](https://yitang.top/fs-doc/217da0c5f7d334b601c53526ed06f90d/MZFMd7mYPofbJ2xQhdEcS3Xrnvd) | YAI 定位、三层使用进阶、知识库/Partner/笔记/CLI 的组合方式 | [第一课快照](snapshots/yai-first-class-2026-09-20.md) |

快照是 2026-09-20 通过浏览器读取官方页面后整理的本地分析基线，保留来源 URL、可见目录、核心原文要点和与 SOP 的关系。页面正文或 CLI 行为变化后，应重新读取官方页面并生成新日期快照，不把快照当成服务端实时事实。

需要快速理解三份资料如何收敛为可执行分支时，读取[核心 SOP 证据映射](core-sop-map.md)。

## 读取时机

- 需要理解产品场景、选择入口或解释“为什么这样做”时读取 YAI 使用指南/第一课。
- 需要分析或调整核心 SOP 时，先读取三个本地快照，再回到对应官方页面核对可能变化的内容。
- 需要确认 CLI 命令或参数时优先运行当前 CLI 的 `--help`，再读取 CLI 指南补充背景。
- 需要实际结果时必须回到 `whyai` 执行，不用官方资料正文代替服务端返回。

## 事实优先级

1. 当前 `whyai --help`、子命令帮助和实际返回决定命令是否可执行。
2. 官方资料决定场景意图、产品定位和用户可理解的使用路径。
3. 二者不一致时保留命令原文，说明差异，不把文档示例强行当成当前版本参数。

## 引用边界

本文件只维护来源和读取条件，不复制三份资料正文。输出业务结论时只引用完成当前任务所需的最小来源。
