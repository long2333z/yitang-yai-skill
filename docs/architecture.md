# 架构文档

## 三层目录

```text
SKILL.md                          # 根路由
  └─ references/index.md          # 三层运行资料索引
       ├─ references/sops/access.md
       ├─ references/sops/scenarios/ # 核心场景编排
       ├─ references/sops/        # 原子 SOP
       ├─ core-sop-map.md
       └─ official-sources.md

docs/                             # 仅维护期读取
  ├─ design.md
  ├─ solution.md
  ├─ architecture.md
  ├─ snapshots/                    # 官方快照与一次性运行观察
  └─ iterations/
```

## 加载规则

- 根入口只负责识别任务和链接到合适层级。
- `references/index.md` 是全部运行资料的目录；每份资料都从该索引或一个已索引 SOP 可达。
- 准入、核心场景、原子 SOP 依次缩小范围：核心场景只编排阶段，原子 SOP 才提供当前阶段的操作。
- SOP 只读取当前任务需要的资料，不把运行说明外的快照和方案一次加载。
- `docs/` 不由根入口引用。它服务于 Creator/维护者的设计和改造，不能被当作运行规则。

## 验证边界

结构验证检查必需文件、链接和索引可达性；真实 CLI 验证确认版本、正式 Gateway、权限和一个最小只读课程调用。两类验证都通过，才能说运行结构和实际读取路径均已覆盖。
