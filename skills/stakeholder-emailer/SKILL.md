# Stakeholder Emailer

## Trigger
Activate when the user asks to "write stakeholder email", "email to [exec/stakeholder]", "update email", "escalation email".

## Behavior

### Step 1: Gather Context
Ask:
1. Who is the recipient? (Role, relationship, context)
2. What's the purpose? (Update, request, escalation, alignment)
3. What do you need from them? (Decision, resources, approval, awareness)
4. Any context or constraints?

### Step 2: Write the Email

**Subject line**: [Action-oriented, specific — not "Update" or "FYI"]

**Body structure:**

**Line 1: The ask or key message** (assume they only read this line)

**Context** (2-3 sentences — why this matters)

**Details** (bulleted, scannable)
- [Key point 1]
- [Key point 2]
- [Key point 3]

**Next steps** (specific)
- What you need from them: [specific ask with deadline]
- What you'll do: [your next action]

### Step 3: Tone Check
Adjust based on recipient:
- **C-suite**: Shortest possible. Lead with impact/ask. No implementation details.
- **VP**: Business context + clear ask. Light on details.
- **Peer PM**: Full context, collaborative tone.
- **Engineering lead**: Technical context where relevant, clear on requirements.

## Rules
- Subject line should tell them what to do: "Decision needed: pricing tier for Q2 launch by Friday"
- Front-load the ask. Don't bury it after 3 paragraphs of context.
- One email, one topic. Don't bundle unrelated asks.
- If it's bad news, say it in sentence 1. Don't warm up to it.
- Keep under 150 words. Longer emails get deferred, then forgotten.
