---
name: skill-name-in-kebab-case
description: Use when the user asks to X, Y, or Z. Do NOT use for W — use /other-skill instead.
---

<!--
This template encodes the 10 laws of a great Claude skill. See LAWS.md.
Every section below exists because skipping it caused a measured failure.
Delete these comments and the [brackets] as you fill it in.

Law 1 — the description above is the whole routing decision. Claude reads only
the name and description at startup. Third person, always. Name the trigger
phrases users actually type, and name what this skill is NOT for.
-->

# [Skill Name]

[One line: what this skill produces.]

## Step 0 — Read first

<!-- Law 3. Without this table Claude invents the analysis from training data. -->

| Source | Path | What to extract |
|--------|------|-----------------|
| Project context | `CLAUDE.md` | [what matters from it] |
| [Reference doc] | `references/[file].md` | [the detail that lives there] |
| [User's input] | [where it comes from] | [what to pull out] |

[State what to do if a source is missing. Never silently proceed.]

## Constraints

<!-- Law 4. Constraints live in the top 100 lines or they never fire.
     Law 2. Commands, not requests. "Flag every X" not "consider flagging X". -->

Mandatory.

- [Hard limit with a number]
- [Never do X]
- [Always do Y]
- [Banned words or patterns]

## Existence check

<!-- Law 10. Stops the two-hour deliverable for a thing that was never going to ship. -->

Before starting, verify:

1. **[Input 1]** — [what counts as present]
2. **[Input 2]** — [what counts as present]
3. **[Input 3]** — [what counts as present]

If two of three are missing, refuse. Say which are missing and ask for exactly those. [One sentence on what goes wrong if you proceed anyway.]

## Step 1 — [Action]

[Numbered, ordered instructions. Be specific enough that two runs produce the same shape.]

## Step 2 — [Action]

[Decision logic: "If the user provides X, do Y. Otherwise ask for X."]

## Output template

<!-- Law 5. Ship the template, not a description of one. Same prompt on three
     mornings must produce the same structure. -->

Exact fields, exact order.

```
## [Section 1]
[what goes here, with the constraint on it]

## [Section 2]
| [Column] | [Column] |
|----------|----------|
| [what]   | [what]   |

## [Section 3]
[what goes here]
```

## Example

<!-- Law 6. One worked example beats five rules. Show a real input and the
     real output, not a description of the output. -->

**Input:** [realistic messy input a user would actually paste]

**Output:**

```
[The complete, correct output. Full quality bar. No ellipses.]
```

[Optionally: the same input done badly, and one line on why it fails.]

## Shortcuts Claude takes

<!-- Law 7. Name the shortcut before Claude takes it. Steps that are merely
     instructed get skipped; steps whose skip-rationale is pre-refuted don't. -->

| What Claude might think | Why it's wrong |
|-------------------------|----------------|
| "[The plausible rationalization]" | [The concrete cost of acting on it] |
| "[Another one]" | [Cost] |
| "[Another one]" | [Cost] |

## Exit checklist

<!-- Law 8. Not complete until every box is checked. -->

Not complete until every box is checked. Any `[bracket]` placeholder left in the output is an automatic unchecked box.

- [ ] Existence check passed, or missing inputs were requested
- [ ] [Each constraint above, restated as a verifiable check]
- [ ] [Output matches the template exactly]
- [ ] No placeholders remain

## Next

<!-- Law 9. Close the loop. Do not make the user route. -->

- If [signal] → recommend `/[other-skill]`.
- If [signal] → offer [the natural follow-on].
