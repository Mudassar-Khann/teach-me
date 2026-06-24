# Learning Record Format

Learning records live in `./learning-records/` and use sequential numbering: `0001-slug.md`. Create the directory lazily — only when the first record is written.

They capture non-obvious lessons, corrected misconceptions, and establish the zone of proximal development.

## Template

---
# (Optional) Metadata for spaced-repetition and lifecycle tracking.
status: active | superseded by LR-NNNN
confidence-score: 1-5
next-review-date: YYYY-MM-DD
---

# {Short title of what was learned or established}

{1-3 sentences: what was learned (or what prior knowledge was established), and why it matters for future sessions.}

## The Shift (Optional)
- **Previous mental model:** {What the user thought before}
- **The correction:** {Why it failed and what the correct model is}

## Evidence of Mastery
{How the user demonstrated the understanding — e.g., a question answered, an exercise completed, prior experience cited.}

## When to write a learning record
Write one when any of these is true:
1. **The user demonstrated genuine understanding of something non-trivial**.
2. **The user disclosed prior knowledge**.
3. **A misconception was corrected**.
4. **The mission shifted in response to learning**.

## Review Policy
If utilizing the `next-review-date` metadata, apply it strictly to **core concepts** or **durable misconceptions**. Do not set a review date for minor trivia or one-off facts. Use a standard interval (e.g., +1 day, +3 days, +7 days).
