# Scoring Rubric

Background reference for `idea-validator`. Read before assigning any rating.

---

## 1. Problem Severity

Questions to answer:
- Is this a hair-on-fire problem or a nice-to-have?
- How often do users hit it? Daily is strong, yearly is weak.
- What does the status quo cost — time, money, frustration, risk?
- Would they pay to solve it today, or is it a "someday" problem?

| Rating | Bar |
|--------|-----|
| Strong | Users hit this daily or weekly AND it costs real time or money. They have built workarounds. |
| Moderate | Real problem, but low frequency, or high frequency with low pain. Users cope. |
| Weak | Nice-to-have. Users are not seeking solutions. No workarounds exist. |

## 2. Market Evidence

Questions to answer:
- Are people already paying for alternatives? How much?
- What search volume, forum posts, Reddit threads, or support tickets exist?
- Is the market growing or shrinking? What is the tailwind?
- Do adjacent markets validate the demand?

| Rating | Bar |
|--------|-----|
| Strong | Multiple competitors with revenue. Growing market. Demonstrated willingness to pay. |
| Moderate | Some competitors or adjacent products. Market exists, size unclear. |
| Weak | No competitors — usually bad, not good. No evidence of demand. |

## 3. Solution Differentiation

Questions to answer:
- Why would someone switch from their current solution?
- What is the unique angle — faster, cheaper, simpler, better for one segment?
- Is it defensible? Network effects, data moat, expertise, integrations?
- Can you state the difference in one sentence?

| Rating | Bar |
|--------|-----|
| Strong | Clear, defensible wedge. One sentence explains why this wins for a specific segment. |
| Moderate | Differentiation exists but may not be durable. "Better UX" alone caps here. |
| Weak | Me-too product. The difference requires explaining. "Like X but better." |

## 4. Feasibility

Questions to answer:
- Can a small team build an MVP in 4–6 weeks?
- What are the biggest technical risks?
- Does it need data, partnerships, or regulatory approval you do not have?
- What is the simplest version that delivers value?

| Rating | Bar |
|--------|-----|
| Strong | MVP buildable in weeks with existing tools and APIs. No special data or partnerships. |
| Moderate | Buildable, but requires one hard thing — a key integration, a dataset, a specific hire. |
| Weak | Requires multiple breakthroughs, regulatory approval, or years of data collection. |

## 5. Business Viability

Questions to answer:
- How does this make money?
- What is realistic willingness to pay, based on alternatives rather than hope?
- Rough CAC vs. LTV?
- Can it reach $1M ARR, and what does that require — X customers at $Y/month?

| Rating | Bar |
|--------|-----|
| Strong | Clear monetization. $1M ARR needs under 1,000 customers. Healthy unit economics. |
| Moderate | Monetization plausible but unproven. $1M ARR needs 5,000+ customers or pricing is unclear. |
| Weak | Monetization is "figure it out later," or it only works at massive scale. |

---

## Worked STOP verdict

This is the quality bar for a STOP. Note that it names the failing dimensions, cites a comparable, shows the math, and offers a direction.

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

A bad STOP, for contrast:

```
Verdict: STOP
This idea already has competitors so it might be hard to differentiate.
```

It never explains why. Worse, it treats competitors as a weakness when competitors are usually the strongest available proof of demand.

---

## Handling emotional attachment

If the user is clearly attached to the idea, acknowledge it in one sentence, then deliver the same analysis you would have delivered anyway. Do not trade accuracy for comfort. A user who ships a bad idea because you were encouraging loses months; a user who hears a hard STOP loses an afternoon.
