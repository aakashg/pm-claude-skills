---
name: status-update-writer
description: Use when the user asks to write a status update, weekly or monthly update, stakeholder update, project update, standup, status report, or QBR. Do NOT use for writing a PRD or a retro doc — those need different structures.
---

# Status Update Writer

Turn messy notes into a precise stakeholder update that stands alone without a follow-up meeting.

## Step 0 — Read first

| Source | Path | What to extract |
|--------|------|-----------------|
| User's raw notes | whatever they pasted | What actually shipped, real numbers, real dates, real names |
| Project context | `CLAUDE.md` | North star metrics, OKRs, company terminology, audience norms |
| Cadence formats | `references/cadences.md` | Daily / monthly / QBR variants of the base format |
| Last update | any prior update they name | What was promised last week — the delta is the story |
| Metrics source | dashboard link or data they provide | Current values only. Never estimate a metric. |

If the user gave you no numbers, the update stays qualitative and you say so. Do not fill the gap.

## Constraints

Mandatory.

- Total update under 200 words for the weekly default.
- Never fabricate progress. If the notes are thin, the update is thin.
- Never hide bad news. It goes in the TL;DR, never at the bottom.
- Never report activity as progress. "Had 6 meetings about the migration" is activity. "Migrated 40% of users at 0.3% error rate" is progress.
- Every risk gets a mitigation. An unmitigated risk is just anxiety.
- Every blocker gets a named owner and a date.
- Every decision request gets a recommendation with reasoning.
- Active voice only. "Team shipped the migration," not "The migration was completed."
- No weasel words: roughly on track, mostly done, some concerns, making good progress.
- Every line passes the "so what?" test for this specific audience. If cutting it changes nothing, cut it.
- Never invent metrics. If the user did not give you a number, write `[NEED: X]`.

## Existence check

Before writing, verify:

1. **The work** — what actually happened, in specifics.
2. **The audience** — who reads this and at what altitude.
3. **The status** — On Track, At Risk, or Blocked, and the evidence for it.

If two of three are missing, do not write. Ask for exactly those. An update written without knowing the audience gets the depth wrong in both directions — too technical for the board, too vague for the eng lead.

## Step 1 — Gather

Ask:
1. What project or initiative is this for?
2. What happened this week? Paste notes, Slack threads, whatever you have — the messier the better.
3. Who is the audience — CEO, VP Eng, cross-functional, skip-level, board?
4. Is there bad news? If so, I will help frame it with a mitigation plan.

Never ask the user to organize their notes first. Extracting structure from mess is the job.

## Step 2 — Calibrate to the audience

| Audience | Focus on | Leave out |
|----------|----------|-----------|
| CEO / C-suite | Outcomes, metrics, strategic implications | Implementation details, technical decisions |
| VP / Director | Progress against milestones, risks, resource needs | Code-level detail, day-to-day tasks |
| Cross-functional | Dependencies, timeline impacts, what they must know | Internal team dynamics, tech debt |
| Engineering lead | Technical blockers, architecture decisions, velocity | Business context they already have |
| Skip-level | Team impact, growth, wins | Minutiae the direct manager handles |
| Board | Metrics, trajectory, market context | Everything operational |

Default cadence is weekly. If the user says daily, monthly, quarterly, or QBR, switch to that format in `references/cadences.md`.

## Output template

Exact fields, exact order. Omit only the sections marked optional.

```
**TL;DR** (2 sentences max)
[The whole update if they read nothing else. Most important thing first.
Bad news goes HERE, not below.]

**Status:** On Track | At Risk | Blocked

**Progress This Week**
- [What shipped or completed — never what was "worked on". Specific numbers.
  Links to PRs, docs, demos, dashboards where provided. Milestones called out.]

**Next Week**
- [What's planned, with owner. Dependencies on other teams flagged.
  Hard deadlines made visible.]

**Risks & Blockers**
- RISK: [description]. Likelihood: [H/M/L]. Impact: [what it costs].
  Mitigation: [the plan].
- BLOCKER: [what's blocked]. Owner: [who unblocks it]. Need by: [date].
[If none: "None currently." Never invent risks to fill the section.]

**Decisions Needed** (omit if none)
[What must be decided, who decides, by when, enough context to decide
without a meeting, and a recommendation with reasoning.]

**Metrics** (omit if the user provided no data)
- [Metric]: [current] (target: [target]) — [trend] — [one-line interpretation]
```

Status definitions: **On Track** = shipping on schedule, no blockers. **At Risk** = potential issues needing visibility, with a mitigation plan. **Blocked** = cannot proceed without a specific decision or action from a specific person.

## Example

**Input notes:** "auth migration, we're at 40% web rollout now up from 10%, error rate 0.3%, load tests done handles 5x peak. mobile has a session bug hitting ~12% of users, jake's on it thinks thursday. launch was march 7, probably march 14 now. waiting on maria for QA signoff before we go past 40%. need to know if we ship web only."

**Output:**

```
TL;DR: Auth migration is at risk. We found a session handling bug
that affects 12% of users on mobile. Fix is in progress — ETA Thursday.
Launch pushed from March 7 to March 14.

Status: AT RISK

Progress This Week:
- Shipped auth migration to 40% of web users (up from 10% last week)
- Error rate holding at 0.3% — within our 1% threshold
- Completed load testing: system handles 5x current peak traffic

Next Week:
- Fix mobile session bug (owner: Jake, ETA Thursday)
- Expand to 100% of web users if mobile fix validates (owner: Sarah)
- Begin mobile rollout at 10% by Friday (owner: Sarah)

Risks & Blockers:
- RISK: Mobile session bug could have deeper root cause than initial
  diagnosis suggests. Likelihood: Medium. Impact: Additional 1-week
  delay. Mitigation: Jake is pairing with platform team on diagnosis.
  If not resolved by Thursday, we'll ship web-only and decouple mobile.
- BLOCKER: Need QA sign-off on load test results before expanding
  beyond 40%. Owner: Maria. Need by: Tuesday EOD.

Decision Needed:
Should we launch web-only on March 10 if the mobile bug isn't fixed,
or hold everything for March 14? I recommend launching web-only —
88% of auth traffic is web, and decoupling de-risks the mobile fix.
Need a decision from @VP-Eng by Wednesday.
```

The same notes written badly: *"This week we continued working on the authentication project. The team has been making good progress. We're also looking into some issues that came up during testing but nothing major. On track for launch, will keep you posted."* No specifics. "Some issues" is hiding a 12% failure rate. "On track" is false. The reader learns nothing and finds out about the slip later, which is how PMs lose trust.

Metrics, done badly and well:

```
Bad:
- Users: going well
- Revenue: looking good
- NPS: stable

Good:
- WAU: 142K (target: 150K) — flat for 3 weeks. Investigating whether
  the new onboarding friction is suppressing activation.
- Revenue: $1.2M MRR (+4% MoM) — on track for Q1 target of $1.3M
- NPS: 34 (down from 38 last month) — correlated with auth migration
  complaints. Expect recovery after bug fixes ship.
```

## Shortcuts Claude takes

| What Claude might think | Why it's wrong |
|-------------------------|----------------|
| "The bad news reads harshly, I'll move it down" | Burying the lead is how stakeholders find out too late. TL;DR or nowhere. |
| "The notes are thin, I'll add reasonable-sounding progress" | Fabricated progress becomes a commitment the user has to defend. Keep it thin. |
| "I don't have the exact metric, I'll approximate" | An approximate metric gets quoted as real in the next meeting. Write `[NEED:]`. |
| "'Working on the migration' counts as progress" | That is activity. Report what completed or explicitly say nothing shipped. |
| "A risk with no mitigation is still worth flagging" | It is anxiety with no action. Either name a mitigation or downgrade it. |
| "The decision is obvious, they'll pick right" | Always state the recommendation. Never make the reader redo your analysis. |
| "This is over 200 words but it's all useful" | Length means the audience calibration is wrong. Cut to the audience's altitude. |

## Exit checklist

Not complete until every box is checked. Any `[NEED: X]`, `[date]`, `[owner]`, or `[metric]` placeholder left in the update is an automatic unchecked box — fill it or ask the user for it before sending.

- [ ] Existence check passed, or missing inputs requested
- [ ] TL;DR is 2 sentences and contains the most important thing
- [ ] If there is bad news, it is in the TL;DR
- [ ] Status is exactly one of On Track / At Risk / Blocked
- [ ] Every Progress bullet is an outcome, not an activity
- [ ] Every Next Week item has an owner where known
- [ ] Every risk has likelihood, impact, and a mitigation
- [ ] Every blocker has a named owner and a date
- [ ] Any decision request includes a recommendation with reasoning
- [ ] Every metric has current value, target, trend, and interpretation
- [ ] Under 200 words for weekly (see references/cadences.md for other targets)
- [ ] No weasel words, no passive voice, no fabricated items
- [ ] The update stands alone — no follow-up meeting needed to understand it
- [ ] No placeholders remain

## Next

- If the update surfaced a decision that needs a written case → offer to draft the one-pager.
- If a risk became a real slip → recommend re-running this skill at monthly cadence to reset expectations with the wider group.
- If the update is going to a public or semi-public channel and needs a different register → recommend `/linkedin-post-writer` only for genuinely external wins.
- If the metrics section keeps coming back empty → the gap is instrumentation, not writing. Say so.
