# PM Claude Skills

5 ready-to-use Claude Code skills for product managers. Drop them in your `.claude/skills/` folder and they work immediately.

Each skill triggers on natural language — just say "write a LinkedIn post" or "validate this idea" and Claude knows what to do.

**This is a free set. I shared 6 more skills with full breakdowns in my deep dive.**
**[Get 6 more skills with walkthroughs →](https://www.news.aakashg.com/p/steal-6-of-my-claude-skills)**

---

## The Skills

| # | Skill | Trigger | What It Does |
|---|-------|---------|-------------|
| 1 | [LinkedIn Post Writer](skills/linkedin-post-writer/SKILL.md) | "write a LinkedIn post" | Turns rough ideas into structured LinkedIn posts |
| 2 | [Idea Validator](skills/idea-validator/SKILL.md) | "validate this idea" | Stress-tests product ideas before you invest time |
| 3 | [Prompt Engineer](skills/prompt-engineer/SKILL.md) | "improve this prompt" | Upgrades your prompts using proven techniques |
| 4 | [Product Designer](skills/product-designer/SKILL.md) | "review this design" | Reviews designs for consistency, clarity, and UX issues |
| 5 | [Status Update Writer](skills/status-update-writer/SKILL.md) | "write a status update" | Turns messy notes into clean stakeholder updates |

## Setup

**Option 1: Copy all skills**
```bash
cp -r skills/* /path/to/your/project/.claude/skills/
```

**Option 2: Copy individual skills**
```bash
# Just the ones you want
cp -r skills/linkedin-post-writer /path/to/your/project/.claude/skills/
cp -r skills/idea-validator /path/to/your/project/.claude/skills/
```

**Option 3: Clone and symlink**
```bash
git clone https://github.com/aakashg/pm-claude-skills.git
ln -s pm-claude-skills/skills/* /path/to/your/project/.claude/skills/
```

Then open Claude Code in your project. Skills load automatically.

## How Skills Work

Claude Code skills are markdown files in `.claude/skills/` that load on demand. When you say something that matches a skill's trigger, Claude reads the SKILL.md and follows its instructions.

Think of them like playbooks: each skill encodes a specific workflow so Claude produces consistent, high-quality output every time.

## Want More?

I wrote a full breakdown of 6 additional skills with explanations of why each one works.

**[Steal 6 of My Claude Skills →](https://www.news.aakashg.com/p/steal-6-of-my-claude-skills)**

---

Built by [Aakash Gupta](https://www.aakashg.com) | [Product Growth Newsletter](https://www.news.aakashg.com)
