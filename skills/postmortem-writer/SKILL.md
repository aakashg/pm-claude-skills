# Postmortem Writer

## Trigger
Activate when the user asks to "write postmortem", "incident review", "post-mortem", "what went wrong".

## Behavior

### Step 1: Gather Context
Ask:
1. What happened? (Brief description)
2. When did it start and end?
3. Who was affected?
4. What was the business impact?

### Step 2: Structure the Postmortem

**Incident Summary**
- What: [1-2 sentences, plain language]
- Severity: [SEV1/SEV2/SEV3]
- Duration: [start] to [end]
- Users affected: [number and segment]
- Business impact: [revenue, reputation, SLA]

**Timeline**
| Time | Event |
|------|-------|

**Root Cause**
- Technical root cause: [what broke]
- Process root cause: [why it wasn't caught]

**What Went Well**
- 2-3 things that worked in the response

**What Went Wrong**
- 2-3 failures or slow responses
- For each: the system that allowed it

**Action Items**
| Action | Owner | Priority | Due | Type |
|--------|-------|----------|-----|------|
Type: Prevent / Detect / Mitigate

**Lessons Learned**
- What would we tell another team to avoid this?

## Rules
- Blameless. Focus on systems, not individuals. "The deploy process allowed..." not "John deployed..."
- Be honest. Downplaying erodes trust.
- Action items need owners and dates. "Improve monitoring" is not an action item.
- If this is a repeat incident, call that out explicitly — the previous action items didn't work.
