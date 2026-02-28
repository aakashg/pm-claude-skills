# Contributing to PM Claude Skills

This repo collects Claude Code skills built for product managers. Here's how to add yours.

## How to Create a Skill

### 1. Understand the Structure

Each skill lives in its own directory under `.claude/skills/`:

```
.claude/skills/
└── your-skill-name/
    ├── SKILL.md          # Required: the skill definition
    └── examples/         # Optional: example inputs/outputs
        └── example-1.md
```

### 2. Write Your SKILL.md

A SKILL.md tells Claude Code when and how to apply the skill. It should include:

- **Trigger**: When should this skill activate? (e.g., "When the user asks to write a PRD")
- **Context**: What background knowledge does Claude need?
- **Instructions**: Step-by-step rules for Claude to follow
- **Output format**: What the result should look like
- **Examples**: Input/output pairs showing correct behavior (inline or in the examples/ folder)

### 3. Test It

Before submitting:
1. Drop the skill into your local `.claude/skills/` directory
2. Start a Claude Code session and trigger it
3. Verify the output matches your expectations
4. Test edge cases (missing info, unusual inputs)

### 4. Submit a PR

1. Fork this repo
2. Add your skill directory under `.claude/skills/`
3. Update the README if your skill adds a new category
4. Open a PR with:
   - What the skill does
   - Example usage
   - Any dependencies or assumptions

## Skill Quality Checklist

- [ ] SKILL.md has a clear trigger condition
- [ ] Instructions are specific, not vague
- [ ] Output format is defined
- [ ] At least 2-3 examples included
- [ ] Tested in a real Claude Code session
- [ ] No hardcoded company-specific details (use placeholders)

## Naming Conventions

- Skill directory: `kebab-case` (e.g., `competitive-analysis`)
- Keep names descriptive but short
- Prefix with the PM domain: `prd-writer`, `user-research`, `sprint-planning`

## Questions?

Open an issue if you're unsure whether your skill idea fits this repo.
