# Project Documentation Skill (人机双重视角项目技术文档与 Mermaid 避坑规范)

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Target Agents](https://img.shields.io/badge/Agents-Antigravity%20%7C%20Claude%20Code%20%7C%20Cursor%20%7C%20Codex-purple.svg)](#)

本仓库提供了一套面向现代软件工程团队与 AI 编码助手的 **项目技术文档治理与架构图表渲染规范技能**。打破传统文档仅面向人类的单一局限，构建“人类工程师 + AI Agent 结对伙伴”双重视角的知识库体系，提供非硬编码的目录自适应探测机制与规避 Markdown 预览器崩溃的 Mermaid 4 大渲染铁律。

---

## 🌟 核心规范亮点 (Highlights)

- **智能目录探测 (Folder-Agnostic)**：不强绑定任何单一文件夹名，自动识别既有的 `docs/`、`wiki/`、`documentation/`、`project_wiki/` 或在项目根目录下智能初始化。
- **人机双重视角 (Dual-Audience Architecture)**：
  - **Human-Facing**：业务全景背景、可视化拓扑图、接口契约手册、开发部署指南；
  - **Agent-Facing Context**：领域实体与术语映射字典、核心代码物理路径索引（Code Path Mapping）、架构决策记录（ADR & 踩坑历史 Gotchas）。
- **分类分层子目录治理**：按 `architecture/`、`api/`、`guides/`、`agent-context/` 模块化组织，杜绝文档平铺堆砌。
- **Mermaid 渲染防坑 4 大铁律**：
  - 🚫 严禁菱形判断节点嵌套 `{...}`（防 AST 词法崩溃）；
  - 🚫 连线条件 `|...|` 必须纯文本（严禁中英文括号与逗号）；
  - 🚫 所有节点 Label 文本强制显式双引号包裹；
  - 🚫 箭头必须精确指向具体节点 ID，严禁直连 `subgraph` 容器。
- **增量维护与完整性原则**：严禁粗暴覆写或清空已有章节，保证文档即真实代码镜像。

---

## 📂 仓库结构 (Repository Layout)

```text
.
├── SKILL.md                          # 根目录 Agent Skill 核心规范说明文件
├── skills/
│   └── project-documentation/
│       └── SKILL.md                  # 符合标准多 Skill 管理器规范的目录结构
├── .gitignore                        # Git 忽略规则
├── LICENSE                           # MIT 开源许可证
└── README.md                         # 详尽的中文项目说明与章节导航
```

---

## 🚀 安装与使用 (Installation & Usage)

### 1. Antigravity IDE / Antigravity CLI
全局自动生效：
```bash
mkdir -p ~/.gemini/config/skills/project-documentation
cp SKILL.md ~/.gemini/config/skills/project-documentation/SKILL.md
```

作为项目工作区本地技能生效：
```bash
mkdir -p .agents/skills/project-documentation
cp SKILL.md .agents/skills/project-documentation/SKILL.md
```

### 2. 通过 Agent Skills 包管理器安装
```bash
npx skills add Garfield247/agent-skill-project-documentation
```

---

## 📄 开源许可证 (License)

本项目基于 [MIT License](LICENSE) 开源。


## 📦 安装与多 Agent 使用指南 (Installation & Multi-Agent Usage)

本项目遵循开放 Agent 规范，支持在 **Gemini / Antigravity**、**Anthropic Claude**、**Cursor / Codex** 等各类主流 Agent 环境中一键安装与激活：

### 1. Google Antigravity / Gemini Code Assist
- **全局安装（推荐）**：
  ```bash
  git clone git@github.com:Garfield247/agent-skill-project-documentation.git ~/.gemini/config/skills/project-documentation
  ```
- **项目工作区局部引入**：
  ```bash
  mkdir -p .agents/skills
  git clone git@github.com:Garfield247/agent-skill-project-documentation.git .agents/skills/project-documentation
  ```

### 2. Anthropic Claude (Claude Code / Claude Projects)
- **Claude Code (CLI 终端智能体)**：
  克隆至 Claude 全局技能库：
  ```bash
  mkdir -p ~/.claude/skills
  git clone git@github.com:Garfield247/agent-skill-project-documentation.git ~/.claude/skills/project-documentation
  ```
  *或者在项目根目录的 `CLAUDE.md` 中追加引入：*
  ```markdown
  See detailed engineering specifications in: ~/.claude/skills/project-documentation/SKILL.md
  ```
- **Claude Projects (Web / 桌面端)**：
  直接将仓库中的 `SKILL.md` 内容复制并粘贴至 Project 的 **Project Knowledge (项目知识库)** 或 **Custom Instructions (自定义指令)** 中。

### 3. Cursor / GitHub Copilot / OpenAI Codex
- **Cursor (现代 MDC 规则体系)**：
  在项目根目录创建或链接规则：
  ```bash
  mkdir -p .cursor/rules
  # 克隆或软链接为 Cursor 专有规则文件
  git clone git@github.com:Garfield247/agent-skill-project-documentation.git .cursor/rules/project-documentation
  ```
- **GitHub Copilot / Codex**：
  将本技能规范注入 Copilot 指令集：
  ```bash
  mkdir -p .github
  cat << 'EOF' >> .github/copilot-instructions.md
  # 引入本技能核心规则
  EOF
  cat path/to/SKILL.md >> .github/copilot-instructions.md
  ```

