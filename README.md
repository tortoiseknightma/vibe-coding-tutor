# vibe-coding-tutor

> An AI agent skill that turns vibe-coding outputs into learnable tutorials.
> 一个把 vibe-coding 产出变成可学习教程的 AI Agent Skill。

[English](#english) | [中文](#中文)

---

## English

### The Problem

Vibe-coding is fast — you describe what you want, AI builds it. But speed comes at a cost: **you don't understand what you now own.** The code works, but you can't maintain it, extend it, or explain it to anyone.

### The Solution

`vibe-coding-tutor` is a skill for AI coding agents (Hermes, Cursor, Claude Code, etc.) that automatically generates a **human-oriented tutorial** after building your project. Not API docs. Not auto-generated comments. A real tutorial that teaches you:

1. **Project Map** — What was built, and why each directory exists
2. **Tech Stack Primer** — The key technologies, explained in plain language
3. **Architecture Walkthrough** — One concrete request traced through the entire system
4. **Key Patterns Explained** — Design decisions, tradeoffs, and non-obvious choices
5. **Try It Yourself** — Safe experiments to deepen understanding
6. **Extension Points** — How to build on this project later

### Installation

#### For Hermes Agent

```bash
# From within Hermes CLI
skill_install vibe-coding-tutor

# Or manually
cp SKILL.md ~/.hermes/skills/software-development/vibe-coding-tutor/
```

#### For Other Agents

Copy `SKILL.md` into your agent's skill/plugin directory. The skill is agent-agnostic — it's a structured prompt that works with any LLM-powered coding agent.

### Usage

After completing a coding task, the agent will automatically offer a tutorial. Or trigger it manually:

```
User: "帮我理解这个项目"
Agent: [generates tutorial in docs/tutorial-YYYY-MM-DD.md]
```

### Tutorial Output Example

```markdown
# Task Manager App Tutorial

## 1. Project Map
项目名称: Task Manager
做什么: 一个支持拖拽排序的任务看板
技术栈: React + TypeScript + Zustand + Tailwind

目录骨架:
  src/
  ├── components/   ← UI 组件层
  ├── stores/       ← 状态管理 (Zustand)
  ├── types/        ← TypeScript 类型定义
  └── utils/        ← 工具函数

## 2. Tech Stack Primer
技术: Zustand
是什么: 轻量级 React 状态管理库
为什么用它: 比 Redux 简单，比 Context 高效
核心概念: store 就是一个自定义 hook，直接在组件里 use
...
```

See [examples/](examples/) for full tutorial samples.

### Philosophy

- **Concepts > Syntax** — "This uses Observer pattern" beats "this has an event listener"
- **Stories > Diagrams** — Trace one request through the system
- **Why > What** — The code shows *what*; the tutorial explains *why*
- **Safe Experiments** — Learn by doing, without breaking things

### Contributing

Issues and PRs welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

### License

MIT — see [LICENSE](LICENSE).

---

## 中文

### 问题

Vibe-coding 很快——你描述需求，AI 来构建。但速度有代价：**你不理解你拥有的东西。** 代码能跑，但你无法维护、扩展或向别人解释它。

### 解决方案

`vibe-coding-tutor` 是一个 AI 编程 Agent 的 Skill（适用于 Hermes、Cursor、Claude Code 等），在构建项目后自动生成一份**面向人类的教程**。不是 API 文档，不是自动注释，是一份真正教你理解项目的教程：

1. **鸟瞰全局** — 构建了什么，每个目录为什么存在
2. **技术栈速成** — 关键技术的通俗解释
3. **架构走读** — 跟踪一个具体请求走完系统全链路
4. **关键模式解读** — 设计决策、权衡取舍、不显然的选择
5. **动手实验** — 安全的小实验加深理解
6. **扩展指引** — 将来如何在此基础上继续开发

### 安装

#### Hermes Agent

```bash
# 在 Hermes CLI 中
skill_install vibe-coding-tutor

# 或手动安装
cp SKILL.md ~/.hermes/skills/software-development/vibe-coding-tutor/
```

#### 其他 Agent

将 `SKILL.md` 复制到你所用 Agent 的 skill/plugin 目录即可。该 skill 与 Agent 无关——它是一个结构化的 prompt，适用于任何 LLM 驱动的编程 Agent。

### 使用

完成编程任务后，Agent 会自动提供教程。也可以手动触发：

```
用户: "帮我理解这个项目"
Agent: [生成教程到 docs/tutorial-YYYY-MM-DD.md]
```

### 设计理念

- **概念 > 语法** — "这里用了观察者模式" 比 "这里有个事件监听器" 更有价值
- **故事 > 图表** — 跟踪一个请求走完全链路，比抽象描述更容易记住
- **为什么 > 是什么** — 代码已经展示了是什么，教程要解释为什么
- **安全实验** — 通过动手做来学习，但不会搞坏东西

### 贡献

欢迎 Issue 和 PR。详见 [CONTRIBUTING.md](CONTRIBUTING.md)。

### 许可证

MIT — 详见 [LICENSE](LICENSE)。

---

## Skill Structure

```
vibe-coding-tutor/
├── SKILL.md              # The skill definition (core)
├── README.md             # This file
├── LICENSE               # MIT license
├── examples/             # Example tutorial outputs
│   └── react-todo-app.md
├── templates/            # Optional: custom tutorial templates
│   └── tutorial-template.md
└── CONTRIBUTING.md       # Contribution guidelines
```

## Compatible Agents

| Agent | Status | Notes |
|-------|--------|-------|
| Hermes | ✅ Native | Primary target |
| Cursor | ✅ | Copy SKILL.md to .cursor/rules/ |
| Claude Code | ✅ | Use as CLAUDE.md reference |
| Copilot | ⚠️ Partial | Works as custom instructions |
| Generic LLM | ✅ | Paste SKILL.md as system prompt |

## Tags

`learning` `teaching` `vibe-coding` `documentation` `onboarding` `tutorial` `architecture`
