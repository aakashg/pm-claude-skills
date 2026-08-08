# AI UX Review

Background reference for `product-designer`. Run these checks in addition to the 6 core dimensions whenever the design includes AI features — chatbots, generated content, smart suggestions, copilots, autocomplete.

AI UX has distinct failure modes that traditional heuristics miss entirely.

---

## Setting expectations

- Does the UI communicate what the AI can and cannot do? Scope framing prevents disappointment.
- Is AI-generated output clearly labeled as such? Users need to know when to verify.
- Does the UI set the right confidence level? Avoid both "this is definitely correct" and "this might be totally wrong."

## Handling uncertainty

- How does the UI show confidence? High-confidence results should look different from low-confidence guesses.
- Can users see *why* the AI made a recommendation? Even a one-line explanation reduces distrust materially.
- What happens when the AI does not know? "I'm not sure" beats a confident wrong answer.

## Loading and latency

- AI responses often take 2–10 seconds. Is there streaming or progressive display?
- Does the loading state indicate the AI is thinking, or is it a generic spinner? Typing indicators and progress text set better expectations.
- Can the user cancel a slow request without losing their input?

## Errors and edge cases

- What happens when the AI produces garbage? Is there a clear "try again" or "report bad output" path?
- Can users edit AI output before it is applied? Never auto-apply AI suggestions to user data without confirmation.
- Does the UI degrade gracefully at rate limits or when the AI service is down?

## Human-AI loop

- Can users give feedback on output — thumbs, edit, regenerate?
- Does the system improve from corrections? If so, is that communicated?
- Is there always a manual fallback? Users should never be blocked because the AI failed.

---

## Escalation rule

Flag an AI UX issue as **Must Fix** — not Should Fix — when any of these are true:

1. AI output is auto-applied to user data without review.
2. There is no recovery path from bad AI output.
3. Confidence signals are misleading, meaning a low-confidence guess is presented with the same visual weight as a verified fact.

These three cause data loss or misplaced trust, which are launch blockers regardless of how polished the rest of the screen is.
