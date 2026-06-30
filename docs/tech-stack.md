# Tech Stack Decision Record

## Decision principle

Choose the stack that makes the study app quick to build, easy to run locally, and easy to change. Do not choose technologies merely because the learner needs to study them. Codex writing the app does not teach the learner React, Next.js, FastAPI, or Flask. The app should teach through prompts, exercises, timed practice, revision, and feedback.

## Recommended stack

| Layer | Choice | Why it fits the interview goal |
| --- | --- | --- |
| Web app | Static React with Vite, or plain HTML/JS if the MVP stays very small | Runs locally, builds fast, and can be published to GitHub Pages later without server infrastructure. |
| Language | TypeScript if using React; JavaScript is acceptable for a throwaway prototype | TypeScript improves scheduling/scoring correctness, but the app code is not the learner's study source. |
| Styling | Simple CSS or Tailwind only if already convenient | The app is a study tool, so speed, readability, and maintainability matter more than a design system. |
| Persistence | Start with local JSON/localStorage; move to SQLite when queries and history become awkward | Single-user local-first storage avoids unnecessary database setup. SQLite gives real persistence without running a service. |
| API/backend | None for MVP | A local app can schedule, score, and track progress in the browser or a small local script. |
| FastAPI/Flask | Learning exercises inside the curriculum, not app infrastructure | These should be practiced directly through interview tasks, not added to the app just to use them. |
| Testing | Unit tests for scheduling/scoring; one smoke test for the app | Test the logic that decides what to study next. Avoid heavy test setup before the tool is useful. |
| Deployment | Local first; optional GitHub Pages for cloud-accessible static app | The learner does not need Vercel, managed databases, or production hosting for MVP. |
| Diagrams/docs | Markdown and Mermaid | Keeps planning inspectable before implementation. |

## MVP stack recommendation

Use a **local-first static web app** first:

1. Vite + React + TypeScript if a component-based UI is useful.
2. Plain HTML/CSS/JavaScript if the MVP can remain tiny.
3. localStorage or a JSON file for the first slice.
4. SQLite once attempts, revision history, and filtering need real queries.

For cloud access after MVP, prefer the lightest path:

1. GitHub Pages for a static build.
2. Browser storage plus manual JSON backup.
3. Later, if phone and laptop need shared state, add a small SQLite-backed sync option or a tiny hosted backend.

GitHub Pages makes the app reachable from a phone, but it does not automatically sync study data between devices. Treat cross-device data as a separate post-MVP decision.

## Rationale

- The app's stack should minimize build drag. The study curriculum should teach interview technologies.
- React/Next.js/TypeScript practice belongs in daily exercises where the learner writes code, explains choices, and gets timed feedback.
- FastAPI and Flask practice belongs in backend exercises where the learner builds endpoints, validates data, writes tests, and explains framework trade-offs.
- React Native practice belongs in focused mobile exercises after React fundamentals, not in the prep app unless mobile access becomes the main blocker.
- SQLite is the right upgrade path when localStorage/JSON becomes too limited. PostgreSQL is unnecessary for one local user.
- AI integrations should be judged by study value: follow-up prompts, answer feedback, weak-spot summaries, and plan adjustments. They should not require a database, auth, or hosted backend for MVP.

## Implementation order

1. Static curriculum/resource schema.
2. Local app shell with dashboard, resource library, and daily checklist.
3. Deterministic scheduling/scoring logic with tests.
4. Flashcard/Q&A trainer.
5. Exercise catalog and attempt tracking.
6. SQLite persistence if the local data model has outgrown JSON/localStorage.
7. GitHub Pages build if phone access matters after MVP.
8. FastAPI, Flask, Next.js, and React Native practice modules as study content, not app infrastructure.
