---
name: project-documentation
description: >-
  人机双重视角项目技术文档体系、分类分层目录治理、00 号标准约束与红线第一法则、
  Diátaxis 四象限架构、MADR 架构决策记录、高价值 BUG 案例与深度避坑档案 (Post-Mortems)、
  渐进式披露 (Progressive Disclosure) 与 Mermaid 图表防崩渲染生产级规范技能。
---

# 项目技术文档治理与知识工程规范 (Project Documentation Skill)

本技能定义了为软件工程编写维护技术文档、架构时序决策与工程避坑档案时的标准体系、文档与代码同频门禁与渐进式手册索引。

---

## 1. 核心铁律与绝对红线 (Core Redlines)

1. 🚨 **人机三态正交文档治理门禁**：
   - 第一态（AI 规则态：`.agents/rules/`，必须 Git 追踪）；
   - 第二态（人类 SSOT 真理库：`project_wiki/` 或 `docs/`，必须 Git 追踪）；
   - 第三态（瞬态/过程报告态：`.scratch/`，**坚决禁止 Git 追踪**，在 `.gitignore` 排除）。
2. 🚨 **架构与业务逻辑零脱节铁律 (Architecture-Logic Zero-Drift Gate)**：
   - 凡改动涉及调用时序、FSM 状态机、系统拓扑或 API 契约，**必须在同一次 Git 提交中同频修改架构文档**；
   - 严禁“先上线代码、下周补文档”，做到“代码即架构，架构即真相”。
3. 🚨 **中文命名与细节绝不丢失**：
   - 人类文档目录与 Markdown 文件**优先采用中文显式编号命名**（如 `02_架构设计/`）；
   - 严禁以“精简”为由阉割数据表 DDL 约束、枚举字典与错误码，确保细节 100% 保真。
4. 🚨 **Mermaid 语法防崩四大禁令**：
   - 严禁菱形节点嵌套花括号 `{...}`；连线条件 `|...|` 必须为纯文本（禁括号/逗号）；
   - 节点 Label 必须显式双引号包裹；连线必须精确连接到节点 ID，禁连向 subgraph 容器。

---

## 2. 标准开发工作流 (Standard Workflow)

1. **前置摸骨**：首读 `00_标准与规范/` 实体与枚举字典，查阅 `02_架构设计/` 时序流与状态机；
2. **按需路由**：顺着 `<project>/.agents/rules/`（如 `00_project_map.md`）语义锚点指针精准切片查阅，自愈行号偏移；
3. **安全编码**：遵从规范编码并运行自动化测试取得铁证；
4. **同频修改**：同步更新 `project_wiki/` 对应架构图、契约报文与 DDL 字段；
5. **原子提交**：将业务代码与架构文档精准暂存（`git add <code_file> <doc_file>`）并提交闭环。

---

## 3. 渐进式专业参考手册 (Progressive Disclosure References)

根据具体涉及的业务场景，**按需查阅 `references/` 目录下的专门规约**，严禁将全量子文档一次性无脑全部展开：

| 场景模块 | 参考子文档 | 核心涵盖规范 |
| :--- | :--- | :--- |
| **Diátaxis 架构与分层** | [01_diataxis_framework_and_hierarchy.md](references/01_diataxis_framework_and_hierarchy.md) | • 智能目录探测 (Folder Discovery)<br>• Diátaxis 四象限显式编号目录树规范与 00 号总纲 |
| **MADR 架构决策记录** | [02_madr_architectural_decision_records.md](references/02_madr_architectural_decision_records.md) | • MADR 标准架构决策记录结构<br>• 提议/采纳/废弃状态流转与否决权衡沉淀 |
| **故障复盘与避坑档案** | [03_post_mortems_and_immunity_cases.md](references/03_post_mortems_and_immunity_cases.md) | • 高价值案例甄选门槛 (排障抗体)<br>• 根因剖析、反例对比与永久免疫标准模版 |
| **Mermaid 防崩四大铁律** | [04_mermaid_four_zero_crash_rules.md](references/04_mermaid_four_zero_crash_rules.md) | • 菱形节点禁嵌套花括号、连线纯文本<br>• 文本双引号与精确节点 ID 安全时序图范式 |
| **三态治理与元指针地图** | [05_three_tier_documentation_and_project_map.md](references/05_three_tier_documentation_and_project_map.md) | • 规则态 vs 知识库态 vs 瞬态工件三态模型<br>• `<project>/.agents/rules/` 语义锚点自愈规范 |
