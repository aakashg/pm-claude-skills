# PM Claude Skills

5 ready-to-use Claude Code skills for product managers. Drop them in your `.claude/skills/` folder and they work immediately.

Each skill triggers on natural language — just say "write a LinkedIn post" or "validate this idea" and Claude knows what to do.

**These 5 skills are fully functional — install and use them today. I wrote a deep dive breaking down 6 additional skills with the reasoning behind each one, how I built them, and what makes them work.**

**[Read the full skill breakdown →](https://www.news.aakashg.com/p/steal-6-of-my-claude-skills)**

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

I wrote a deep dive explaining the architecture behind my skill system — how to structure triggers, chain skills together, and build skills that actually produce consistent output.

**[Steal 6 of My Claude Skills →](https://www.news.aakashg.com/p/steal-6-of-my-claude-skills)**

---

Built by [Aakash Gupta](https://www.aakashg.com) | [Product Growth Newsletter](https://www.news.aakashg.com)

---

## How to Create Your Own Skill

Skills are markdown files that extend Claude Code's capabilities for specific PM tasks. Here's how to build one from scratch.

### Step 1: Identify the Task

Pick a task you do repeatedly that has a consistent structure. Good candidates:
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

Once your skill works well, submit it to this repo via PR. See CONTRIBUTING.md for details.
