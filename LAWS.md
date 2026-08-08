# 10 Laws of a Great Claude Skill

Derived from 75 test runs across 25 skills. These 10 patterns survived every comparison. Every skill in this repo follows all ten; `templates/SKILL-TEMPLATE.md` encodes them section by section.

Plain text is what breaks. `Monospace` is the line to put in your SKILL.md.

---

## Part 1 — Description: routes the work

Nothing else fires if the skill never loads.

### 1. Engineer the description for routing

Claude scans only the name and description at startup. A 37-character description stayed invisible to 10 of 10 prompts that should have triggered it.

```
Use when the user asks to X, Y or Z. — third person, always.
Do NOT use for W — use /w instead.
```

---

## Part 2 — Body: constrains the work

### 2. Write commands, not requests

"Could you take a look?" returns a friendly note with no severities.

```
Flag every issue with severity (Critical/High/Med/Low).
Cite file and line. Do not soften.
```

### 3. Open with a read-first table

"Check the relevant files" makes Claude invent analysis from training data.

```
## Step 0 — Read first
| Source | Path | What to extract |
```

### 4. Put constraints in the top 100 lines

Safety rules at line 700 of a 724-line coach never fired once.

```
Body under 500 lines. Constraints up top.
Background → references/
```

### 5. Ship a template, not a description of one

Same prompt, three mornings, three different output structures.

```
## Output template
Exact fields, exact order, one worked example.
```

### 6. One worked example beats five rules

12 rules for commit messages produced 3 formats in 3 runs.

```
## Example
Input: … → Output: … (write examples, not rules)
```

### 7. Name the shortcut before Claude takes it

A self-review step got skipped in 4 of 5 runs, instructions unchanged.

```
| What Claude might think | Why it's wrong |
```

---

## Part 3 — Exit: closes the loop

### 8. End with an exit checklist

An investor update shipped with `[MRR figure]` still in the body.

```
Not complete until every box is checked.
Any placeholder left → unchecked.
```

### 9. Hand off to the next skill

The analysis names a retention problem, stops, and you become the router.

```
## Next
If [signal] → recommend /retention-analysis
```

### 10. Open with an existence check

A two-hour PRD for a feature that was never going to ship.

```
Verify problem + user + evidence.
If 2 of 3 are missing, refuse and say which.
```

---

## Then keep the loop running

After any session where you corrected the output: what did you regenerate? That is the gap. Fix the skill, not the prompt, and it stops happening.

---

Source: [10 Laws of a Great Claude Skill](https://www.news.aakashg.com) — Aakash Gupta, Product Growth.
