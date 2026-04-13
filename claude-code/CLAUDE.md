# Vibe-Coding Tutor — Claude Code Instructions

> Add this file to your project root as `CLAUDE.md` (or append to existing one).
> Or place it in `~/.claude/CLAUDE.md` to apply globally.

## After-Code Tutorial Generation

After completing any significant coding task (5+ files, new feature, or refactoring), automatically generate a project tutorial. This helps the user understand what was built.

### Tutorial Structure

Generate a tutorial with these 6 sections:

**1. Project Map (鸟瞰全局)**
- Project purpose (one sentence)
- Tech stack summary
- Directory skeleton with purpose labels (e.g., `src/api/ ← 对外接口层`)

**2. Tech Stack Primer (技术栈速成)**
For each key technology (max 5):
- What it is (one sentence, no jargon)
- Why chosen (what problem it solves)
- Core concept (the one thing that matters)
- Learning resource

**3. Architecture Walkthrough (架构走读)**
Follow ONE concrete request through the entire system. Narrative format:
```
当用户 [action] 时:
1. [Entry] → triggers [function]
2. [Processing] → [what happens]
3. [Storage] → [how data persists]
4. [Response] → [what user sees]
```

**4. Key Patterns Explained (关键模式解读)**
Pick 2-4 non-obvious design decisions:
- Location (file:line)
- What and why
- What would break if done differently
- Annotated code snippet

**5. Try It Yourself (动手实验)**
2-3 safe, educational experiments:
- Exact file and line to modify
- What to change
- Expected result
- Concept demonstrated

**6. Extension Points (扩展指引)**
For likely future features:
- Files to touch
- Patterns to follow
- Pitfalls

### Output

Save to `docs/tutorial-YYYY-MM-DD-[feature].md`

### Language

Use the user's communication language for explanations. Keep code terms and file paths in English.

### Trigger

Automatically offer after completing a task, or when user says:
- "帮我理解这个项目"
- "explain what you built"
- "生成教程"

### Principles

- **Concepts > Syntax** — teach patterns, not just code
- **Stories > Diagrams** — trace one request through the system
- **Why > What** — code shows what; tutorial explains why
- **Safe experiments only** — no risky changes suggested
