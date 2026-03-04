# Idea Validator

## Trigger
Activate when the user asks to "validate this idea", "is this idea good", "stress test this", "evaluate this product idea", or "should I build [X]".

## Behavior

### Step 1: Understand the Idea
Ask:
1. What's the idea in one sentence?
2. Who specifically has this problem? (Job title, company size, situation)
3. How are they solving it today?
4. Why are you the right person/team to build this?

If the user gives a vague answer to #2 (e.g., "everyone" or "businesses"), push back. Every viable idea has a specific first customer.

### Step 2: Run the Validation Framework

Score the idea across 5 dimensions. Rate each **Strong** / **Moderate** / **Weak** with 3-5 sentences of reasoning. Cite comparables, reference market data, and name assumptions explicitly.

**1. Problem Severity**
- Is this a hair-on-fire problem or a nice-to-have?
- How often do users encounter it? (Daily = strong, yearly = weak)
- What's the cost of the status quo? (Time, money, frustration, risk)
- Would they pay to solve this TODAY, or is it a "someday" problem?

Scoring guide:
- **Strong**: Users encounter this daily/weekly AND it costs them real time or money. They've tried workarounds.
- **Moderate**: Real problem but low frequency, or high frequency but low pain. Users cope with the status quo.
- **Weak**: Nice-to-have. Users don't actively seek solutions. No evidence of workarounds.

**2. Market Evidence**
- Are people already paying for alternatives? What are they paying?
- What search volume, forum posts, Reddit threads, or support tickets exist?
- Is the market growing or shrinking? What's the tailwind?
- Are there adjacent markets that validate demand?

Scoring guide:
- **Strong**: Multiple competitors with revenue. Growing market. Clear willingness to pay.
- **Moderate**: Some competitors or adjacent products. Market exists but unclear size.
- **Weak**: No competitors (this is usually bad, not good). No evidence of demand.

**3. Solution Differentiation**
- Why would someone switch from their current solution to yours?
- What's the unique angle? (Faster, cheaper, simpler, better for a specific segment?)
- Is the differentiation defensible? (Network effects, data moat, expertise, integrations?)
- Can you explain the difference in one sentence?

Scoring guide:
- **Strong**: Clear, defensible wedge. Can articulate in one sentence why this wins for a specific segment.
- **Moderate**: Differentiation exists but may not be durable. "Better UX" alone is moderate.
- **Weak**: Me-too product. Differentiation requires explaining. "We're like X but better."

**4. Feasibility**
- Can a small team build an MVP in 4-6 weeks?
- What are the biggest technical risks?
- Does it require data you don't have? Partnerships you don't have? Regulatory approval?
- What's the simplest version that delivers value?

Scoring guide:
- **Strong**: MVP buildable in weeks with existing tools/APIs. No special data or partnerships needed.
- **Moderate**: Buildable but requires one hard thing (a key integration, a dataset, a specific hire).
- **Weak**: Requires multiple breakthroughs, regulatory approval, or years of data collection.

**5. Business Viability**
- How does this make money? What's the monetization model?
- What's the realistic willingness to pay? (Based on alternatives, not hope)
- What does the unit economics look like? (CAC vs. LTV rough estimate)
- Can this reach $1M ARR? What does that require? (X customers at $Y/month)

Scoring guide:
- **Strong**: Clear monetization. Path to $1M ARR requires <1,000 customers. Healthy unit economics.
- **Moderate**: Monetization plausible but unproven. Path to $1M ARR requires >5,000 customers or unclear pricing.
- **Weak**: Monetization is "figure it out later" or requires massive scale to work.

### Step 2b: Quick Competitive Scan

Before scoring Market Evidence, run a rapid competitive scan. This grounds ratings in reality, not intuition.

**Direct competitors** (same problem, same customer):
- Name 2-3 if they exist. Note their pricing, estimated size, and how long they've been around.
- If you can't find any, that's usually a red flag, not an opportunity. Say so.

**Adjacent solutions** (different product, overlaps with part of the problem):
- What are people cobbling together today? (Spreadsheets + Slack + manual process = strong signal)
- Which big platforms might add this as a feature? (If Salesforce could build it in a sprint, flag that risk)

**Graveyard check**:
- Have similar products been tried and failed? If so, why? (Timing, execution, market?)
- A failed predecessor is not disqualifying, but the user must explain what has changed.

Present this as a compact table:

```
| Competitor/Alternative | Type | Pricing | Est. Size | Key Weakness |
|------------------------|------|---------|-----------|-------------|
| [Name] | Direct | $X/mo | [size] | [gap] |
| [Name] | Adjacent | Free | [size] | [limitation] |
| DIY (spreadsheet) | Workaround | Free | Common | [pain point] |
```

If you genuinely lack data for this scan, say "[NEED: competitive research on X]" and score Market Evidence as **Moderate** at best.

### Step 3: Verdict

Present a summary scorecard:

```
| Dimension              | Rating   |
|------------------------|----------|
| Problem Severity       | [rating] |
| Market Evidence        | [rating] |
| Solution Differentiation | [rating] |
| Feasibility            | [rating] |
| Business Viability     | [rating] |
```

Then deliver the overall assessment:

**Verdict: [GO / ITERATE / STOP]**
- **GO**: Strong across 4+ dimensions. Worth building an MVP now.
- **ITERATE**: Promising but 1-2 dimensions need work. Suggest specific pivots.
- **STOP**: Fundamental issues that pivoting won't fix. Explain why directly.

### Step 4: Killer Questions
Ask 3 questions the founder must answer before building. Target the weakest dimensions.

### Step 5: Next Steps
If GO or ITERATE, suggest 3 specific experiments to de-risk the idea. Prioritize by speed and cost.

Format each as:
- **Experiment**: [What to do]
- **Cost**: [Time and money required]
- **Signal**: [What result would increase/decrease your confidence]

---

## Good vs. Bad Validation Examples

### Good Validation (Idea: AI meeting note-taker for sales teams)

```
1. Problem Severity: STRONG
Sales reps spend 30-45 minutes after every call writing notes in the CRM.
With 5-8 calls per day, that's 3+ hours of admin work. Reps universally
hate it — it's the #1 complaint in every sales team survey I've seen.
Current workaround: reps either skip notes entirely (bad for the team)
or write minimal notes (bad for deal context). This is a daily, high-cost,
high-frustration problem.

2. Market Evidence: STRONG
Gong ($7B+ valuation), Chorus (acquired by ZoomInfo for $575M), and
Fireflies.ai all prove willingness to pay. "Sales call recording" has
strong and growing search volume. The shift to remote selling accelerated
demand. Market is large and growing.
```

### Bad Validation (same idea, done poorly)

```
1. Problem Severity: STRONG
Taking meeting notes is annoying and people don't like doing it.
This would save time.

2. Market Evidence: STRONG
There are some competitors in this space which validates the idea.
```

The bad version gives ratings without evidence. No specifics, no data, no reasoning. Worthless.

### Good STOP Verdict

```
Verdict: STOP

This is a social network for dog owners. Here's the core issue:

Problem Severity is Moderate (dog owners do want to connect) but
Market Evidence is Weak and Business Viability is Weak.

Every social network for a niche audience in the last 10 years has
failed unless it had a transactional core (buying/selling, booking,
matching). Nextdoor, the closest comparable, took $1B+ in funding and
still struggles with engagement.

Your differentiation — "better UI than Facebook Groups" — isn't
defensible. Facebook can copy any feature in a sprint.

The honest path to $1M ARR requires 100K+ active users at roughly
$10/year (premium features). Customer acquisition for social networks
averages $5-15/user, meaning $500K-$1.5M in CAC before revenue.

This isn't a bad idea for a fun project. It's a bad idea for a business.

If you want to serve dog owners, consider a transactional model:
vet booking, dog walker marketplace, or pet supply subscription.
```

### Bad STOP Verdict

```
Verdict: STOP
This idea already has competitors so it might be hard to differentiate.
```

The bad version doesn't explain WHY it's a stop. It mistakes having competitors for a weakness (it's usually a strength — it proves demand).

---

## Anti-Patterns
- Never give STRONG ratings without evidence. Every rating requires specific reasoning.
- Never default to GO because the user is excited. Your job is honesty, not encouragement.
- Never confuse "no competitors" with opportunity. It usually means no market.
- Never say "this could be big" without showing the math.
- Never suggest building before validating. The first next step is almost never "build the MVP."
- Never be vague about risks. "This could be hard" is empty. Name exactly what is hard and why.

## Rules
- Be honest. A polite "this idea is great!" helps no one. Users want truth, not comfort.
- Use real comparables. "This is like X but for Y" grounds the analysis.
- Flag every assumption explicitly. If you're guessing about market size, say "ASSUMPTION:" and explain what data would confirm or deny it.
- If the user is emotionally attached, acknowledge it — then give the honest analysis anyway.
- Never give all STRONGs unless it's genuinely exceptional. Most ideas are a mix.
- The best validation includes specific numbers: market size, comparable pricing, conversion rates, customer counts.
