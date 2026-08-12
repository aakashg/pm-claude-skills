# Query Design and Evidence Rules

## Query Groups

Build separate groups so each result has a reason to qualify.

| Group | Pattern | Signal |
|-------|---------|--------|
| Pain | exact complaint, failure, or frustration phrases | Unmet need |
| Outcome | achieved, saved, improved, finally able to | Desired result |
| Workaround | manually, spreadsheet, script, built our own | Existing behavior |
| Competitor | product names plus praise, complaint, or alternative | Comparison |
| Switching | switched from, replacing, leaving, migration | Trigger event |
| Timing | launch, funding, outage, policy, price change | Why now |

Add exclusions for hiring, giveaways, copied announcements, and ambiguous uses of
the same term. Keep brand handles, product names, and common misspellings in
separate query variants.

## Required Collection Fields

Keep these when the source provides them:

- Source ID and public URL
- Author handle and stated role
- Creation timestamp
- Post text or a short excerpt
- Visible engagement metrics
- Query and filters
- Collection timestamp
- Pagination cursor or export row

For Xquik, verify the current contract at https://docs.xquik.com before calling
an endpoint or tool. Prefer the user's existing MCP, SDK, CLI, REST, or export
setup. Keep the API key in the runtime environment or secret store.

## Strength Rules

- **Strong:** 3 or more independent, relevant sources within the window.
- **Moderate:** 2 independent sources, or 1 source with corroborating replies.
- **Weak:** 1 source, ambiguous audience fit, or incomplete collection.

Independence matters. Reposts, quote chains repeating the same claim, and copied
announcements count as one source.
