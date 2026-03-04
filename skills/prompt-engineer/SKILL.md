# Prompt Engineer

## Trigger
Activate when the user asks to "improve this prompt", "make this prompt better", "optimize this prompt", "prompt engineer this", or "rewrite this prompt".

## Behavior

### Step 1: Analyze the Current Prompt

Read the user's prompt and diagnose issues across these dimensions:

| Dimension | What to Check |
|-----------|--------------|
| **Role** | Is there a specific role/persona? Generic "you are an expert" doesn't count. |
| **Context** | Does the LLM have enough background to do the task well? |
| **Instructions** | Are steps explicit and ordered? Or vague and open to interpretation? |
| **Output format** | Is the expected structure defined? (Headers, bullets, length, tone) |
| **Examples** | Are there input/output pairs showing what "good" looks like? |
| **Constraints** | Are there explicit DO/DON'T rules? Edge cases handled? |
| **Evaluation** | Can the LLM self-check its output against clear criteria? |

### Step 2: Apply Techniques

Apply the relevant techniques below. Match the technique to the problem — not every prompt needs every technique.

**Role Priming**
Give the LLM a specific identity with relevant experience. Specificity drives output quality.
- Weak: "You are a helpful assistant"
- Better: "You are a senior product manager"
- Best: "You are a senior PM at a B2B SaaS company with 10 years of experience. You've shipped 20+ features and written 100+ PRDs. You're known for concise, metrics-driven specs."

**Structured Output**
Define the exact format. Specify fields, order, and length — never just "give me a summary."
- Weak: "Summarize this article"
- Best: "Summarize this article in exactly 3 bullet points. Each bullet: one sentence, under 20 words, focused on actionable takeaways for a PM audience."

**Chain of Thought**
For complex reasoning, force the LLM to show its work. This dramatically improves accuracy on multi-step problems:
- Add: "Think through this step by step before giving your final answer."
- Or: "First, identify the key factors. Then, analyze each one. Finally, synthesize into a recommendation."

**Few-Shot Examples**
Add 1-3 input/output pairs showing what good looks like. Include at least one edge case.
- Examples must demonstrate the quality bar, format, and tone expected.
- One great example outweighs 50 words of instruction.

**Constraints (DO/DON'T)**
Explicit rules prevent the most common failure modes:
- "DO: Use specific metrics. Cite the data I provided. Flag assumptions."
- "DON'T: Use jargon without defining it. Make up statistics. Exceed 500 words."

**Evaluation Criteria**
Direct the LLM to verify its own output before responding.
- "Before responding, verify: (1) every recommendation has a supporting reason, (2) all metrics are from the data provided, (3) the total length is under 300 words."

**Delimiter Separation**
Use clear delimiters to separate instructions from input data. This prevents the LLM from confusing instructions with content it should process.
- Use triple backticks, XML tags, or clear headers: "INPUT DATA:" / "INSTRUCTIONS:"

### Step 3: Show the Improvement

Present the improved prompt in a code block. Then add:

**What changed and why:**
- [Technique] → [what problem it fixes]
- [Technique] → [what problem it fixes]

### Step 4: Offer to Iterate
"Want me to add examples, adjust the tone, tune it for a specific LLM, or make it shorter?"

---

## Full Before/After Examples

### Example 1: Vague Prompt → Specific Prompt

**Before:**
```
Write a competitive analysis of Notion.
```

Problems: No role, no structure, no audience, no scope, no output format. The LLM will produce a generic, rambling overview:

**After:**
```
You are a senior product strategist at a B2B knowledge management company competing with Notion.

Analyze Notion's AI features specifically. Structure your analysis as:

1. WHAT THEY BUILT
- Core AI features (list each with one-line description)
- Target user for each feature
- Pricing model for AI features

2. WHAT'S SMART (3 product decisions)
- For each: what they did, why it works, evidence

3. WHAT'S WEAK (3 gaps or friction points)
- For each: the issue, who it affects, opportunity for us

4. IMPLICATIONS
- 2 things we should copy and why
- 2 things we should avoid and why
- 1 opportunity they're missing that we could own

Rules:
- Be specific. "Good UX" is not analysis. Name the interaction and explain why it works.
- If you don't have data, say "[NEED: data on X]" instead of guessing.
- Keep total output under 800 words.
```

**What changed:**
- Role priming → LLM writes from a strategic perspective, not generic
- Structured output → Ensures consistent, complete analysis
- Constraints → Prevents vague filler and controls length
- Scope → "AI features specifically" prevents a surface-level overview of everything

### Example 2: Weak Few-Shot → Strong Few-Shot

**Before:**
```
Rewrite these feature requests as user stories.

Feature requests:
- We need better search
- Users want dark mode
- Add CSV export
```

Problems: No format specified, no quality bar shown, no context about the product.

**After:**
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

**What changed:**
- Few-shot example → Shows the exact quality bar and format expected
- Product context → User stories will be specific to the actual product
- Edge case requirement → Forces the LLM to think beyond the happy path
- Structured output → Consistent format across all stories

### Example 3: Over-Engineered → Right-Sized

**Before (too complex):**
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

Problems: Prompt is longer than the output. Role is impossibly broad. Instructions request 8+ frameworks for a simple task. The LLM will produce mediocre output across all dimensions instead of strong output on what actually matters.

**After (right-sized):**
```
Analyze this customer feedback. Group by theme, rank by frequency, and flag the top 3 issues I should act on.

For each top issue:
- How many customers mentioned it
- Representative quote
- Suggested next step

Feedback:
[paste feedback here]
```

**What changed:**
- Removed bloated role (unnecessary for this task)
- Cut 8 frameworks down to the one that matters (theme clustering + prioritization)
- Clear, scannable output format
- The prompt is shorter than the expected output, which is almost always the right ratio for analytical tasks

---

## Prompt Debugging

When the improved prompt still produces bad output, stop rewriting. Diagnose the failure mode first, then apply the targeted fix.

**Step 1: Identify the failure type**

| Symptom | Likely Cause | Fix |
|---------|-------------|-----|
| Output is too generic / "could be anyone" | Missing role or weak context | Add a specific persona with domain details |
| Output misses the point entirely | Prompt is ambiguous — LLM chose a valid but wrong interpretation | Add a "Your goal is..." preamble and one clarifying example |
| Output is right but wrong format | No output spec, or output spec is buried | Move format instructions to the top, use a template |
| Output is verbose and padded | No length constraints or "be thorough" is in the prompt | Add explicit word/sentence limits. Replace "thorough" with "cover X, Y, Z" |
| Output hallucinates facts | No grounding instructions | Add "Only use information from the provided context. If data is missing, say [NEED: X]" |
| Output starts strong, degrades at the end | Prompt is too long — LLM loses focus | Shorten the prompt. Move examples before instructions. Cut redundant sections. |
| Output ignores some instructions | Too many competing instructions | Reduce to 3-5 core rules. Number them. Add "These rules are mandatory." |

**Step 2: Test the fix**

After diagnosing and fixing, tell the user:
- "Here's what I changed and why"
- "Test it with [this specific input] to verify the fix"
- "If it still fails, the next thing to try is [fallback approach]"

**Step 3: Know when to split**

If a single prompt is trying to do 3+ distinct things, it probably needs to be a chain:
- Prompt 1 does analysis → feeds into Prompt 2 for synthesis → Prompt 3 formats the output
- Tell the user: "This prompt is overloaded. Here's how to split it into a 2-step chain that will produce better results."

---

## Anti-Patterns
- Never add complexity for its own sake. A 10-line prompt that works beats a 50-line prompt that confuses.
- Never use "be thorough and comprehensive" — it produces verbose, unfocused output. Specify exactly what to cover.
- Never assign a role that mismatches the task. "You are a world-class neurosurgeon" adds nothing to a marketing brief.
- Never add few-shot examples below the quality bar you expect back. Bad examples teach bad patterns.
- Always test. Run the improved prompt to verify it actually produces better output.
- Never override the user's intent. Improve HOW they ask, not WHAT they are asking for.

## Rules
- Always show before and after. The user must see what changed and why.
- Explain each change in terms of the problem it solves, not just the technique name.
- Preserve the user's intent. Improve the prompt, not the task.
- Right-size the improvement. Simple tasks need simple prompts. Never add chain-of-thought to "write a tweet."
- When in doubt, add one great example rather than more instructions. Examples teach faster than rules.
