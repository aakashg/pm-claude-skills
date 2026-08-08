# Techniques

Background reference for `prompt-engineer`. Read before applying a technique.

---

## Role priming

Give the model a specific identity with relevant experience. Specificity drives output quality.

- Weak: "You are a helpful assistant"
- Better: "You are a senior product manager"
- Best: "You are a senior PM at a B2B SaaS company with 10 years of experience. You've shipped 20+ features and written 100+ PRDs. You're known for concise, metrics-driven specs."

Skip this entirely when the task is mechanical (reformatting, extraction). A role on a formatting task is decoration.

## Structured output

Define the exact format — fields, order, and length.

- Weak: "Summarize this article"
- Best: "Summarize this article in exactly 3 bullet points. Each bullet: one sentence, under 20 words, focused on actionable takeaways for a PM audience."

## Chain of thought

For multi-step reasoning only.

- "Think through this step by step before giving your final answer."
- "First, identify the key factors. Then analyze each one. Finally, synthesize into a recommendation."

Never add this to generative tasks. It makes a tweet worse.

## Few-shot examples

1–3 input/output pairs showing what good looks like. Include at least one edge case. One great example outweighs 50 words of instruction.

## Constraints (DO / DON'T)

Explicit rules prevent the most common failure modes.

- "DO: Use specific metrics. Cite the data I provided. Flag assumptions."
- "DON'T: Use jargon without defining it. Make up statistics. Exceed 500 words."

## Evaluation criteria

Have the model check its own output before responding.

- "Before responding, verify: (1) every recommendation has a supporting reason, (2) all metrics come from the data provided, (3) total length is under 300 words."

## Delimiter separation

Separate instructions from input data so the model does not read the data as instructions. Use triple backticks, XML tags, or explicit headers: `INSTRUCTIONS:` / `INPUT DATA:`.

---

## Worked example: weak few-shot → strong few-shot

**Before**
```
Rewrite these feature requests as user stories.

Feature requests:
- We need better search
- Users want dark mode
- Add CSV export
```

Problems: no format specified, no quality bar shown, no product context.

**After**
```
You are a PM turning raw feature requests into user stories for an engineering team.

For each request, produce:
- User story (As a [user type], I want [action] so that [outcome])
- Acceptance criteria (2-3 testable conditions)
- One edge case to consider

EXAMPLE:
Request: "Customers want to undo actions"
User story: As a document editor, I want to undo my last 10 actions so that I can experiment without fear of losing work.
Acceptance criteria:
- Cmd+Z undoes the most recent action within 200ms
- Undo stack preserves the last 10 actions per session
- Undo is disabled (greyed out) when no actions exist in the stack
Edge case: What happens if the user undoes a collaborative edit that another user has already built upon?

Now process these requests:
Product context: B2B project management tool for mid-market teams (50-200 people).

Feature requests:
- We need better search
- Users want dark mode
- Add CSV export
```

What changed:
- Few-shot example → shows the exact quality bar and format
- Product context → stories become specific to the real product
- Edge case requirement → forces thinking past the happy path
- Structured output → consistent format across all stories

---

## Worked example: over-engineered → right-sized

**Before**
```
You are an expert-level product management consultant with 20 years of
experience across consumer, enterprise, and marketplace products. You have
deep expertise in behavioral economics, jobs-to-be-done theory, the Kano
model, and design thinking. You have consulted for Fortune 500 companies
and high-growth startups alike. You approach every problem with a blend of
quantitative rigor and qualitative empathy. You always consider second-order
effects and systemic implications.

Please analyze the following customer feedback and provide a comprehensive
multi-dimensional assessment including but not limited to: sentiment analysis,
theme clustering, priority scoring using the RICE framework, impact mapping,
root cause analysis using the 5 Whys methodology, and strategic recommendations
aligned with OKR best practices.

[50 more lines of instructions...]
```

Problems: the prompt is longer than the output will be. The role is impossibly broad. It requests 8+ frameworks for one simple task, so the model produces mediocre output across all of them instead of strong output on the one that matters.

**After**
```
Analyze this customer feedback. Group by theme, rank by frequency, and flag the top 3 issues I should act on.

For each top issue:
- How many customers mentioned it
- Representative quote
- Suggested next step

Feedback:
[paste feedback here]
```

What changed:
- Removed the bloated role — unnecessary for this task
- Cut 8 frameworks to the one that matters (theme clustering + prioritization)
- Clear, scannable output format
- The prompt is now shorter than the expected output, which is the right ratio for analytical tasks

---

## Knowing when to split

If one prompt is doing 3+ distinct jobs, it needs to be a chain:

Prompt 1 analyzes → feeds Prompt 2 for synthesis → Prompt 3 formats the output.

Tell the user directly: "This prompt is overloaded. Here's how to split it into a 2-step chain that will produce better results." Then show both steps.

---

## Anti-patterns

- Never add complexity for its own sake.
- Never use "be thorough and comprehensive" — it produces verbose, unfocused output.
- Never assign a role that mismatches the task.
- Never add few-shot examples below the quality bar you expect back.
- Always test. Verify the improved prompt actually produces better output before declaring victory.
- Never override the user's intent. Improve how they ask, not what they ask for.
