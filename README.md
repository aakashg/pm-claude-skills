# PM Claude Skills

[![Stars](https://img.shields.io/github/stars/aakashg/pm-claude-skills?style=flat-square)](https://github.com/aakashg/pm-claude-skills/stargazers)
[![License](https://img.shields.io/github/license/aakashg/pm-claude-skills?style=flat-square)](LICENSE)

6 production-ready Claude Code skills for product managers. Drop them in `.claude/skills/` and they work immediately.

Each skill triggers on natural language. Say "write a LinkedIn post" or "validate this idea" and Claude follows the playbook.

Every skill here follows all **[10 Laws of a Great Claude Skill](LAWS.md)** — the patterns that survived 75 test runs across 25 skills. YAML frontmatter engineered for routing, constraints in the top 100 lines, a read-first table, an output template, one worked example, a table that pre-empts the shortcuts Claude takes, an exit checklist, and a handoff to the next skill.

**All 6 skills are fully functional. I wrote a deep dive breaking down 6 additional skills: the reasoning behind each one, how I built them, and what makes them work.**

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
| 6 | [Social Signal Research](skills/social-signal-research/SKILL.md) | "research customer language on X" | Turns public X/Twitter conversations into a source-backed PM evidence packet |

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
# You should see: idea-validator  linkedin-post-writer  product-designer  prompt-engineer  social-signal-research  status-update-writer
```

Then open Claude Code in your project. Say "write a LinkedIn post" or "validate this idea" — skills load automatically when triggered.

## How Skills Work

Claude Code skills are markdown files in `.claude/skills/` that load on demand. At startup Claude reads only each skill's `name` and `description` from its YAML frontmatter. When your request matches, it loads the full SKILL.md and follows it.

That first sentence is the whole game. If the description does not name the phrases you actually type, the skill never loads and nothing else in it matters. This is Law 1, and it is the most common reason a skill "doesn't work."

```yaml
---
name: status-update-writer
description: Use when the user asks to write a status update, weekly or monthly update, stakeholder update, project update, standup, status report, or QBR. Do NOT use for writing a PRD or a retro doc — those need different structures.
---
```

Think of the body as a playbook: each skill encodes a specific workflow so Claude produces the same shape of output every run.

### Anatomy of a skill in this repo

Every SKILL.md here has the same eight parts, in this order:

| Part | Why it exists |
|------|---------------|
| YAML frontmatter | Routing. Claude only sees this at startup |
| `## Step 0 — Read first` | Without a source table, Claude invents the analysis from training data |
| `## Constraints` | Rules below line 100 stop firing. They go up top |
| `## Existence check` | Refuses the two-hour deliverable for a thing that was never going to ship |
| `## Output template` | Exact fields, exact order — so three runs produce three identical structures |
| `## Example` | One worked example outperforms five rules |
| `## Shortcuts Claude takes` | Pre-empts the rationalization before Claude acts on it |
| `## Exit checklist` + `## Next` | Nothing ships with a placeholder in it; the skill routes you onward |

Long background material lives in `references/` inside each skill folder, so the SKILL.md body stays short enough to be read in full. Full reasoning for each part is in [LAWS.md](LAWS.md).

### Combining Skills with CLAUDE.md

Skills work best alongside a `CLAUDE.md` in your project root. The CLAUDE.md sets your global context (who you are, your product, your writing style). Skills handle specific tasks.

```
CLAUDE.md  →  "I'm a PM at a B2B SaaS company. Our product is..."
Skills     →  "When I say 'write a status update,' follow these steps..."
```

This separation matters: CLAUDE.md loads every session; skills load only when triggered. Identity, style rules, and company context belong in CLAUDE.md. Task-specific workflows belong in skills.

### Customizing Skills for Your Team

These skills are starting points. Fork and adapt:

1. **Add your company context** — Replace the worked example with a real one from your product. A status update skill that knows your OKR format is 10x more useful.
2. **Tune the output template** — If your VP prefers a different structure, change the `## Output template` block. That block is what every run reproduces.
3. **Add your shortcuts** — When Claude skips a step, add the rationalization to the `## Shortcuts Claude takes` table. Naming it is what stops it.
4. **Extend the exit checklist** — Every recurring mistake becomes a checkbox. That is the self-improvement loop.

### Troubleshooting

**Skills aren't triggering:**
- Check the frontmatter. No `name` and `description` in YAML at the top means the skill is invisible to routing — this is the #1 cause
- Widen the `description`. It must contain the phrases you actually type, in third person. A short description matches nothing
- Check the path: skills must be in `.claude/skills/[skill-name]/SKILL.md` (not `skills/` at the project root)
- Make sure the file is named exactly `SKILL.md` (case-sensitive)

**Output quality is inconsistent:**
- Check that your `## Output template` gives exact fields in an exact order. A description of the format produces a different format each run
- Add one full worked example rather than more rules. Examples teach faster than instructions
- Move your constraints above line 100. Rules near the bottom of a long file stop firing
- Verify your CLAUDE.md does not contradict the skill
- Use `/clear` between unrelated tasks to prevent context bleed

**Claude skips a step:**
- Add the shortcut to the `## Shortcuts Claude takes` table with the reason it is wrong. Instructing harder does not work; pre-refuting the rationalization does

**Output ships with placeholders in it:**
- Add to the `## Exit checklist`: any `[bracket]` left in the output is an automatic unchecked box

### Keep the loop running

After any session where you corrected the output, ask: what did I regenerate? That is the gap. Fix the skill, not the prompt, and it stops happening.

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

Copy `templates/SKILL-TEMPLATE.md`. It has the 10 laws built into its section order, with a comment on each explaining the failure it prevents.

```bash
cp templates/SKILL-TEMPLATE.md .claude/skills/your-skill-name/SKILL.md
```

Fill it top to bottom. The three that carry the most weight:

**Frontmatter.** Third person, names the phrases users actually type, and names what the skill is *not* for. This is the only part Claude reads before deciding whether to load anything else.

```yaml
---
name: your-skill-name
description: Use when the user asks to X, Y, or Z. Do NOT use for W — use /w instead.
---
```

**Output template.** Give exact fields in an exact order, not a description of the structure. This is the difference between three consistent runs and three different documents.

**One worked example.** A real input and the complete output at full quality. One example beats a dozen rules.

Keep the body under 500 lines and put long background material in `references/` next to the SKILL.md, the way every skill in this repo does.

### Step 4: Test It

1. Drop the skill into `.claude/skills/` in any project
2. Start a Claude Code session
3. Ask using the phrasing you would actually use — not the trigger words you wrote. If it does not load, the description is too narrow
4. Run it three times on the same input. If the structure differs across runs, your output template is a description rather than a template
5. Refine the SKILL.md based on what went wrong. Every correction becomes a checklist item or a row in the shortcuts table

### Step 5: Share It

Once your skill works well, submit it via PR. See CONTRIBUTING.md for details.
