# Status Update Writer

## Trigger
Activate when the user asks to "write a status update", "weekly update", "stakeholder update", "write a project update", or "status report".

## Behavior

### Step 1: Gather Context
Ask:
1. What project or initiative is this for?
2. What happened this week? (Paste notes, Slack messages, whatever you have — the messier the better)
3. Who is the audience? (CEO, VP Eng, cross-functional team, skip-level, board)
4. Is there bad news? (If so, I'll help you frame it with a mitigation plan)

If the user pastes raw notes, Slack threads, or bullet points — extract and structure the information yourself. Don't ask the user to organize it first.

### Step 2: Write the Update

Follow this exact structure:

---

**TL;DR** (2 sentences max)
The entire update if they read nothing else. Lead with the single most important thing. If there's bad news, it goes here — not buried below.

**Status: [pick one]**
- **On Track** — shipping on schedule, no blockers
- **At Risk** — potential issues that need visibility, with mitigation plan
- **Blocked** — cannot proceed without a decision or action from someone specific

**Progress This Week**
- Bullet points of what actually shipped or completed — not what was "worked on"
- Be specific: "Shipped new onboarding flow to 10% of users" not "Made progress on onboarding"
- Include links to PRs, docs, demos, or dashboards if the user provides them
- If a milestone was hit, call it out explicitly

**Next Week**
- What's planned, with owners where known
- Highlight dependencies on other teams or decisions
- If something needs to happen by a specific date, make the deadline visible

**Risks & Blockers**
- Every risk gets: description, likelihood, impact, mitigation plan
- Every blocker gets: what's blocked, who can unblock it, by when
- If there are none, write "None currently" — don't fabricate risks to fill the section

**Decisions Needed** (include only if applicable)
- State exactly what needs to be decided
- Who needs to decide it
- By when
- Enough context that the reader can decide without scheduling a meeting
- If possible, include your recommendation: "I recommend Option A because..."

**Metrics** (include only if applicable and the user provides data)
- Key metric: current value vs. target, trend (up/down/flat), brief interpretation
- Don't include metrics for the sake of it — only if they tell a story

---

### Step 3: Tone Calibration

Adjust content and depth based on audience:

| Audience | Focus On | Leave Out |
|----------|----------|-----------|
| **CEO / C-suite** | Outcomes, metrics, strategic implications | Implementation details, technical decisions |
| **VP / Director** | Progress against milestones, risks, resource needs | Code-level details, day-to-day tasks |
| **Cross-functional** | Dependencies, timeline impacts, what they need to know | Internal team dynamics, technical debt |
| **Engineering lead** | Technical blockers, architecture decisions, velocity | Business context they already know |
| **Skip-level** | Your team's impact, growth, wins | Minutiae that your direct manager handles |
| **Board** | Metrics, trajectory, market context | Everything operational |

### Formatting Rules
- Total update should be under 200 words. If it's longer, you're including too much detail for the audience.
- No filler. "We continued to make progress on..." → just say what was done.
- Bad news goes above the fold, not buried at the bottom. Always pair bad news with a mitigation plan.
- Active voice. "Team shipped the migration" not "The migration was completed."
- Use parallel structure in bullet points. Start each with a verb.

---

## Good vs. Bad Examples

### Bad Update (vague, buries bad news, no actions)

```
Subject: Weekly Update - Auth Project

Hi team,

This week we continued working on the authentication project. The team
has been making good progress and we're feeling positive about the
direction. We had some productive discussions about the technical
approach and are aligned on next steps.

We're also looking into some issues that came up during testing but
nothing major. The team is working hard and we expect to have more
updates next week.

On track for launch, will keep you posted.

Thanks,
Sarah
```

What's wrong: No specifics anywhere. "Some issues" is hiding something. "Making good progress" could mean anything. No metrics, no dates, no owners. Reader learns nothing.

### Good Update (specific, honest, actionable)

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

What's different: Specific numbers everywhere. Bad news is in the TL;DR, not hidden. Every risk has a mitigation. The decision request includes a recommendation with reasoning.

### Bad Metrics Section

```
Metrics:
- Users: going well
- Revenue: looking good
- NPS: stable
```

### Good Metrics Section

```
Metrics:
- WAU: 142K (target: 150K) — flat for 3 weeks. Investigating whether
  the new onboarding friction is suppressing activation.
- Revenue: $1.2M MRR (+4% MoM) — on track for Q1 target of $1.3M
- NPS: 34 (down from 38 last month) — correlated with auth migration
  complaints. Expect recovery after bug fixes ship.
```

---

## Common Mistakes to Avoid

**Hiding bad news at the bottom.** If your launch date slipped, that's the TL;DR — not a footnote. Stakeholders lose trust when they discover you buried the lead.

**Confusing activity with progress.** "Had 6 meetings about the migration" is activity. "Migrated 40% of users with 0.3% error rate" is progress. Report outcomes, not effort.

**Using weasel words.** "Roughly on track," "mostly done," "some concerns" — these phrases signal you're not sure what's happening. Be precise. If you don't know, say "investigating, will update by [date]."

**Including everything.** A status update is not a diary. Only include information that matters to THIS audience at THIS level. Your VP doesn't need to know you refactored a utility function.

**No action items.** Every update should make it clear: what do you need from the reader? If nothing, say so. But most "nothing needed" updates are missing something.

---

## Adapting by Cadence

The default format above is a weekly update. For other cadences, adjust scope and depth:

**Daily Standup / Async Daily**
- 3 lines max: What shipped yesterday. What's happening today. Any blockers.
- Skip metrics, risks section, and decisions unless something changed today.
- Format: Plain text, no headers. This should fit in a Slack message.

```
Yesterday: Shipped auth migration to 40% of web users
Today: Running load tests, expanding to 60% if results hold
Blocked: Waiting on QA sign-off from Maria (need by EOD)
```

**Monthly Update**
- Same structure as weekly but zoom out: progress against monthly goals, not daily tasks.
- Add a "Month in Review" summary: 3-5 biggest accomplishments as a bulleted list.
- Include metric trends (not just snapshots): "WAU grew from 130K to 142K (+9%)"
- Add a "Next Month Preview" section with key milestones and dates.
- Target: 300-500 words.

**Quarterly Business Review (QBR)**
- Lead with OKR scorecard: each KR with target vs. actual and red/yellow/green status.
- Include a "Key Decisions Made" section — what big bets were placed and early results.
- Add a "Lessons Learned" section: 2-3 things that would change if you could rerun the quarter.
- Forward-looking: next quarter's top 3 priorities with success criteria.
- Target: 500-800 words. Use tables for OKR scorecards and metric summaries.

When the user doesn't specify cadence, default to weekly. If they mention "monthly," "quarterly," "QBR," or "daily," switch to the matching format.

---

## Anti-Patterns
- Don't fabricate progress. If the user's raw notes are thin, the update should be thin. Don't pad it.
- Don't hide bad news. Your job is to surface it early, with a plan. PMs who hide bad news lose trust fast.
- Don't include items that fail the "so what?" test. If cutting a bullet wouldn't change the reader's understanding or actions, cut it.
- Don't use passive voice to avoid ownership. "The deadline was missed" → "We missed the deadline because X. Here's the recovery plan."
- Don't send a status update that requires a follow-up meeting to understand. The update should stand alone.
- Don't include risks without mitigation plans. An unmitigated risk is just anxiety.

## Rules
- Never fabricate progress or inflate status. If you're behind, say so with a plan.
- Never hide bad news. Surface it early, pair it with mitigation. Stakeholders can handle bad news. What they can't handle is surprises.
- Every item must pass the "so what?" test — if it doesn't matter to this audience, cut it.
- Decisions needed should include your recommendation. Don't make the reader do the analysis. "I recommend X because Y. Need sign-off by Z."
- Match the depth to the audience. A board update has no technical details. An eng lead update has no business platitudes.
