---
name: linkedin-post-writer
description: Use when the user asks to write, draft, or rewrite a LinkedIn post, turn notes or an article into a LinkedIn post, or fix a hook that is not landing. Do NOT use for X/Twitter threads, newsletters, or blog posts — those need different length and hook rules.
---

# LinkedIn Post Writer

Turn a rough idea into one publishable LinkedIn post: one hook, one format, one CTA.

## Step 0 — Read first

Read these before writing a single line. Do not write from memory of "how LinkedIn posts go."

| Source | Path | What to extract |
|--------|------|-----------------|
| Project context | `CLAUDE.md` | Who the user is, their product, banned words, audience |
| Post patterns | `references/post-patterns.md` | 5 full worked posts + why each works |
| User's raw input | whatever they pasted | The one insight, the specific numbers, the personal detail |
| Prior posts | any file/link the user names | Their actual voice — match it, do not invent one |

If `references/post-patterns.md` is missing, say so and proceed with the worked example below only.

## Constraints

These are mandatory. Violating any one means the draft is not done.

- Hook is ONE line. Two-line hooks lose reach. No exceptions.
- Total body 800–1,300 characters. Under 800 reads thin; over 1,300 truncates in feed.
- Exactly ONE call to action. Not two, not "and follow me."
- Zero or one emoji. Zero is the default.
- No paragraph longer than 3 lines.
- The post must contain at least one specific number, name, or timeframe.
- Never use: delve, landscape, synergy, leverage, robust, streamline, cutting-edge.
- Never open with "I'm excited to announce" or "Thrilled to share."
- No hashtags in the body. If requested, 3–5 after a line break at the end.
- Lead with the insight, never the product. Product appears in context or not at all.

## Existence check

Before drafting, verify three things:

1. **The insight** — one sentence the reader did not already know.
2. **The evidence** — a number, a named result, a specific story the user actually lived.
3. **The audience** — a specific person or role, not "professionals."

If two of three are missing, do not draft. Say which are missing and ask for exactly those. A post with no insight and no evidence is engagement bait, and publishing it costs the user credibility.

## Step 1 — Gather

Ask, in one message:
1. What is the one insight or takeaway?
2. Who is the target reader?
3. Any hook or angle you want?
4. Format preference — listicle, story, hot take, before/after, framework, observation — or should I pick?

If the user pasted raw notes, a thread, or an article, extract the insight yourself and confirm it in one line. Never ask the user to organize their notes first.

## Step 2 — Pick the format

| Format | Best for | Optimizes for |
|--------|----------|---------------|
| Listicle | Tips, lessons, frameworks | Saves |
| Story arc | Personal turning points | Comments |
| Hot take | Challenging conventional wisdom | Shares |
| Before/after | Transformations, results | Saves |
| Framework | Teaching a concept | Saves |
| Observation | Industry trends | Speed |

## Output template

Produce exactly this, in this order. No preamble, no "here's your post!"

```
[HOOK — one line, no context needed to understand it]
[RE-HOOK — one line: adds heft, creates contrast, or preempts the objection]

[BODY — 8–16 lines. Chosen format. 1-3 line paragraphs, alternating single
lines with short clusters. At least one signpost line showing how the author
knows this. Specific numbers throughout.]

[CLOSER — the reusable line. The part someone screenshots.]

[CTA — one question, low friction, easy to answer. "P.S." form works well.]
```

Then, below the post, output:
- **Character count:** [number]
- **Format used:** [name]
- **Hook alternatives:** two more one-line hooks the user can swap in.

## Example

**Input:** "I want to write about how I only got clients once I stopped posting about myself. Got my first 10 clients in 2024 with under 1,000 followers."

**Output:**

```
How to get your first 10 clients on LinkedIn:
(even if you have less than 1,000 followers)

Most people overcomplicate this.

They build funnels, run ads, and buy courses.

But the people I've watched go from 0 to 6 figures did 4 things:

1. Picked ONE problem they solve
→ Not 5. Not "I help businesses grow." One specific pain.

2. Posted 3x/week about that problem
→ Not about themselves. About the reader's pain.

3. Commented on 20 posts a day from their ideal clients
→ Not "Great post!" — they added a missing insight or tip #8.

4. Ended every conversation with "How can I help?"
→ Not "Buy my thing." Just helped. For free. Consistently.

That's it. No funnel. No ads. No viral post needed.

The boring stuff works. Most people just won't do it long enough.

P.S. What's the one thing that got YOU your first client?
```

**Character count:** 1,043
**Format used:** Listicle
Why this works: the parenthetical re-hook removes the reader's excuse before they raise it. Each point carries a DO and a DON'T, which forces specificity. The P.S. is low friction.

Four more worked posts — story arc, framework, contrarian, observation — are in `references/post-patterns.md`. Read them before choosing a format.

## Shortcuts Claude takes

| What Claude might think | Why it's wrong |
|-------------------------|----------------|
| "The hook works, the checklist is a formality" | The checklist catches character count and double-CTA every time. Run it. |
| "Two lines make a stronger hook" | Two-line hooks measurably lose reach. Cut to one. |
| "I'll add a second CTA so they can also follow" | Two CTAs halve the response rate on both. |
| "The user has no numbers, I'll write it generically" | A post with no specifics is indistinguishable from every other post. Ask for the number. |
| "This is a product launch, so lead with the product" | Product-first posts get scrolled. Insight first, always. |
| "I'll show the draft, then run the checklist" | Run it silently first and fix the issues. Show only the clean version. |

## Exit checklist

Run this silently. Fix every failure, then present the clean draft. Not complete until every box is checked. Any placeholder left in the draft — `[name]`, `[number]`, `[company]` — is an automatic unchecked box.

- [ ] Hook is one line and works with zero context
- [ ] Re-hook adds contrast, heft, or handles an objection
- [ ] Body is 800–1,300 characters
- [ ] At least one specific number, name, or timeframe appears
- [ ] A signpost line establishes why the author knows this
- [ ] No paragraph exceeds 3 lines
- [ ] Exactly one CTA, phrased as an easy question
- [ ] Zero or one emoji
- [ ] No banned words
- [ ] Read aloud: sounds like a coffee chat, not a keynote
- [ ] Remove any sentence starting with "I'm excited to," "I believe that," "It's important to"
- [ ] No placeholders remain
- [ ] Two alternative hooks are included below the post

## Next

- If the user liked the post and wants more from the same insight → offer to spin it into a 3-post sequence.
- If the insight turns out to be about a product idea they have not validated → recommend `/idea-validator` before they post a claim they cannot back.
- If they want to reuse this post as a prompt for future drafts → recommend `/prompt-engineer`.
