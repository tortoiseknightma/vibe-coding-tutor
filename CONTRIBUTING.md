# Contributing to vibe-coding-tutor

## How to Contribute

### Reporting Issues

- Use GitHub Issues for bugs, feature requests, and questions
- Include your agent type and version when reporting issues
- For tutorial quality issues, include the input project description

### Submitting Changes

1. Fork the repo
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Make your changes
4. Test with at least one real project
5. Submit a PR with a clear description

### Areas for Contribution

- **New tutorial templates** for specific domains (web, mobile, ML, etc.)
- **Agent adapters** for new coding agents
- **Example tutorials** from real projects
- **Translations** of README and templates
- **Bug fixes** in the SKILL.md prompt structure

### Skill Design Principles

When modifying SKILL.md, keep these in mind:

1. **Agent-agnostic** — The skill should work with any LLM-powered agent
2. **Structured but flexible** — Clear sections that adapt to different project types
3. **Teaching-first** — Every design decision should serve learning
4. **Bilingual-friendly** — Explanations in user's language, code terms in English

### Testing Your Changes

Before submitting:

1. Build a real project with your modified skill
2. Generate a tutorial and read it as a newcomer would
3. Check: Does it teach concepts or just describe code?
4. Check: Are the "Try It Yourself" experiments safe and educational?

## Code of Conduct

Be respectful, constructive, and inclusive. We're all here to help people learn.
