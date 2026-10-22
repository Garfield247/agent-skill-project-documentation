# MADR 标准架构决策记录规范 (MADR Specifications)

## 1. MADR 模版标准 (`docs/02_architecture/adr_decisions/`)

重大技术选型与架构折中必须撰写 MADR，记录决策背景与否决理由：

```markdown
# ADR-0001: [标题：决策的核心主题，如：状态机跃迁使用 Redis Lua 分布式锁替代乐观锁]

## 1. 状态 (Status)
- **状态**：提议中 (Proposed) / 已采纳 (Accepted) / 已废弃 (Deprecated) / 已被替代 (Superseded by ADR-0005)
- **决定日期**：2026-XX-XX
- **决策制定人**：[架构师 / 核心开发人员]

## 2. 背景上下文与面临挑战 (Context and Problem Statement)
- 面临什么高并发、数据一致性或性能瓶颈？
- 现有方案在什么量级下无法支撑？

## 3. 考虑过的备选方案 (Considered Options)
1. **方案 A (最终采纳)**：[简要说明]
2. **方案 B (已否决)**：[简要说明]
3. **方案 C (已否决)**：[简要说明]

## 4. 决策结果与理由 (Decision Outcome)
- **最终选定**：方案 A
- **采纳理由**：
  - [理由 1：写入时延降低至 2ms]
  - [理由 2：完美化解 TOCTOU 竞态]
- **否决理由 (Why Rejected)**：
  - *方案 B 否决原因*：在 5000 QPS 下数据库重试冲突率高达 35%，导致主库 CPU 爆满。

## 5. 优势与代价折中 (Pros and Cons of the Options)
### 带来优势 (Good Consequences)
- 彻底消除了并发脏读与状态回跳。
### 产生代价与防范措施 (Bad Consequences & Mitigations)
- 增加了对 Redis 实例高可用 (Sentinel/Cluster) 的依赖；必须实现自动降级告警。
```
