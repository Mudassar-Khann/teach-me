# Teach-Me Custom Skill

A stateful, workspace-based custom skill designed to teach new concepts or skills while optimizing for long-term retention, active processing, and conceptual clarity.

## Overview

The Teach-Me skill enables AI agents to guide users through structured, multi-session learning pathways. It enforces a strict pedagogical pipeline that anchors all lessons in real-world goals, verifies understanding through active retrieval and transfer challenges, tracks capability growth, and handles mistakes using a Socratic debugging protocol.

## Workspace Structure

The teaching environment relies on a structured workspace directory that stores resources, progress tracking, and lessons. The following structure defines the workspace:

*   **MISSION.md**: Defines the core motivation, target outcomes, milestones, constraints, and out-of-scope boundaries. Every lesson aligns with this mission.
*   **RESOURCES.md**: A curated list of trusted sources (Knowledge) and community references (Wisdom) to ground all lessons.
*   **GLOSSARY.md**: The canonical vocabulary for the topic. Terms are added only once understanding is demonstrated.
*   **learning-records/**: A directory containing numbered records (e.g., `0001-slug.md`) that track capability shifts, misconceptions corrected, and spaced-repetition schedules.
*   **lessons/**: Contains self-contained lessons formatted as HTML pages, each focusing on a single, tightly-scoped concept.
*   **reference/**: Reference sheets and quick-access documentation.
*   **assets/**: Shared reusable components for lesson presentation.
*   **NOTES.md**: A scratchpad for recording user preferences and context.

## How it Works

When a teaching request is initiated, the agent executes a structured Standard Operating Procedure (SOP) to ensure contextually grounded, incremental instruction.

### 1. The Standard Operating Procedure (SOP)
*   **Bootstrap**: Check if [MISSION.md](file:///D:/skills/teach-me/MISSION.md) and [RESOURCES.md](file:///D:/skills/teach-me/RESOURCES.md) exist in the workspace root. If missing, read [MISSION-FORMAT.md](file:///D:/skills/teach-me/MISSION-FORMAT.md) and [RESOURCES-FORMAT.md](file:///D:/skills/teach-me/RESOURCES-FORMAT.md) and collaborate with the user to initialize them, along with [GLOSSARY.md](file:///D:/skills/teach-me/GLOSSARY.md) (using [GLOSSARY-FORMAT.md](file:///D:/skills/teach-me/GLOSSARY-FORMAT.md)).
*   **Anchor**: Read [MISSION.md](file:///D:/skills/teach-me/MISSION.md). If its details are vague, pause and ask the user to clarify their real-world goals and constraints.
*   **Locate & Review**: Scan [learning-records/](file:///D:/skills/teach-me/learning-records/) to identify the user's current edge of capability. Check for concepts with a `next-review-date` that is today or in the past, and prioritize a review/quiz for those concepts before teaching new material.
*   **Ground**: Pull facts from [RESOURCES.md](file:///D:/skills/teach-me/RESOURCES.md) to ground the lesson content.
*   **Execute**: Teach a single, tightly-scoped concept. Author a self-contained HTML lesson file under [lessons/](file:///D:/skills/teach-me/lessons/) (e.g. `0001-variables.html`) utilizing components in [assets/](file:///D:/skills/teach-me/assets/) and provide a clickable file link. End the response with one active retrieval question and one transfer challenge.
*   **Persist**: Update [GLOSSARY.md](file:///D:/skills/teach-me/GLOSSARY.md) and write/update a learning record in [learning-records/](file:///D:/skills/teach-me/learning-records/) only after the user demonstrates understanding or corrects a notable mistake.

### 2. The Quality Gate
To maintain educational standards, every generated lesson must satisfy all of the following criteria:
*   **Mission Alignment**: Directly connected to an objective defined in [MISSION.md](file:///D:/skills/teach-me/MISSION.md).
*   **Single Bounded Win**: Teaches exactly one concept with one clear victory.
*   **Source Grounding**: Drawn strictly from trusted sources documented in [RESOURCES.md](file:///D:/skills/teach-me/RESOURCES.md).
*   **Retrieval Check**: Includes a question requiring the user to recall key concepts.
*   **Transfer Challenge**: Includes a practical exercise where the user applies the knowledge to a new scenario.

### 3. Socratic Debugging
When a user submits an incorrect answer or makes a mistake during an exercise, the agent does not provide the correct solution immediately. Instead, it follows a Socratic failure protocol:
1.  **Isolate the fault**: Point out exactly where the logic or understanding broke down.
2.  **Explain the crash**: Explain why the incorrect mental model caused the error.
3.  **Prompt the patch**: Ask targeted questions to guide the user toward discovering the correct solution themselves.

## Installation and Configuration

To use this skill, include [SKILL.md](file:///D:/skills/teach-me/SKILL.md) in your agent's customization directory or workspace configuration. The agent will read [SKILL.md](file:///D:/skills/teach-me/SKILL.md) to trigger the behavioral instructions whenever a learning or teaching task is requested.
