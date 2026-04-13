---
name: vibe-coding-tutor
description: After vibe-coding completes, generate human-oriented teaching materials — project walkthroughs, tech stack tutorials, and architecture explanations — so the user learns while building.
version: 1.0.0
author: Hermes Agent
metadata:
  hermes:
    tags: [learning, teaching, vibe-coding, documentation, onboarding]
    related_skills: [writing-plans, subagent-driven-development, systematic-debugging]
---

# Vibe-Coding Tutor

Transform vibe-coding outputs from "black box delivery" into "learnable tutorials". After building something, generate structured teaching materials that help the user understand what was built, why it's structured that way, and what tech concepts are at play.

## When to Use

**Trigger automatically after:**
- Completing a multi-file project or feature (5+ files created/modified)
- User says "explain what you built" or "help me understand this"
- User mentions they want to learn from the code
- After any significant refactoring

**Offer proactively when:**
- User is building something new to them (unfamiliar tech stack)
- Project involves patterns they haven't used before
- User seems to be copy-pasting without understanding

## The Teaching Framework

Generate a **Project Tutorial** with these sections, in order:

### 1. Project Map (鸟瞰全局)

Give a bird's-eye view of the project. Not a file listing — a *mental model*.

```
项目名称: [name]
做什么: [one sentence purpose]
技术栈: [key technologies]
核心思路: [the main idea in 2-3 sentences]

目录骨架:
  src/
  ├── api/          ← 对外接口层 (API layer)
  ├── core/         ← 业务逻辑核心 (Business logic)
  ├── models/       ← 数据模型 (Data models)
  ├── utils/        ← 工具函数 (Utilities)
  └── config/       ← 配置 (Configuration)
```

**Key principle:** Explain the *purpose* of each directory, not just its name.

### 2. Tech Stack Primer (技术栈速成)

For each key technology used, explain:
- **What it is** (1 sentence, no jargon)
- **Why we chose it** (what problem it solves)
- **Key concept you need to know** (the one thing that matters)
- **Where to learn more** (link or resource)

Format:
```
技术: [name]
是什么: [plain language explanation]
为什么用它: [what problem it solves]
核心概念: [the one key idea]
  例: "React 的核心是组件化 — 每个 UI 片段都是一个独立的、可复用的函数"
深入学习: [resource link]
```

Keep it to 3-5 technologies max. Focus on what's most important for understanding this project.

### 3. Architecture Walkthrough (架构走读)

Walk through the project's architecture as a narrative, not a diagram. Use the "request lifecycle" approach:

```
当用户执行 [action] 时，数据流是这样的:

1. [入口] 用户触发 [event]
   → 调用 src/api/handler.ts 的 handleAction()

2. [处理] handler 调用 core/processor.ts 的 process()
   → 这里做了 [what and why]

3. [存储] processor 通过 models/repo.ts 保存数据
   → 选择 [storage method] 因为 [reason]

4. [响应] 返回给用户 [result]
```

**Key principle:** Follow ONE concrete request through the entire system. Abstract descriptions are forgettable; stories stick.

### 4. Key Patterns Explained (关键模式解读)

Pick 2-4 important patterns or decisions in the code. For each:

```
模式: [pattern name]
在哪: [file:line]
是什么: [what it does, plain language]
为什么这么写: [the design decision and tradeoff]
不这么写会怎样: [what would break or be harder]

代码片段:
[paste the actual code, with line-by-line comments in Chinese]
```

Focus on things that would confuse a reader:
- Non-obvious design choices
- Patterns that look weird but have a reason
- Things the user might want to modify later
- Common pitfalls in this area

### 5. Try It Yourself (动手实验)

Suggest 2-3 small, safe experiments the user can do to deepen understanding:

```
实验 1: [what to change]
难度: ⭐ (入门)
步骤:
  1. 打开 [file], 找到 [line/section]
  2. 把 [X] 改成 [Y]
  3. 运行 [command]
  4. 观察 [what happens]
学到了什么: [concept this demonstrates]

实验 2: [what to change]
难度: ⭐⭐ (进阶)
...
```

These should be:
- Low-risk (won't break the project)
- Educational (reveal a key concept)
- Observable (user can see the effect)

### 6. Extension Points (扩展指引)

If the user wants to build on this project later:

```
如果要添加 [feature A]:
  - 需要改: [files]
  - 参考: [existing pattern to follow]
  - 注意: [pitfall]

如果要添加 [feature B]:
  - 需要改: [files]
  - 参考: [existing pattern to follow]
  - 注意: [pitfall]
```

## Generation Process

### Step 1: Gather Context

```
# Understand what was built
search_files("*.py|*.ts|*.js|*.tsx|*.jsx", target="files")
read_file("package.json") or read_file("requirements.txt") or read_file("Cargo.toml")
read_file("README.md") if exists
```

### Step 2: Identify Key Files

Find the most important files — entry points, core logic, config:
```
search_files("def main|export default|class.*App|index\\.", target="content")
```

Read them to understand the architecture.

### Step 3: Generate Tutorial

Write the tutorial to `docs/tutorial.md` (or inline if user prefers).

**Language:** Match user's communication language. Default Chinese.
**Tone:** Friendly senior dev explaining to a curious junior. Not condescending, not textbook.
**Length:** Aim for 2000-4000 chars. Enough to be useful, not so much it's overwhelming.

### Step 4: Offer Follow-up

After generating the tutorial:
1. Ask if any section needs deeper explanation
2. Offer to generate specific deep-dives (e.g., "explain the auth flow in detail")
3. Suggest the "Try It Yourself" experiments

## Output Format

Save to `docs/tutorial-YYYY-MM-DD-[feature].md`:

```markdown
# [项目/功能名称] 教程

> 自动生成 by Hermes Vibe-Coding Tutor
> 生成时间: [date]

## 1. 鸟瞰全局
...

## 2. 技术栈速成
...

## 3. 架构走读
...

## 4. 关键模式解读
...

## 5. 动手实验
...

## 6. 扩展指引
...

---
还有疑问？随时问我。
```

## Principles

1. **Teach concepts, not syntax.** "This uses the Observer pattern" is more valuable than "this has an event listener".

2. **Stories > Diagrams.** Follow one request through the system. Concrete beats abstract.

3. **Why > What.** Always explain *why* a decision was made. The code already shows *what*.

4. **Safe experiments.** Suggested changes should be educational and low-risk.

5. **Respect the user's level.** If they seem advanced, skip basics. If they're new, explain more. Adapt.

6. **Bilingual awareness.** Use Chinese for explanations, but keep code terms and file paths in English.

## Integration with Vibe-Coding Flow

```
Normal vibe-coding:
  User: "帮我做一个 X"
  Agent: [builds it]
  Agent: "Done!"

With tutor:
  User: "帮我做一个 X"
  Agent: [builds it]
  Agent: "Done! 我还生成了一份教程帮你理解这个项目："
  Agent: [shows tutorial summary]
  Agent: "完整教程在 docs/tutorial.md，要我解释哪个部分？"
```

## Remember

```
鸟瞰全局 → 技术栈速成 → 架构走读 → 关键模式 → 动手实验 → 扩展指引
     ↑                                                        ↓
     └──── 用户有问题？深入讲解任何部分 ─────────────────────────┘
```

The goal: **User walks away understanding what they now own.**
