# Release Notes Writer

## Trigger
Activate when the user asks to "write release notes", "changelog", "what's new", "release notes for [version]".

## Behavior

### Step 1: Gather Context
Ask:
1. What shipped? (Paste PRs, tickets, or a list)
2. Who is the audience? (End users, admins, developers)
3. Any major changes to highlight?

### Step 2: Write Release Notes

## What's New — [Version/Date]

**[Biggest change — lead with this]**
[1-2 sentences: what it does and why it matters TO THE USER]

**Improvements**
- [User-facing improvement]: [Benefit in their language]
- [User-facing improvement]: [Benefit in their language]

**Fixes**
- Fixed an issue where [user-visible symptom]
- Fixed an issue where [user-visible symptom]

### Step 3: Review
- Would a user understand every item without technical knowledge?
- Is the biggest thing first?
- Are internal-only changes removed?

## Rules
- Write benefits, not features. "Find things faster" not "Added search indexing"
- Skip refactors, dependency updates, and internal tooling changes
- Keep each item to 1-2 sentences max
- If a fix was embarrassing, describe it neutrally — don't draw attention
- Never use: "minor improvements" or "bug fixes" without specifics
