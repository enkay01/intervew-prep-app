# Tech Stack Decision Record

## Recommended stack

| Layer | Choice | Why it fits the interview goal |
| --- | --- | --- |
| Web app | Next.js with React | Demonstrates modern full-stack React patterns, routing, data fetching, server/client boundaries, forms, and deployment. |
| Language | TypeScript | Required for many React/Next.js roles and useful for discussing contracts, safety, generics, narrowing, and maintainability. |
| Styling | Tailwind CSS plus accessible component primitives | Fast UI delivery while leaving room to discuss accessibility and design systems. |
| Primary API | FastAPI | High-value Python API framework using type hints and Pydantic-style validation concepts. |
| Comparison API/labs | Flask | Shows ability to explain lightweight Python web fundamentals and contrast Flask with FastAPI. |
| Database | PostgreSQL | Common production relational database for progress, attempts, resources, and scheduling. |
| ORM | Prisma for Next.js data or SQLAlchemy for Python service | Pick one primary persistence path for MVP; SQLAlchemy is better if FastAPI owns the backend. |
| Testing | Vitest, React Testing Library, Playwright, pytest | Covers unit, component, e2e, and Python API tests. |
| Deployment | Vercel for Next.js, Render/Fly.io/Railway for Python API, managed Postgres | Practical interview discussion around deployment boundaries and trade-offs. |
| Diagrams/docs | Markdown and Mermaid | Keeps planning inspectable before implementation. |

## MVP stack recommendation

Use **Next.js + TypeScript + Tailwind + PostgreSQL** first, with a **FastAPI service** for exercises/scheduling once the frontend roadmap is usable. Add **Flask labs** as learning modules rather than production-critical infrastructure.

## Rationale

- React weakness is the main blocker, so the product should be built in React/Next.js from the start.
- TypeScript should be used everywhere in the UI to force daily practice with props, events, API responses, unions, and generics.
- FastAPI should power at least one real feature so the learner can explain Python type hints, validation, dependency injection, OpenAPI docs, async, and tests.
- Flask should be included through focused comparison exercises: routing, request context, blueprints, app factory, testing, and when a lightweight framework is appropriate.
- React Native is best introduced after React fundamentals, using shared concepts: components, props, state, hooks, navigation, lists, forms, and platform APIs.

## Implementation order

1. Static documentation and curriculum schema.
2. Next.js shell, dashboard, resource library, and daily checklist.
3. TypeScript domain logic for scoring and scheduling.
4. Flashcard/Q&A trainer.
5. Exercise catalog and attempts.
6. FastAPI exercise service and tests.
7. Flask comparison labs.
8. React Native companion mini-app or Expo prototype after the web MVP.
