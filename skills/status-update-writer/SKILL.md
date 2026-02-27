# Status Update Writer

## Trigger
Activate when the user asks to "write a status update", "weekly update", "stakeholder update", "write a project update", or "status report".

## Behavior

### Step 1: Gather Context
Ask:
1. What project or initiative is this for?
2. What happened this week? (Paste notes, Slack messages, whatever you have)
3. Who is the audience? (CEO, VP Eng, cross-functional team, etc.)

If the user pastes raw notes or Slack threads, extract the relevant information yourself.

### Step 2: Write the Update

**TL;DR** (2 sentences max)
The update if they read nothing else. Lead with the most important thing.

**Status: [pick one]**
- 🟢 On Track — shipping on schedule, no blockers
- 🟡 At Risk — potential issues that could delay, with mitigation
- 🔴 Blocked — cannot proceed without help, state what's needed

**Shipped This Week**
- Bullet points. Specific. What shipped, not what was "worked on."
- Include links to PRs, docs, or demos if the user provides them.

**Next Week**
- What's planned. Include owners if known.
- Highlight any dependencies.

**Risks & Blockers**
- Every risk gets a mitigation plan
- Every blocker gets a next step and owner
- If there are none, say "None" — don't fabricate risks

**Decisions Needed** (only if applicable)
- State exactly what you need decided, by whom, by when
- Provide enough context for the reader to decide without a meeting

### Formatting Rules
- Under 200 words total. Executives don't read long updates.
- No filler. "We continued to make progress on..." → just say what shipped.
- Bad news goes above the fold, not buried at the bottom.
- Active voice. "Team shipped X" not "X was shipped by the team."

### Step 3: Tone Check
Adjust tone based on audience:
- **Executive (C-suite):** Outcomes and metrics. No implementation details.
- **Cross-functional:** Context and dependencies. What other teams need to know.
- **Engineering lead:** Technical details, blockers, architecture decisions.

## Rules
- Never fabricate progress. If the user's notes are thin, the update should be thin.
- Never hide bad news. Surface it early with a plan.
- Every item should pass the "so what?" test — if it doesn't matter to the reader, cut it.
