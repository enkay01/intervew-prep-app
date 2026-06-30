# Requirements and Feature Scope

## Product goal

Build a small personal interview prep app that turns weak React/full-stack confidence into interview-ready capability across React, Next.js, TypeScript, React Native, FastAPI, and Flask.

This is not a SaaS product, a multi-user learning platform, or a portfolio app whose codebase is meant to teach the learner. Codex will implement the app. The learner benefits from using the app: doing exercises, answering prompts, revising mistakes, and seeing what to study next.

## Target user

One developer preparing to apply for a wider range of full-stack jobs in July. The app only needs to support that person's study data, schedule, exercises, and progress.

## Success metrics

- Complete at least 25 focused study days in July.
- Complete at least 60 coding exercises across UI, API, TypeScript, and data structures.
- Complete at least 8 timed mock interviews.
- Produce interview-ready practice artifacts: code exercises, short explanations, API designs, and mock interview notes.
- Maintain a revision streak with spaced recall of previous exercises.

## Feature list

### 1. Onboarding and baseline assessment

- Capture target roles, available hours, current confidence per technology, and interview date range.
- Run a diagnostic quiz for JavaScript, React, TypeScript, API design, and data structures.
- Run a short coding diagnostic: React component, TypeScript utility, REST endpoint, and one algorithm problem.
- Produce a readiness score by technology and interview category.

### 2. Learning roadmap

- Generate a July-ready plan with daily tasks.
- Prioritize React, TypeScript, and Next.js first because they unlock most full-stack frontend interviews.
- Include FastAPI and Flask API interview patterns.
- Include React Native as a mobile transfer layer after React fundamentals.
- Support daily revision of earlier exercises using spaced repetition.

### 3. Interview Q&A trainer

- Flashcards for principles, lifecycle/rendering, routing, state, hooks, typing, API design, auth, testing, deployment, and trade-offs.
- Answer recording with rubric scoring: accuracy, concision, trade-off awareness, and example quality.
- Follow-up question generator for deeper interview probing.
- The follow-up generator can be rule-based in MVP. AI is optional later if it improves practice quality.
- "Explain it like a senior engineer" answer templates.

### 4. Coding practice workspace

- Timed exercises for:
  - React components and hooks.
  - Next.js routing, server/client components, forms, data fetching, and auth flows.
  - TypeScript types, generics, narrowing, discriminated unions, and API contracts.
  - React Native navigation, lists, forms, storage, and platform differences.
  - FastAPI routes, Pydantic models, dependencies, async, auth, and tests.
  - Flask routes, blueprints, request handling, templates or JSON APIs, auth, and tests.
- Hidden tests and rubric feedback.
- Review mode comparing user solution to model solution.

### 5. Mock interview mode

- 30, 45, and 60 minute interview simulations.
- Tracks behavioral, Q&A, system design, and coding rounds.
- Generates feedback summary and next-day remediation tasks.

### 6. Progress tracking

- Dashboard for July progress, streaks, readiness scores, weak topics, and next best action.
- Phone-friendly study dashboard for checking today's plan and marking tasks complete.
- Daily completion checklist and weekly readiness review.

### 7. Resource library

- Curated links to official docs and selected practice resources.
- Resource metadata: topic, difficulty, interview relevance, estimated time, and linked exercises.
- Notes and summaries connected to flashcards and coding tasks.

### 8. Build notes

- Keep a simple build backlog so Codex can implement the app in small slices.
- Keep build progress outside the study loop unless it affects what can be used today.
- Do not make Codex logs a core app feature; they are project-management notes, not interview prep.

## Functional requirements

- The system shall store technologies, topics, lessons, flashcards, exercises, attempts, rubrics, study sessions, and mock interviews for one local user.
- The system shall generate a daily plan based on deadline, readiness, and revision debt.
- The system shall schedule revision for exercises answered incorrectly or with low confidence.
- The system shall support timed coding tests and persist attempts.
- The system shall provide interview Q&A prompts and scoring rubrics.
- The system shall expose a dashboard optimized for desktop and mobile.

## Non-functional requirements

- Fast local startup and simple local backup.
- Strong typing in app code where it reduces implementation risk; the app code is not the learner's primary study material.
- Accessible UI with keyboard navigation and readable contrast.
- Testable domain logic for scheduling, scoring, and progress calculations.
- No authentication for MVP because there is only one local user.
- Local-first storage. SQLite is acceptable when persistence needs queries; JSON files are acceptable for the first static/content-heavy slice.
- Optional backup/export to Markdown or JSON only when it helps review study history or move data between machines. Export is not an interview-prep feature by itself.

## Scope guard

This section exists only to prevent the app drifting back into a platform. It does not list every product idea that could exist.

- Login, account management, roles, teams, classrooms, and public sharing.
- Hosted production deployment.
- Native mobile app release.
- AI voice calls.
- Complex remote code execution infrastructure. Local/manual checks are enough at first.

## MVP cut

1. Roadmap dashboard.
2. Daily plan and revision queue.
3. Resource library.
4. Flashcard/Q&A trainer.
5. Coding exercise catalog with manual/self-scored results first.
6. Mock interview checklist and rubric.
