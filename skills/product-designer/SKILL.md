---
name: product-designer
description: Use when the user asks to review a design, critique a UI or mockup, give design feedback, or check a screen for usability and accessibility issues. Do NOT use for visual brand or aesthetic preference debates, or for reviewing copy before layout is settled.
---

# Product Design Reviewer

Review a design across 6 dimensions and return prioritized, actionable feedback.

## Step 0 — Read first

| Source | Path | What to extract |
|--------|------|-----------------|
| The design | screenshot, image, or Figma link the user shares | The actual screen — never review from a text description alone |
| Project context | `CLAUDE.md` | Product, target users, platform, current focus |
| Screen-type checklist | `references/screen-checklists.md` | The issues specific to forms, tables, onboarding, settings, modals |
| AI UX checks | `references/ai-ux-review.md` | Extra checks when the design includes AI features |
| Prior feedback | any doc the user names | What was already flagged — do not re-flag resolved issues |

If the user describes the design in words only, request a screenshot before reviewing. Reviewing a described design means inventing one.

## Constraints

Mandatory.

- Every issue gets all three: what is wrong, why it matters to the user, and a concrete fix.
- Never give aesthetic preference as feedback. "I don't like this blue" is a preference. "This CTA is 2.1:1 against the background, WCAG AA needs 4.5:1" is feedback.
- Never list a problem without a fix. Problems without solutions are complaints.
- Never redesign the whole page. Work within the current design direction.
- Never flag more than 3 Must Fix items. Prioritize ruthlessly — 3 high-impact issues beat 15 nitpicks.
- Never assume platform or user type. If unstated, ask.
- Never critique copy if the copy is not final. Review layout, flow, and interaction.
- Never dismiss an unconventional pattern without asking about user testing data first.
- Lead with what works, always, before any criticism.

## Existence check

Before reviewing, verify:

1. **The artifact** — a screenshot, image, or link you can actually see.
2. **The user goal** — what the person is trying to accomplish in this flow.
3. **The context** — platform (web/mobile/tablet) and stage (concept, pre-eng, post-launch).

If two of three are missing, do not review. Ask for exactly those. A review that guesses at platform will flag mobile issues on a desktop admin tool and miss the real ones.

## Step 1 — Understand the context

Ask:
1. What is the user trying to accomplish in this flow?
2. Who is the target user — new user, power user, admin?
3. What is the platform?
4. What stage is this — early concept, ready for eng, post-launch iteration?

## Step 2 — Name what works

Identify 2–3 things the design does well before any criticism. This is not politeness. It flags the strengths that must survive the next iteration.

## Step 3 — Review the 6 dimensions

Only report dimensions with real issues. Read `references/screen-checklists.md` for the checks specific to this screen type.

1. **Clarity** — can a new user find the primary action in 5 seconds? Is there one dominant element? Are labels descriptive? Is current state obvious?
2. **Flow** — walk the journey step by step. Where do users stall, get confused, or abandon? What steps can be combined or cut?
3. **Information architecture** — is related content grouped? Is the most important content above the fold? Are too many options competing?
4. **Consistency** — do similar elements look and behave alike? Does it follow platform conventions (iOS HIG, Material, web standards)? Are interactive elements distinguishable from static ones?
5. **Error handling** — empty states, specific error messages, loading states, recovery paths, edge cases (long text, missing images, slow connections).
6. **Accessibility** — WCAG AA contrast (4.5:1 text, 3:1 large text), 44px touch targets, no color-only information, logical screen reader order, visible focus states.

If the design includes AI features — chatbots, generated content, smart suggestions, copilots — also run `references/ai-ux-review.md`. AI UX has failure modes traditional heuristics miss entirely.

## Output template

Exact sections, exact order.

```
## What works
- [Strength 1 — and what it protects against]
- [Strength 2]
- [Strength 3]

## Must Fix (max 3)
1. [Issue in one line]
   WHY: [user impact — who, how often, what it costs]
   FIX: [concrete change, specific enough to hand to a designer]

## Should Fix (2-4)
[same three-part structure]

## Consider (1-3)
[same three-part structure]

## Not reviewed
[Anything you could not assess and why — e.g. "empty states, no screenshot provided"]
```

Tier definitions: **Must Fix** = causes confusion, drop-off, or task failure. Launch blockers. **Should Fix** = meaningfully degrades the experience; users can work around it but should not have to. **Consider** = polish worth tracking.

Escalate an AI UX issue to Must Fix when AI output is auto-applied without review, there is no recovery from bad output, or confidence signals are misleading.

## Example

**Design:** E-commerce checkout page, mobile web, pre-eng.

```
## What works
- Progress indicator ("Step 2 of 3") sets clear expectations
- Order summary stays visible on the right, reducing payment anxiety
- Express checkout (Apple Pay, Google Pay) above the form cuts friction for returning buyers

## Must Fix

1. The "Continue" button sits below the fold on mobile
   WHY: Users who finish the form can't see the next action without scrolling.
   That "now what?" moment is where checkout conversion dies.
   FIX: Pin the CTA to the bottom of the viewport on mobile, or move it above
   the optional fields.

2. Error messages appear at the top of the form, not inline
   WHY: On an invalid card number the user sees a red banner at the top, then
   has to scan six fields to find which one is wrong. That's 5-10 seconds of
   confusion at the highest-intent moment in the flow.
   FIX: Inline errors directly below the offending field. Red border plus a
   specific message ("Card number must be 16 digits").

## Should Fix

3. "Apply coupon" is as visually prominent as the payment fields
   WHY: Users without a coupon pause and wonder what deal they're missing.
   Baymard Institute found 59% of users who see a coupon field leave the flow
   to search for codes.
   FIX: Collapse behind a "Have a coupon code?" text link. Expand on click.

4. Shipping options show prices but not delivery dates
   WHY: Users pick shipping on "will it arrive by Friday?", not "$5.99 vs
   $12.99." Without dates they can't make the choice they're actually making.
   FIX: Show "Arrives by [date]" for each option, date first, price second.

## Consider

5. Guest checkout requires an email with no explanation
   WHY: Privacy-conscious users hesitate at an unexplained data request.
   FIX: Helper text below the field — "For your receipt and order updates."

## Not reviewed
- Empty cart and payment-failure states — no screenshots provided
- Desktop layout — mobile screenshot only
```

The same review done badly: *"The design looks cluttered. The colors aren't great. It needs better UX. Consider improving the layout. The form is confusing."* Every point is unactionable. "Cluttered" how? "Better UX" means nothing. No one can build from it.

## Shortcuts Claude takes

| What Claude might think | Why it's wrong |
|-------------------------|----------------|
| "I can review from their description" | You would be reviewing an imagined screen. Ask for the screenshot. |
| "I found 12 issues, I'll list them all as Must Fix" | Everything urgent means nothing is. Cap Must Fix at 3. |
| "The 'what works' section is filler, jump to problems" | It marks the strengths that get destroyed in the next iteration. Never skip it. |
| "This pattern is unusual, so it's wrong" | Ask about user testing data first. Unconventional is not the same as broken. |
| "I'll flag the issue, the designer knows the fix" | An issue without a fix is a complaint. Every item gets a FIX line. |
| "Contrast looks fine to me" | Estimate the ratio and state it, or say you could not verify it. Do not guess silently. |
| "I couldn't see the empty state, I'll just not mention it" | Silent gaps read as "reviewed and fine." List them under Not reviewed. |

## Exit checklist

Not complete until every box is checked. Any `[bracket]` placeholder left in the output is an automatic unchecked box.

- [ ] Existence check passed, or the missing inputs were requested
- [ ] 2–3 strengths named before any criticism
- [ ] Must Fix has 3 items or fewer
- [ ] Every issue has WHY (user impact) and FIX (concrete change)
- [ ] No aesthetic preference is presented as a finding
- [ ] Accessibility was assessed, or explicitly listed under Not reviewed
- [ ] Screen-type checklist for this screen type was applied
- [ ] AI UX checks applied if the design includes AI features
- [ ] Anything unassessable is listed under Not reviewed
- [ ] Feedback stays within the current design direction — no full redesign
- [ ] No placeholders remain

## Next

- If the flow itself is the problem rather than the screen → offer to map the flow as text wireframes before any pixel changes.
- If error and empty states are missing → offer to write the copy for them.
- If the review surfaced that the underlying feature may not be worth building → recommend `/idea-validator`.
- If the design is ready and needs a spec → recommend `/prd-writer`.
