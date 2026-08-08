# Cadence Variants

Background reference for `status-update-writer`. The default in SKILL.md is weekly. Switch formats when the user says daily, monthly, quarterly, or QBR.

---

## Daily standup / async daily

- 3 lines max: what shipped yesterday, what is happening today, blockers.
- Skip metrics, risks, and decisions unless something changed today.
- Plain text, no headers. It must fit in a Slack message.
- Target: under 40 words.

```
Yesterday: Shipped auth migration to 40% of web users
Today: Running load tests, expanding to 60% if results hold
Blocked: Waiting on QA sign-off from Maria (need by EOD)
```

---

## Weekly

The default. Full structure in SKILL.md. Target: under 200 words.

---

## Monthly

Same structure as weekly, zoomed out.

- Report against monthly goals, not daily tasks.
- Add **Month in Review**: 3–5 biggest accomplishments as a bulleted list.
- Metrics show trends, not snapshots: "WAU grew from 130K to 142K (+9%)."
- Add **Next Month Preview** with key milestones and dates.
- Target: 300–500 words.

---

## Quarterly business review (QBR)

- Lead with an **OKR scorecard**: each KR with target vs. actual and red/yellow/green.
- Add **Key Decisions Made**: what big bets were placed and their early results.
- Add **Lessons Learned**: 2–3 things you would change if you could rerun the quarter.
- Forward-looking section: next quarter's top 3 priorities with success criteria.
- Use tables for the OKR scorecard and metric summaries.
- Target: 500–800 words.

---

## Common mistakes across all cadences

**Hiding bad news at the bottom.** If the launch date slipped, that is the TL;DR, not a footnote. Stakeholders lose trust when they discover you buried the lead.

**Confusing activity with progress.** "Had 6 meetings about the migration" is activity. "Migrated 40% of users with 0.3% error rate" is progress. Report outcomes, not effort.

**Using weasel words.** "Roughly on track," "mostly done," "some concerns" signal uncertainty, not status. If something is unknown, write "investigating, will update by [date]."

**Including everything.** A status update is not a diary. Only include what matters to this audience at this altitude. Your VP does not need to know about a refactored utility function.

**No action items.** Every update must make clear what is needed from the reader. If nothing is needed, say so — but most "nothing needed" updates are missing something.

**Passive voice to avoid ownership.** "The deadline was missed" becomes "We missed the deadline because X. Here is the recovery plan."
