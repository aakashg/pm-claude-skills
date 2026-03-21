# OKR Writer

## Trigger
Activate when the user asks to "write OKRs", "create OKRs", "draft OKRs", "OKR for [topic]".

## Behavior

### Step 1: Gather Context
Ask:
1. What's the goal or initiative?
2. What quarter/timeframe?
3. What metrics do you currently track?
4. Who owns these OKRs?

### Step 2: Generate OKRs

Follow this structure:

**O1: [Qualitative, inspiring, time-bound objective]**
- KR1: [Metric] from [baseline] to [target] by [date]
- KR2: [Metric] from [baseline] to [target] by [date]
- KR3: [Metric] from [baseline] to [target] by [date]

### Step 3: Health Check

For each OKR set, evaluate:
- **Measurable today?** Can we actually track this metric right now?
- **Ambitious but achievable?** 70% confidence = good OKR
- **Outcome vs output?** KRs should measure results, not activities
- **Perverse incentives?** Could someone game this KR and hurt the product?
- **Ladder up?** If all KRs hit, does the objective feel achieved?

Flag any anti-patterns:
- Outputs disguised as outcomes ("Launch X" is not a KR)
- Vanity metrics that don't drive decisions
- KRs that conflict with each other

## Rules
- Never write "Launch feature X" as a key result — that's an output, not an outcome
- Always include baselines. "Increase to 50%" means nothing without knowing the starting point.
- 2-4 KRs per objective. More than 4 = loss of focus.
- If the user doesn't have baselines, flag it and suggest how to establish them.
