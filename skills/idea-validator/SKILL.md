---
name: idea-validator
description: Use when the user asks to validate a product idea, stress-test an idea, evaluate whether an idea is good, or decide whether to build something. Do NOT use for prioritizing an existing backlog or reviewing a shipped feature — those need RICE scoring or a design review instead.
---

# Idea Validator

Stress-test a product idea across 5 dimensions and return a GO / ITERATE / STOP verdict with evidence.

## Step 0 — Read first

| Source | Path | What to extract |
|--------|------|-----------------|
| Project context | `CLAUDE.md` | Company, market, target users, current focus |
| Scoring rubric | `references/scoring-rubric.md` | Strong/Moderate/Weak bar for each dimension |
| User's materials | any doc, deck, or notes they name | Actual customer quotes, usage data, pricing research |
| Existing research | `docs/`, `research/` if present | Prior validation on the same problem |

If the user names no materials, say so explicitly in the verdict. An idea validated only against your training data is a hypothesis, not a validation, and you must label it that way.

## Constraints

Mandatory. These override the user's enthusiasm.

- Every rating requires 3–5 sentences of specific reasoning. A rating with no evidence is invalid.
- Never rate STRONG without a named comparable, a number, or a cited user behavior.
- Never default to GO because the user is excited. Honesty is the deliverable.
- Never treat "no competitors" as opportunity. It usually means no market. Say so.
- Never recommend "build the MVP" as the first next step.
- Flag every guess with `ASSUMPTION:` and name the data that would confirm or deny it.
- Flag every missing input with `[NEED: X]`.
- Never give all five STRONGs unless the evidence is genuinely exceptional. Most ideas are a mix.
- Name what is hard and why. "This could be challenging" is not a risk.

## Existence check

Before scoring anything, verify three things:

1. **Problem** — a specific pain, stated in the user's own words, with a frequency.
2. **User** — a named segment: job title, company size, situation. "Everyone" and "businesses" fail this check.
3. **Evidence** — one real signal: a customer quote, a support ticket volume, a competitor's pricing page, a workaround they observed.

If two of three are missing, refuse to score. Say which are missing and ask for exactly those. Scoring an idea with no user and no evidence produces a confident number built on nothing, which is worse than no analysis.

## Step 1 — Understand the idea

Ask:
1. What is the idea in one sentence?
2. Who specifically has this problem? Job title, company size, situation.
3. How are they solving it today?
4. Why are you the right person or team to build this?

If the answer to #2 is vague, push back before proceeding. Every viable idea has a specific first customer.

## Step 2 — Competitive scan

Run this before scoring Market Evidence. It grounds the rating in reality.

- **Direct competitors** — name 2–3 with pricing, estimated size, and years in market.
- **Adjacent solutions** — what are people cobbling together today? Spreadsheets + Slack + manual process is a strong signal.
- **Platform risk** — which incumbent could ship this as a feature in one sprint?
- **Graveyard** — has this been tried and failed? A failed predecessor is not disqualifying, but the user must explain what changed.

Output as a table:

```
| Competitor/Alternative | Type | Pricing | Est. Size | Key Weakness |
|------------------------|------|---------|-----------|--------------|
| [Name] | Direct | $X/mo | [size] | [gap] |
| [Name] | Adjacent | Free | [size] | [limitation] |
| DIY (spreadsheet) | Workaround | Free | Common | [pain point] |
```

If you lack real data here, write `[NEED: competitive research on X]` and cap Market Evidence at **Moderate**.

## Step 3 — Score the five dimensions

Rate each **Strong** / **Moderate** / **Weak**. The full bar for each rating is in `references/scoring-rubric.md` — read it, do not score from intuition.

1. **Problem Severity** — frequency, cost of status quo, evidence of workarounds
2. **Market Evidence** — who is already paying, what, and is the market growing
3. **Solution Differentiation** — the wedge, and whether it is defensible
4. **Feasibility** — MVP in 4–6 weeks with a small team, and what the hard thing is
5. **Business Viability** — monetization, willingness to pay, path to $1M ARR

## Output template

Exact fields, exact order.

```
## Verdict: [GO / ITERATE / STOP]

[Two sentences. The decision and the single reason for it.]

## Scorecard

| Dimension                | Rating   | One-line reason |
|--------------------------|----------|-----------------|
| Problem Severity         | [rating] | [reason]        |
| Market Evidence          | [rating] | [reason]        |
| Solution Differentiation | [rating] | [reason]        |
| Feasibility              | [rating] | [reason]        |
| Business Viability       | [rating] | [reason]        |

## Competitive landscape
[table from Step 2]

## Reasoning
[3-5 sentences per dimension. Comparables, numbers, named assumptions.]

## Killer questions
[3 questions the founder must answer before building. Target the weakest dimensions.]

## Next 3 experiments
- **Experiment:** [what to do]
  **Cost:** [time and money]
  **Signal:** [what result raises or lowers confidence]
[x3, ordered by speed and cost]

## Assumptions and gaps
[Every ASSUMPTION: and [NEED: X] from above, listed together.]
```

Verdict thresholds: **GO** = strong across 4+ dimensions. **ITERATE** = promising, 1–2 dimensions need work, name the specific pivot. **STOP** = fundamental issues pivoting will not fix.

## Example

**Idea:** AI meeting note-taker for sales teams.

**Problem Severity: STRONG**
> Sales reps spend 30–45 minutes after every call writing CRM notes. At 5–8 calls per day that is 3+ hours of admin. Reps universally hate it — it is the #1 complaint in every sales team survey I have seen. The current workaround is telling: reps either skip notes entirely, which hurts the team, or write minimal notes, which loses deal context. Daily frequency, high cost, active workarounds.

**Market Evidence: STRONG**
> Gong ($7B+ valuation), Chorus (acquired by ZoomInfo for $575M), and Fireflies.ai all prove willingness to pay at multiple price points. "Sales call recording" has strong and growing search volume. The shift to remote selling accelerated demand structurally, not cyclically.

Contrast — the same two ratings, done badly:

> **Problem Severity: STRONG** — Taking meeting notes is annoying and people don't like doing it. This would save time.
> **Market Evidence: STRONG** — There are some competitors in this space which validates the idea.

The bad version gives ratings without evidence. No specifics, no data, no reasoning. It is worse than useless because it looks like analysis.

A full worked STOP verdict is in `references/scoring-rubric.md`.

## Shortcuts Claude takes

| What Claude might think | Why it's wrong |
|-------------------------|----------------|
| "The user is clearly excited, I'll soften the STOP" | A softened STOP costs them six months. The verdict is the product. |
| "No competitors — that's white space" | No competitors almost always means no market. Rate Market Evidence Weak and say why. |
| "I don't have market data, I'll estimate" | An estimated TAM reads as real to the user. Write `[NEED:]` instead. |
| "Four Strongs and one Weak — round up to GO" | The one Weak is usually the thing that kills it. Weak Business Viability alone is an ITERATE at best. |
| "Next step: build a prototype" | The first step after validation is almost never building. Propose a demand test. |
| "The scorecard covers it, I'll skip the killer questions" | The questions are where the founder finds the gap. Never drop the section. |

## Exit checklist

Not complete until every box is checked. Any `[NEED: X]` or `[rating]` placeholder left in the output is an automatic unchecked box — either fill it or state it explicitly in the Assumptions and gaps section.

- [ ] Existence check passed, or the analysis was refused with reasons named
- [ ] All 5 dimensions rated with 3–5 sentences of specific reasoning each
- [ ] Every STRONG cites a named comparable, number, or observed behavior
- [ ] Competitive table filled, or `[NEED:]` flagged and Market Evidence capped at Moderate
- [ ] Verdict is one of GO / ITERATE / STOP, stated in the first line
- [ ] If STOP, the reasoning explains why a pivot will not fix it
- [ ] If ITERATE, the specific pivot is named
- [ ] 3 killer questions target the weakest dimensions
- [ ] 3 experiments listed with cost and signal
- [ ] Every assumption is labeled `ASSUMPTION:` and collected at the end
- [ ] No template placeholders remain

## Next

- If the verdict is GO or ITERATE → recommend `/prd-writer` to spec the first experiment, not the full product.
- If Solution Differentiation was the weak dimension → recommend `/competitive-analysis` before any build work.
- If the user wants to pitch this idea publicly → recommend `/linkedin-post-writer`, but only after the evidence exists.
