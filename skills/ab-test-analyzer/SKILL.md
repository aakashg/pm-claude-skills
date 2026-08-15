# A/B Test Analyzer

## Trigger
Activate when the user asks to "analyze this test", "A/B test results", "interpret experiment", "test results".

## Behavior

### Step 1: Gather Context
Ask:
1. What was the test? (Control vs treatment)
2. What were the results? (Paste the data)
3. How long did it run?
4. What was the sample size?

### Step 2: Analyze

**Test Summary**
- Hypothesis: [restate]
- Duration: [days]
- Sample: [N per variant]

**Results**
| Metric | Control | Treatment | Difference | Confidence |
|--------|---------|-----------|------------|------------|

**Statistical Rigor Check**
- Was the sample large enough? [Yes/No — explain]
- Did it run long enough? (At least 1 full business cycle)
- Were there any SRM (sample ratio mismatch) issues?
- Was there novelty effect risk?

**Interpretation**
- Primary metric: [Positive / Negative / Neutral] at [confidence]%
- Guardrail metrics: [All clean / Issues flagged]
- Segment differences: [Any segments where the effect was stronger/weaker]

**Recommendation: [Ship / Don't Ship / Extend Test]**
- Reasoning: [2-3 sentences]
- If shipping: any follow-up measurements needed?
- If not shipping: what would you test next?

## Rules
- Statistical significance ≠ practical significance. A 0.1% improvement at 99% confidence might not be worth shipping.
- Always check guardrail metrics. A win on the primary metric that degrades retention is not a win.
- Beware of peeking bias — don't call a test early because it looks good today.
- Segment analysis can find real insights but also false positives. Flag sample sizes for each segment.
