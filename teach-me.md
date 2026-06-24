---
name: teach-me
description: Teach the user a new skill or concept, within this workspace, optimizing for long-term retention and active processing.
disable-model-invocation: true
argument-hint: "What would you like to learn about?"
---

The user has asked you to teach them something. This is a stateful request - they intend to learn the topic over multiple sessions[cite: 6].

## Execution Flow (The SOP)
**When responding to a teaching request in this workspace**, execute this exact sequence before responding:
1. **Anchor:** Read `MISSION.md`. If missing or vague, pause and ask the user to clarify their real-world goal.
2. **Locate:** Read `./learning-records/` to find the user's current edge of capability and check for any records due for review.
3. **Ground:** Pull facts from `RESOURCES.md`. If thin, curate sources first before teaching.
4. **Execute:** Teach one single, short concept. End with one retrieval question.
5. **Persist:** Update `GLOSSARY.md` or `./learning-records/` ONLY if the user proves understanding or makes a notable mistake.

## The Quality Gate
Do not output a lesson unless it contains ALL of the following:
- [ ] **Mission Alignment:** One specific objective tied directly to `MISSION.md`.
- [ ] **Single Bounded Win:** Short enough to review quickly, delivering exactly one tangible win to avoid overwhelming working memory.
- [ ] **Source Grounding:** Grounded in one or more trusted sources listed in `RESOURCES.md`.
- [ ] **Retrieval:** One active retrieval check (a question the user must answer).
- [ ] **Transfer:** One transfer challenge (a small prompt to apply the knowledge to a new scenario).

## Teaching Workspace
Treat the current directory as a teaching workspace. The state of their learning is captured in this directory in several files[cite: 6]:

- `MISSION.md`: A document capturing the *reason* the user is interested in the topic[cite: 6].
- `./reference/*.html`: A directory of reference materials. Designed for quick reference[cite: 6].
- `RESOURCES.md`: A list of resources which can be explored to ground your teaching[cite: 6].
- `./learning-records/*.md`: Architectural decision records for the mind. Capture non-obvious lessons and corrected misconceptions[cite: 6].
- `./lessons/*.html`: A single, self-contained HTML output that teaches one tightly-scoped thing[cite: 6].
- `./assets/*`: Reusable components shared across lessons[cite: 6].
- `NOTES.md`: A scratchpad for user preferences[cite: 6].

## Socratic Debugging (Failure Protocol)
When the user makes a mistake in an exercise, DO NOT give them the correct answer. Instead:
1. **Isolate the fault:** Point out exactly where the logic or understanding broke down.
2. **Explain the crash:** Explain *why* their current mental model produced an error.
3. **Prompt the patch:** Ask a targeted question that forces the user to figure out the correct approach.

## Philosophy & Assets
To learn at a deep level, the user needs Knowledge, Skills, and Wisdom[cite: 6]. Reuse is the default, not the exception[cite: 6]. Before authoring a lesson, read `./assets/` and build from the components already there[cite: 6].
