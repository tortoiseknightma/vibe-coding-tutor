# /tutor

Generate a human-oriented tutorial for the current project. After building or modifying code, use this command to create a learnable walkthrough.

## Process

1. **Analyze the project**: Read the codebase structure, key files, and tech stack
2. **Generate tutorial** with these sections:

### Section 1: Project Map (鸟瞰全局)
- What the project does (one sentence)
- Tech stack used
- Core idea in 2-3 sentences
- Directory skeleton with purpose explanations (not just names)

### Section 2: Tech Stack Primer (技术栈速成)
For each key technology (max 5):
- What it is (plain language)
- Why it was chosen
- The one key concept to understand
- Learning resource link

### Section 3: Architecture Walkthrough (架构走读)
Trace ONE concrete request through the entire system:
- Entry point → processing → storage → response
- Use a narrative, not abstract descriptions

### Section 4: Key Patterns Explained (关键模式解读)
Pick 2-4 important patterns/decisions:
- Where it is (file:line)
- What it does
- Why it was designed this way
- What would break if done differently
- Annotated code snippet

### Section 5: Try It Yourself (动手实验)
2-3 safe experiments:
- What to change (exact file and line)
- Difficulty rating (⭐ to ⭐⭐⭐)
- Steps to follow
- What concept it demonstrates

### Section 6: Extension Points (扩展指引)
For common additions the user might want:
- Files to modify
- Patterns to follow
- Pitfalls to avoid

## Output

Save to `docs/tutorial-YYYY-MM-DD-[feature].md`

## Language

Match the user's language. Use Chinese for explanations, English for code terms and file paths.

## Principles

- Concepts > Syntax — teach patterns, not just code
- Stories > Diagrams — trace one request through the system
- Why > What — the code shows what, the tutorial explains why
- Safe experiments only — educational, low-risk changes
