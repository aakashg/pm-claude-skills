---
name: prompt-engineer
description: Use when the user asks to improve, optimize, rewrite, debug, or shorten a prompt, or asks why a prompt is producing bad output. Do NOT use for writing a Claude Code SKILL.md — that needs skill structure rules, not prompt techniques.
---

# Prompt Engineer

Diagnose a prompt, rewrite it, and show exactly what changed and why.

## Step 0 — Read first

| Source | Path | What to extract |
|--------|------|-----------------|
| The prompt | whatever the user pasted | Actual wording — never paraphrase before diagnosing |
| Failing output | the output they got, if provided | The failure mode; this determines the fix |
| Project context | `CLAUDE.md` | Audience, product, banned words, output preferences |
| Technique reference | `references/techniques.md` | Full before/after examples for each technique |

If the user pasted a prompt but no failing output, ask for one example of what it produced. Diagnosing from the prompt alone guesses at the failure mode.

## Constraints

Mandatory.

- Always show before and after. The user must see the diff, not just the result.
- Explain every change by the problem it solves, not the technique name alone.
- Preserve the user's intent. Improve how they ask, never what they are asking for.
- Right-size the fix. A 10-line prompt that works beats a 50-line prompt that confuses.
- Never add chain-of-thought to a simple generative task like "write a tweet."
- Never write "be thorough and comprehensive." Name exactly what to cover.
- Never add a role that does not match the task.
- Never add a few-shot example below the quality bar you expect back. Bad examples teach bad patterns.
- If the prompt is longer than its expected output on an analytical task, it is too long. Cut it.

## Existence check

Before rewriting, verify:

1. **The prompt itself** — the literal text, not a description of it.
2. **The goal** — what the user wants the output to do or be used for.
3. **The failure** — what the current output gets wrong, ideally with a sample.

If two of three are missing, do not rewrite. Ask for exactly those. Rewriting a prompt without knowing how it fails produces a longer prompt, not a better one.

## Step 1 — Diagnose

Score the prompt across these dimensions. Name which ones fail.

| Dimension | What to check |
|-----------|---------------|
| Role | Is there a specific persona? Generic "you are an expert" does not count. |
| Context | Does the model have enough background to do the task well? |
| Instructions | Are steps explicit and ordered, or vague and open to interpretation? |
| Output format | Is structure defined — headers, fields, length, tone? |
| Examples | Are there input/output pairs showing what good looks like? |
| Constraints | Are there explicit DO/DON'T rules? Edge cases handled? |
| Evaluation | Can the model self-check its output against clear criteria? |

## Step 2 — Match the failure to the fix

If the user provided failing output, use this table instead of guessing.

| Symptom | Cause | Fix |
|---------|-------|-----|
| Generic, "could be anyone" | Missing role or weak context | Add a specific persona with domain details |
| Misses the point entirely | Ambiguous — model chose a valid but wrong reading | Add a "Your goal is..." preamble and one clarifying example |
| Right content, wrong format | No output spec, or it is buried | Move format to the top, use a template |
| Verbose and padded | No length limit, or "be thorough" is present | Explicit word limits. Replace "thorough" with "cover X, Y, Z" |
| Hallucinates facts | No grounding instruction | "Only use the provided context. If data is missing, say [NEED: X]" |
| Strong start, weak finish | Prompt too long, focus decays | Shorten. Move examples before instructions. Cut redundancy. |
| Ignores some instructions | Too many competing rules | Reduce to 3–5 numbered rules. Add "These rules are mandatory." |

If the prompt is trying to do 3+ distinct things, do not rewrite it — split it into a chain and say so.

## Step 3 — Apply techniques

Match technique to the diagnosed problem. Not every prompt needs every technique. Full before/after examples for each are in `references/techniques.md`.

- **Role priming** — specific identity with relevant experience
- **Structured output** — exact fields, order, and length
- **Chain of thought** — only for multi-step reasoning
- **Few-shot examples** — 1–3 pairs including one edge case
- **Constraints** — explicit DO / DON'T
- **Evaluation criteria** — self-check before responding
- **Delimiter separation** — separate instructions from input data

## Output template

Exact sections, exact order.

~~~
## Diagnosis
[2-3 sentences. Which dimensions fail and what that causes in the output.]

## Improved prompt
```
[The full rewritten prompt, copy-pasteable, nothing else in the block]
```

## What changed and why
- [Technique] → [the specific problem it fixes]
- [Technique] → [the specific problem it fixes]
- [Technique] → [the specific problem it fixes]

## How to test it
Run it with [specific input]. You should see [specific difference].
If it still fails, try [fallback].
~~~

## Example

**Before:**
```
Write a competitive analysis of Notion.
```

**Diagnosis:** No role, no structure, no audience, no scope, no output format. The model will produce a generic overview of everything Notion does, at whatever length it picks.

**After:**
```
You are a senior product strategist at a B2B knowledge management company competing with Notion.

Analyze Notion's AI features specifically. Structure your analysis as:

1. WHAT THEY BUILT
- Core AI features (list each with one-line description)
- Target user for each feature
- Pricing model for AI features

2. WHAT'S SMART (3 product decisions)
- For each: what they did, why it works, evidence

3. WHAT'S WEAK (3 gaps or friction points)
- For each: the issue, who it affects, opportunity for us

4. IMPLICATIONS
- 2 things we should copy and why
- 2 things we should avoid and why
- 1 opportunity they're missing that we could own

Rules:
- Be specific. "Good UX" is not analysis. Name the interaction and explain why it works.
- If you don't have data, say "[NEED: data on X]" instead of guessing.
- Keep total output under 800 words.
```

**What changed and why:**
- Role priming → output comes from a strategic angle instead of an encyclopedia entry
- Structured output → every run returns the same four sections, so runs are comparable
- Scope narrowing ("AI features specifically") → prevents a shallow survey of the whole product
- Grounding rule → replaces invented statistics with a visible gap marker
- Length cap → forces selection instead of padding

**How to test it:** Run both versions. The original will open with "Notion is an all-in-one workspace." The rewrite will open with a named feature and a pricing tier.

Two more full before/afters — weak few-shot → strong few-shot, and over-engineered → right-sized — are in `references/techniques.md`.

## Shortcuts Claude takes

| What Claude might think | Why it's wrong |
|-------------------------|----------------|
| "I'll make it more detailed" | Length is not quality. Most broken prompts get better by cutting. |
| "Add a role to be safe" | An irrelevant role ("world-class neurosurgeon" on a marketing brief) adds noise. |
| "The user knows what changed, skip the diff" | The diff is the teaching. Without it they cannot improve the next prompt themselves. |
| "I'll improve the task while I'm here" | Never change what they are asking for. Only how they ask it. |
| "One example is enough, I'll write it quickly" | A sloppy example teaches sloppiness. The example is the quality bar. |
| "This prompt does five things, I'll just tighten it" | Five things needs a chain, not a tighter paragraph. Say so. |

## Exit checklist

Not complete until every box is checked. Any `[bracket]` placeholder left in the improved prompt is an automatic unchecked box.

- [ ] Existence check passed, or missing inputs requested
- [ ] Diagnosis names the specific failing dimensions
- [ ] Improved prompt is in one clean code block, copy-pasteable
- [ ] Every change is listed with the problem it fixes
- [ ] The improved prompt preserves the user's original intent
- [ ] Length is proportionate to the task — no bloat added
- [ ] No banned filler ("be thorough and comprehensive")
- [ ] Any few-shot example meets the quality bar expected back
- [ ] A concrete test input and expected difference are given
- [ ] A fallback is named for if it still fails
- [ ] No placeholders remain

## Next

- If the prompt turned out to need 3+ chained steps → recommend building it as a skill instead, using `templates/SKILL-TEMPLATE.md`.
- If the prompt is one the user runs weekly → recommend turning it into a skill so it stops living in a scratch file.
- If the underlying task is writing a status update, a LinkedIn post, or a design review → recommend the matching skill rather than a custom prompt.
