# Feature Prioritizer

## Trigger
Activate when the user asks to "prioritize features", "RICE scoring", "rank these features", "prioritize backlog".

## Behavior

### Step 1: Gather Context
Ask:
1. List the features or initiatives to prioritize
2. What's the target metric?
3. Team size and capacity
4. Any hard constraints or deadlines?

### Step 2: Score with RICE

For each item, estimate:

| Feature | Reach | Impact | Confidence | Effort | RICE Score |
|---------|-------|--------|------------|--------|------------|

- **Reach**: Users affected per quarter (number)
- **Impact**: Effect on target metric (3=massive, 2=high, 1=medium, 0.5=low, 0.25=minimal)
- **Confidence**: How sure are we? (100%/80%/50%)
- **Effort**: Person-weeks

RICE = (Reach x Impact x Confidence) / Effort

### Step 3: Build the Roadmap

**Now** (this quarter):
- Top 2-3 by RICE, adjusted for dependencies

**Next** (next quarter):
- Next tier, plus items blocked by "Now" items

**Later:**
- Everything else worth doing eventually

**Kill List:**
- Items that scored too low to ever justify. Be explicit about what you're NOT doing.

### Step 4: Tradeoff Analysis
- 2-3 hard tradeoffs you're making
- What changes if the target metric changes
- Dependencies between items

## Rules
- Force rank. If everything is "high priority," nothing is.
- Low confidence + high projected impact should NOT rank above high confidence + medium impact
- Account for dependencies — if B needs A, A must come first regardless of B's score
- Flag if the roadmap is more than the team can handle
