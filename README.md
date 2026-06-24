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
*   **Anchor**: Read `MISSION.md`. If it is missing or vague, the agent stops to align on the user's real-world goals.
*   **Locate**: Read the `./learning-records/` directory to identify the user's current edge of capability and check for pending spaced-repetition reviews.
*   **Ground**: Retrieve facts from `RESOURCES.md` to ground the lesson content instead of relying solely on parametric defaults.
*   **Execute**: Teach a single, tightly-scoped concept and present an active retrieval question.
*   **Persist**: Document progress in `GLOSSARY.md` or `./learning-records/` only after the user demonstrates understanding.

### 2. The Quality Gate
To maintain educational standards, every generated lesson must satisfy all of the following criteria:
*   **Mission Alignment**: Directly connected to an objective defined in `MISSION.md`.
*   **Source Grounding**: Drawn strictly from trusted sources documented in `RESOURCES.md`.
*   **Retrieval Check**: Includes a question requiring the user to recall key concepts.
*   **Transfer Challenge**: Includes a practical exercise where the user applies the knowledge to a new scenario.

### 3. Socratic Debugging
When a user submits an incorrect answer or makes a mistake during an exercise, the agent does not provide the correct solution immediately. Instead, it follows a failure protocol:
1.  **Isolate the fault**: Point out exactly where the logic or understanding broke down.
2.  **Explain the crash**: Explain why the incorrect mental model caused the error.
3.  **Prompt the patch**: Ask targeted questions to guide the user toward discovering the correct solution themselves.

## Installation and Configuration

To use this skill, include `teach-me.md` in your agent's customization directory or workspace configuration. The agent will read `teach-me.md` to trigger the behavioral instructions whenever a learning or teaching task is requested.
