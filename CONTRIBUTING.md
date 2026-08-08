# Contributing to PM Claude Skills

This repo collects Claude Code skills built for product managers. Every skill here follows the [10 Laws of a Great Claude Skill](LAWS.md). PRs that skip them will be asked to add them, so start from the template.

## How to Create a Skill

### 1. Understand the Structure

Each skill lives in its own directory:

```
.claude/skills/
└── your-skill-name/
    ├── SKILL.md              # Required: the skill definition
    └── references/           # Optional: background material the body links to
        └── patterns.md
```

The SKILL.md body stays under 500 lines. Anything longer — example galleries, scoring rubrics, checklists — goes in `references/` and gets pulled in by the Step 0 read-first table. Constraints buried past line 100 stop firing.

### 2. Write Your SKILL.md

Start from `templates/SKILL-TEMPLATE.md`. Required sections, in order:

| Section | Requirement |
|---------|-------------|
| YAML frontmatter | `name` and `description`. Third person, names real trigger phrases, names what the skill is NOT for |
| `## Step 0 — Read first` | Table of Source / Path / What to extract, plus what to do when a source is missing |
| `## Constraints` | Imperative, numeric where possible, in the top 100 lines |
| `## Existence check` | The 2-of-3 inputs required before starting, and the refusal if they are missing |
| `## Output template` | Exact fields in exact order, inside a code block |
| `## Example` | One realistic input and the complete output at full quality bar |
| `## Shortcuts Claude takes` | Table of the rationalization and its concrete cost |
| `## Exit checklist` | Every constraint restated as a checkbox, plus the no-placeholders rule |
| `## Next` | Where to route when the work is done |

Write commands, not requests. "Flag every issue with severity" produces severities. "Could you take a look?" produces a friendly note.

### 3. Test It

Before submitting:
1. Drop the skill into your local `.claude/skills/` directory
2. Trigger it with the phrasing you would naturally use, not the exact words in your description. If it does not load, the description is too narrow
3. Run it three times on the same input. Identical structure every time, or the output template needs to be more exact
4. Test the refusal path: give it an input missing two of the three existence-check inputs and confirm it refuses instead of producing something
5. Test with a deliberately thin input and confirm nothing gets fabricated to fill the template

### 4. Submit a PR

1. Fork this repo
2. Add your skill directory under `skills/`
3. Update the README skills table
4. Open a PR describing what the skill does, an example run, and what you found in step 3 of testing

## Skill Quality Checklist

- [ ] YAML frontmatter with `name` and `description` in third person
- [ ] Description names the phrases users actually type, and what the skill is NOT for
- [ ] `## Step 0 — Read first` table present, with missing-source handling
- [ ] Constraints are imperative and appear in the top 100 lines
- [ ] Body under 500 lines; background material moved to `references/`
- [ ] Existence check refuses when 2 of 3 required inputs are missing
- [ ] `## Output template` gives exact fields in exact order
- [ ] At least one complete worked example at the quality bar expected
- [ ] `## Shortcuts Claude takes` table names 3+ plausible rationalizations
- [ ] `## Exit checklist` covers every constraint and flags leftover placeholders
- [ ] `## Next` routes to a follow-on skill or action
- [ ] Tested three times for structural consistency
- [ ] Refusal path tested
- [ ] No hardcoded company-specific details (use placeholders in examples)

## Naming Conventions

- Skill directory: `kebab-case`, matching the `name` in frontmatter exactly
- Keep names descriptive but short
- Prefix with the PM domain: `prd-writer`, `user-research`, `sprint-planning`

## Questions?

Open an issue if you're unsure whether your skill idea fits this repo.
