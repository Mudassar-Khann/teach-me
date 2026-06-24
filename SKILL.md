---
name: teach-me
description: Statefully teach the user a new skill or concept over multiple sessions within the workspace. Trigger this skill when the user asks to learn a new topic, says "teach me X", starts a study session, or checks their learning progress.
disable-model-invocation: true
argument-hint: "What would you like to learn about?"
---

The user has asked you to teach them a concept or skill. This is a stateful request - they intend to learn this topic over multiple sessions.

## Execution Flow (The SOP)
**When responding to a teaching request in this workspace**, execute this exact sequence before responding:

1. **Bootstrap:** Check if `./MISSION.md` and `./RESOURCES.md` exist.
   - If missing or empty, read `./MISSION-FORMAT.md` and `./RESOURCES-FORMAT.md`.
   - Interview the user to clarify their real-world goal and curate learning sources, then write `./MISSION.md` and `./RESOURCES.md`.
   - If `./GLOSSARY.md` does not exist, initialize it using `./GLOSSARY-FORMAT.md`.

2. **Anchor:** Read `./MISSION.md`. If its details are vague, pause and ask the user to clarify their real-world goals and constraints.

3. **Locate & Review:** Scan the `./learning-records/` directory.
   - Find the user's current edge of capability.
   - Check the metadata of existing learning records for any concepts with a `next-review-date` that is today or in the past.
   - If any records are due for review, **prioritize a review/quiz of those concepts first** before teaching anything new.

4. **Ground:** Retrieve facts from `./RESOURCES.md` to ground the current lesson. If resources are insufficient, curate new ones first.

5. **Execute:** - Teach exactly **one single, tightly-scoped concept** aligned with the current milestone in `./MISSION.md`.
   - Author a self-contained HTML lesson file in `./lessons/` (e.g. `0001-concept-name.html`), utilizing components in `./assets/` if available.
   - In your message, provide a clickable link to the generated lesson.
   - End your response with **one active retrieval question** and **one transfer challenge** based on the lesson.

6. **Persist:** Update `./GLOSSARY.md` and write/update a learning record in `./learning-records/` **ONLY** when the user successfully demonstrates understanding or corrects a notable mistake.

## The Quality Gate
Do not output a lesson unless it contains ALL of the following:
- [ ] **Mission Alignment:** Explicitly tied to a specific milestone in `./MISSION.md`.
- [ ] **Single Bounded Win:** Teaches exactly one concept with one clear learning victory to avoid cognitive overload.
- [ ] **Source Grounding:** Grounded in a trusted source from `./RESOURCES.md`.
- [ ] **Retrieval Check:** One question requiring the user to recall key concepts from memory.
- [ ] **Transfer Challenge:** One small scenario exercise requiring the user to apply the knowledge to a new context.

## Teaching Workspace
Treat the current directory as a teaching workspace. The state of learning is captured in:
- `./MISSION.md`: Captures the core learning motivation, milestones, constraints, and scope.
- `./RESOURCES.md`: Curated set of trusted reference materials.
- `./GLOSSARY.md`: Canonical glossary of terms, built dynamically as the user masters concepts.
- `./learning-records/`: Sequential records (`0001-slug.md`) tracking capability shifts, misconceptions corrected, and spaced repetition.
- `./lessons/`: Self-contained lessons authored as HTML pages.
- `./reference/`: Reference sheets and cheat-sheets.
- `./assets/`: Shared components (CSS, templates, logos) for lessons.
- `./NOTES.md`: User preferences and session notes.

## Socratic Debugging (Failure Protocol)
When the user makes a mistake in an exercise, DO NOT give them the correct answer. Instead:
1. **Isolate the fault:** Point out exactly where their logic or understanding broke down.
2. **Explain the crash:** Explain *why* their current mental model produced an error.
3. **Prompt the patch:** Ask a targeted question that forces the user to figure out the correct approach.

## Philosophy & Assets
To learn at a deep level, the user needs Knowledge, Skills, and Wisdom. Reuse is the default, not the exception. Before authoring a lesson, inspect `./assets/` and reuse components.
