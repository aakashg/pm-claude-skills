# PM Claude Skills

[![Stars](https://img.shields.io/github/stars/aakashg/pm-claude-skills?style=flat-square)](https://github.com/aakashg/pm-claude-skills/stargazers)
[![License](https://img.shields.io/github/license/aakashg/pm-claude-skills?style=flat-square)](LICENSE)

5 production-ready Claude Code skills for product managers. Drop them in `.claude/skills/` and they work immediately.

Each skill triggers on natural language. Say "write a LinkedIn post" or "validate this idea" and Claude follows the playbook.

**All 5 skills are fully functional. I wrote a deep dive breaking down 6 additional skills: the reasoning behind each one, how I built them, and what makes them work.**

**[Read the full skill breakdown →](https://www.news.aakashg.com/p/steal-6-of-my-claude-skills)**

---

## The Skills

| # | Skill | Trigger | What It Does |
|---|-------|---------|-------------|
| 1 | [LinkedIn Post Writer](skills/linkedin-post-writer/SKILL.md) | "write a LinkedIn post" | Turns rough ideas into structured, high-performing LinkedIn posts |
| 2 | [Idea Validator](skills/idea-validator/SKILL.md) | "validate this idea" | Stress-tests product ideas across 5 dimensions before you invest time |
| 3 | [Prompt Engineer](skills/prompt-engineer/SKILL.md) | "improve this prompt" | Diagnoses and upgrades prompts using proven techniques |
| 4 | [Product Designer](skills/product-designer/SKILL.md) | "review this design" | Reviews designs for clarity, consistency, and UX issues |
| 5 | [Status Update Writer](skills/status-update-writer/SKILL.md) | "write a status update" | Converts messy notes into precise stakeholder updates |

## Setup

**Option 1: One-liner install (all skills)**
```bash
git clone https://github.com/aakashg/pm-claude-skills.git /tmp/pm-claude-skills && \
  mkdir -p .claude/skills && \
  cp -r /tmp/pm-claude-skills/skills/* .claude/skills/
```

**Option 2: Cherry-pick individual skills**
```bash
mkdir -p .claude/skills
# Copy just the ones you want
cp -r /tmp/pm-claude-skills/skills/linkedin-post-writer .claude/skills/
cp -r /tmp/pm-claude-skills/skills/idea-validator .claude/skills/
```

**Option 3: Clone and symlink (auto-updates when you `git pull`)**
```bash
git clone https://github.com/aakashg/pm-claude-skills.git ~/pm-claude-skills
mkdir -p .claude/skills
ln -s ~/pm-claude-skills/skills/* .claude/skills/
```

**Verify it worked:**
```bash
ls .claude/skills/
# You should see: idea-validator  linkedin-post-writer  product-designer  prompt-engineer  status-update-writer
```

Then open Claude Code in your project. Say "write a LinkedIn post" or "validate this idea" — skills load automatically when triggered.

## How Skills Work

Claude Code skills are markdown files in `.claude/skills/` that load on demand. When your input matches a skill's trigger, Claude reads the SKILL.md and follows its instructions.

Think of them as playbooks: each skill encodes a specific workflow so Claude produces consistent, high-quality output every time.

### Combining Skills with CLAUDE.md

Skills work best alongside a `CLAUDE.md` in your project root. The CLAUDE.md sets your global context (who you are, your product, your writing style). Skills handle specific tasks.

```
CLAUDE.md  →  "I'm a PM at a B2B SaaS company. Our product is..."
Skills     →  "When I say 'write a status update,' follow these steps..."
```

This separation matters: CLAUDE.md loads every session; skills load only when triggered. Identity, style rules, and company context belong in CLAUDE.md. Task-specific workflows belong in skills.

### Customizing Skills for Your Team

These skills are starting points. Fork and adapt:

1. **Add your company context** — Replace generic examples with real ones from your product. A status update skill that knows your OKR format is 10x more useful.
2. **Tune the output format** — If your VP prefers a different structure, change it. The skill must match how your org actually communicates.
3. **Add your anti-patterns** — Every team has recurring mistakes. Add them to the relevant skill's anti-patterns section.

### Troubleshooting

**Skills aren't triggering:**
- Check the path: skills must be in `.claude/skills/[skill-name]/SKILL.md` (not `skills/` at the project root)
- Make sure the file is named exactly `SKILL.md` (case-sensitive)
- Try using the exact trigger phrase from the skill (e.g., "write a LinkedIn post")

**Output quality is inconsistent:**
- Add more examples to the skill's Examples section. Examples teach Claude patterns faster than instructions
- Verify your CLAUDE.md does not contradict the skill's instructions
- Use `/clear` between unrelated tasks to prevent context bleed

## Want More?

I wrote a deep dive on the architecture behind my skill system: how to structure triggers, chain skills together, and build skills that produce consistent output.

**[Steal 6 of My Claude Skills →](https://www.news.aakashg.com/p/steal-6-of-my-claude-skills)**

---

Built by [Aakash Gupta](https://www.aakashg.com) | [Product Growth Newsletter](https://www.news.aakashg.com)

---

## How to Create Your Own Skill

Skills are markdown files that extend Claude Code for specific PM tasks. Here is how to build one from scratch.

### Step 1: Identify the Task

Pick a repeatable task with consistent structure. Good candidates:
- Writing PRDs, one-pagers, or status updates
- Doing competitive analysis
- Preparing for user interviews
- Prioritizing a backlog

### Step 2: Create the Directory

```bash
mkdir -p .claude/skills/your-skill-name
```

### Step 3: Write the SKILL.md

Use the template below (also available at `templates/SKILL-TEMPLATE.md`):

```markdown
# Skill: [Skill Name]

## Trigger
Activate this skill when the user asks to [describe trigger condition].

## Context
[Background knowledge Claude needs. Industry terms, frameworks, assumptions.]

## Instructions
1. [Step-by-step rules for Claude to follow]
2. [Be specific — vague instructions produce vague output]
3. [Include decision points: "If X, do Y. Otherwise, do Z."]

## Output Format
[Describe the expected structure: headings, bullet points, tables, length]

## Examples

### Example 1
**Input:** [What the user says]
**Output:** [What Claude should produce]

### Example 2
**Input:** [Another scenario]
**Output:** [Expected result]

## Anti-patterns
- [Common mistakes to avoid]
- [Things this skill should NOT do]
```

### Step 4: Test It

1. Drop the skill into `.claude/skills/` in any project
2. Start a Claude Code session
3. Ask Claude to perform the task described in your trigger
4. Evaluate the output — does it match your expectations?
5. Refine the SKILL.md based on what went wrong

### Step 5: Share It

Once your skill works well, submit it via PR. See CONTRIBUTING.md for details.
