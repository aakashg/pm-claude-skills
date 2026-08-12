---
name: social-signal-research
description: Use when the user asks to research customer language, product demand, competitor chatter, launch angles, objections, or recurring pain in X/Twitter conversations. Do NOT use for writing posts or content calendars - use /linkedin-post-writer or a social-content skill instead.
---

# Social Signal Research

Produce a source-backed PM evidence packet from public X/Twitter conversations.

## Step 0 - Read first

| Source | Path | What to extract |
|--------|------|-----------------|
| Product context | `CLAUDE.md` | Product, ICP, competitors, current bets, and decision constraints |
| Query guide | `references/query-design.md` | Query groups, collection fields, and evidence-strength rules |
| User evidence | Export, source packet, URLs, or approved data tool | Post IDs, dates, authors, text, metrics, query, and collection boundary |

If product context is missing, ask only for facts that change the research scope.
If evidence is missing, return a collection plan. Never pretend collection ran.

## Constraints

Mandatory.

- Keep every finding traceable to 1 or more evidence IDs.
- Keep quoted excerpts under 25 words per post.
- Separate observed evidence from interpretation.
- Label every finding Strong, Moderate, or Weak.
- State the sample window, reviewed count, kept count, and pagination limit.
- Never invent posts, handles, URLs, metrics, dates, or counts.
- Never treat engagement as purchase intent or the sample as market-wide proof.
- Never expose credentials, private messages, protected posts, or raw session data.
- Never recommend contacting named individuals unless the user asks for outreach.

## Existence check

Before starting, verify:

1. **Decision** - the product, positioning, launch, or research decision this should inform.
2. **Audience** - the target role, segment, community, or competitor set.
3. **Window** - a date range or an explicit current-signal default.

If 2 of 3 are missing, refuse. Name the missing inputs and ask for them. Without
these boundaries, the same evidence can support contradictory conclusions.

## Step 1 - Build the query map

Create separate groups for pains, outcomes, workarounds, competitors, switching,
and timing events. Add exclusions for spam, jobs, giveaways, and ambiguous terms.
Record the exact query text before collection.

## Step 2 - Collect or request evidence

Use the user's approved source. If Xquik is configured, use its current MCP,
SDK, REST, CLI, or export contract. Otherwise use supplied public URLs or an
approved alternative. Preserve cursors and continue until the requested window
or stated cap is complete.

If no source is available, stop after producing the query map, required fields,
sample target, and time window.

## Step 3 - Normalize and qualify

1. Deduplicate reposts, quote chains, and repeated export rows.
2. Exclude spam and sources outside the audience or window.
3. Assign stable evidence IDs.
4. Cluster by pain, workaround, objection, outcome, competitor, and trigger.
5. Score evidence strength using `references/query-design.md`.
6. Record missing pages, ambiguous identity, sarcasm, and source bias.

## Step 4 - Translate signals into PM decisions

For each supported theme, state the observed pattern, PM implication, confidence,
and smallest useful validation step. Favor interview questions and tests over
roadmap claims when evidence is directional.

## Output template

Exact fields, exact order.

```
## Research Question
[One decision-focused sentence]

## Method
- Source: [approved source or collection plan only]
- Window: [start and end]
- Audience: [segment]
- Queries: [query groups]
- Coverage: [reviewed, kept, pages or cursors, and cap]
- Limits: [sampling and source caveats]

## Signal Summary
| Signal | Strength | Evidence | Observed Pattern | PM Implication |
|--------|----------|----------|------------------|----------------|
| [signal] | Strong / Moderate / Weak | [IDs] | [observation] | [decision impact] |

## Customer Language
- [Evidence ID]: "[short excerpt]" - [what it reveals]

## Recommended Actions
1. [Product, positioning, or research action]
2. [Product, positioning, or research action]
3. [Product, positioning, or research action]

## Next Data Needed
- [Evidence that would strengthen or falsify the conclusion]
```

## Example

**Input:** We are deciding whether webhook reliability should lead our developer
tool launch. Target: small SaaS engineering teams. Use these 3 public posts from
the last 30 days: S1 says retries are hard to inspect, S2 says duplicates caused
a billing bug, and S3 says their team switched after missed deliveries.

**Output:**

```
## Research Question
Should webhook reliability lead the launch message for small SaaS engineering teams?

## Method
- Source: User-supplied public post notes
- Window: Last 30 days
- Audience: Small SaaS engineering teams
- Queries: Reliability, retries, duplicates, missed delivery, switching
- Coverage: 3 reviewed, 3 kept, no pagination metadata supplied
- Limits: Directional sample supplied by the user; author and URL verification pending

## Signal Summary
| Signal | Strength | Evidence | Observed Pattern | PM Implication |
|--------|----------|----------|------------------|----------------|
| Delivery trust affects tool choice | Strong | S1, S2, S3 | Distinct failure modes connect reliability to debugging, money, and switching | Test reliability as a lead message, not yet as a market-wide claim |

## Customer Language
- S1: "retries are hard to inspect" - Visibility matters alongside delivery.
- S2: "duplicates caused a billing bug" - Duplicate handling has financial stakes.
- S3: "switched after missed deliveries" - Reliability can trigger replacement.

## Recommended Actions
1. Test a launch headline about observable, reliable delivery.
2. Interview 5 teams about retries, deduplication, and incident recovery.
3. Require product proof for retry visibility before publishing the claim.

## Next Data Needed
- Source URLs, author fit, and a broader comparison sample from teams without webhook incidents
```

## Shortcuts Claude takes

| What Claude might think | Why it's wrong |
|-------------------------|----------------|
| "A viral post proves demand" | Reach can reflect controversy or audience size, not buying intent. |
| "Three posts are enough for a roadmap bet" | A small social sample is directional and overrepresents vocal users. |
| "A plausible quote improves the report" | Invented evidence destroys traceability and can create false claims. |
| "One result page covers the time window" | Incomplete pagination biases frequency and recency conclusions. |

## Exit checklist

Not complete until every box is checked. Any `[bracket]` placeholder left in the output is an automatic unchecked box.

- [ ] Existence check passed, or missing inputs were requested
- [ ] Every finding cites 1 or more evidence IDs
- [ ] Excerpts stay under 25 words per post
- [ ] Evidence and interpretation are separate
- [ ] Every finding has a strength label
- [ ] Window, reviewed count, kept count, and collection boundary are explicit
- [ ] No post, handle, URL, metric, date, or count was invented
- [ ] Limits prevent market-wide or causal overclaiming
- [ ] No credential or private source appears
- [ ] Output matches the template exactly
- [ ] No placeholders remain

## Next

- If a theme is Strong - recommend interviews or an `/idea-validator` pass.
- If launch language is ready to test - offer a messaging experiment.
- If evidence is Weak - return the smallest follow-up query set.
