# Screen-Type Checklists

Background reference for `product-designer`. Apply only the section matching the screen under review.

---

## Forms

- Are required fields marked? Is the marker consistent — asterisk vs. "required" label?
- Do inputs have the right type (email, tel, number)? This changes the mobile keyboard.
- Is the tab order logical?
- Are placeholders being used as the only label? They disappear on focus — that is a defect, not a style choice.
- Is validation immediate or on submit? Is that consistent across fields?

## Tables and data views

- Can users sort and filter? Is the current sort state visible?
- How does it handle 0 results? 1 result? 10,000 results?
- Are row actions discoverable? Hover menus are invisible on touch devices.
- Is there a clear path to act on selected items?
- Does column content truncate gracefully or break the layout?

## Onboarding and wizards

- Can users skip steps? Should they be able to?
- Is progress visible? Can they go back?
- Does each step have one clear purpose?
- What happens if they abandon mid-flow and return later?

## Settings and preferences

- Are changes saved automatically or on submit? Is that obvious?
- Are destructive actions (delete, revoke, disconnect) visually distinct from safe ones?
- Is there a way to reset to defaults?
- Are dependent settings shown as dependent, or can the user create an impossible combination?

## Modals and dialogs

- Is there a clear way to close — both an X and click-outside?
- Does the modal size match the content? A full-screen modal for a yes/no question is a mismatch.
- Can the user still see the context they came from?
- Does it trap focus for keyboard users?

## Dashboards

- Do all KPI cards have equal visual weight? If so, the user has no entry point. Apply the squint test: blur the screen — the most important number should still be the first thing you notice.
- Are any charts showing overlapping data (daily / weekly / monthly users as three separate charts)? Redundant visualizations increase cognitive load and force the reader to mentally diff them.
- Is the date range control where users expect it, usually top-right?
- What does the dashboard look like on day one, with no data?

---

## Worked example: dashboard review

Bad feedback:

```
The dashboard has too much information. Simplify it.
```

Good feedback:

```
What works:
- The date range picker in the top-right is well-placed and follows convention
- KPI cards at the top give a quick snapshot

Must Fix:

1. All 8 KPI cards have equal visual weight
   WHY: When everything is emphasized, nothing is. The user's eye has no
   entry point. They don't know which number matters most.
   FIX: Make the primary metric (e.g., revenue) 2x the size of secondary
   metrics. Group the others in a row below. Apply the "squint test" — if you
   blur the screen, the most important number should still be the first thing
   you notice.

Should Fix:

2. Three charts show overlapping data (daily users, weekly users, monthly users)
   WHY: Redundant visualizations waste space and increase cognitive load.
   The user has to mentally diff the charts to extract insight.
   FIX: One chart with a toggle (daily / weekly / monthly). Or one chart
   showing the primary timeframe with a sparkline trend for the others.
```
