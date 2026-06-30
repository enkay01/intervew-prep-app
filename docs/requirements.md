# Requirements and Feature Scope

## Product goal

Build an interview prep platform that turns weak React/full-stack confidence into interview-ready capability across React, Next.js, TypeScript, React Native, FastAPI, and Flask.

## Target user

A developer preparing to apply for a wider range of full-stack jobs in July who needs daily guided practice, revision, coding tests, and concise interview explanations.

## Success metrics

- Complete at least 25 focused study days in July.
- Complete at least 60 coding exercises across UI, API, TypeScript, and data structures.
- Complete at least 8 timed mock interviews.
- Produce portfolio-ready mini-projects using React, Next.js, TypeScript, FastAPI, Flask, and React Native.
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
- “Explain it like a senior engineer” answer templates.

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
- Phone-friendly status view for checking Codex/cloud session progress.
- Daily completion checklist and weekly readiness review.

### 7. Resource library

- Curated links to official docs and selected practice resources.
- Resource metadata: topic, difficulty, interview relevance, estimated time, and linked exercises.
- Notes and summaries connected to flashcards and coding tasks.

### 8. Codex implementation operations

- Establish documentation before code.
- Break implementation into small autonomous Codex tasks.
- Track sessions, limit resets, branch status, PRs, and test results.
- Provide mobile-readable progress updates.

## Functional requirements

- The system shall store technologies, topics, lessons, flashcards, exercises, attempts, rubrics, study sessions, and mock interviews.
- The system shall generate a daily plan based on deadline, readiness, and revision debt.
- The system shall schedule revision for exercises answered incorrectly or with low confidence.
- The system shall support timed coding tests and persist attempts.
- The system shall provide interview Q&A prompts and scoring rubrics.
- The system shall expose a dashboard optimized for desktop and mobile.

## Non-functional requirements

- Fast local development and CI feedback.
- Strong TypeScript typing across frontend and API contracts.
- Accessible UI with keyboard navigation and readable contrast.
- Testable domain logic for scheduling, scoring, and progress calculations.
- Secure handling of auth tokens and user data.
- Exportable learning data to Markdown or JSON.

## Out of scope for initial MVP

- Multi-user classrooms.
- Payments.
- AI voice interview calls.
- Native app store release.
- Complex code execution sandbox infrastructure beyond local/test-runner-based exercises.

## MVP cut

1. Roadmap dashboard.
2. Daily plan and revision queue.
3. Resource library.
4. Flashcard/Q&A trainer.
5. Coding exercise catalog with manual/self-scored results first.
6. Mock interview checklist and rubric.
