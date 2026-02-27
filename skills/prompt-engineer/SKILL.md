# Prompt Engineer

## Trigger
Activate when the user asks to "improve this prompt", "make this prompt better", "optimize this prompt", "prompt engineer this", or "rewrite this prompt".

## Behavior

### Step 1: Analyze the Current Prompt
Read the user's prompt and identify issues:
- Missing context or role definition
- Vague instructions that allow too much interpretation
- No output format specified
- No examples provided
- Missing edge case handling
- No quality criteria

### Step 2: Apply Techniques

Improve the prompt using these evidence-based techniques, applying whichever are relevant:

**Role Priming**
- Add a specific role: "You are a [specific expert] with [specific experience]"
- Make it relevant to the task, not generic

**Structured Output**
- Define the exact format you want back (headers, bullet points, tables)
- Include field names and expected content for each

**Chain of Thought**
- For complex reasoning: "Think through this step by step"
- Break multi-part tasks into numbered steps

**Few-Shot Examples**
- Add 1-3 input/output examples showing what good looks like
- Include one edge case example

**Constraints**
- Add explicit rules: word limits, things to include/exclude, tone
- Add anti-patterns: "Do NOT [common mistake]"

**Evaluation Criteria**
- Tell the LLM how to judge its own output
- "Before responding, verify that your answer includes X, Y, Z"

### Step 3: Show the Improvement

Present the improved prompt in a code block. Then add a brief section:

**What changed and why:**
- [Technique applied] → [what it fixes]
- [Technique applied] → [what it fixes]

### Step 4: Offer to Iterate
"Want me to add examples, adjust the tone, or tune it for a specific LLM?"

## Rules
- Show before and after — the user should see what changed
- Explain WHY each change helps, not just what you changed
- Don't over-engineer. A 50-line prompt isn't always better than a 10-line one.
- Preserve the user's intent. Improve the prompt, don't rewrite the task.
