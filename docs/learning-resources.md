# Learning Resources and Interview Knowledge Map

## Source selection principles

Use official documentation first, then practice platforms for interview repetition. The objective is not passive tutorial completion; every resource must produce an interview answer, a code exercise, or a portfolio feature.

## Primary sources

| Area | Source | Interview use |
| --- | --- | --- |
| React | https://react.dev/learn | Components, props, state, events, conditional rendering, lists, hooks, effects, refs, context, and thinking in React. |
| Next.js | https://nextjs.org/docs and https://nextjs.org/learn | App Router, routing, layouts, server/client components, data fetching, rendering strategies, forms, caching, API routes, and deployment. |
| TypeScript | https://www.typescriptlang.org/docs/handbook/intro.html | Everyday types, narrowing, functions, object types, generics, unions, discriminated unions, modules, and type design trade-offs. |
| React Native | https://reactnative.dev/docs/getting-started | Native components, platform differences, styling, lists, touch handling, navigation concepts, and Expo/local setup options. |
| FastAPI | https://fastapi.tiangolo.com/tutorial/ | Python type hints, path/query/body parameters, Pydantic models, dependency injection, auth, async, OpenAPI docs, and testing. |
| Flask | https://flask.palletsprojects.com/en/stable/tutorial/ | Routes, request/response cycle, app factory, blueprints, templates, sessions, testing, and lightweight API design. |
| JavaScript fundamentals | https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide | Closures, promises, async/await, arrays, objects, modules, DOM/event model, and language fundamentals needed for React interviews. |
| Coding interviews | https://neetcode.io/roadmap | Structured data structures and algorithms sequence for timed coding screens. |

## What to know for interviews

### React

- Component model, props, state, rendering, reconciliation basics, and composition.
- Hooks: useState, useEffect, useMemo, useCallback, useRef, useContext, custom hooks, and rules of hooks.
- Controlled vs uncontrolled forms.
- Lifting state, derived state, context trade-offs, and when to use external state libraries.
- Performance: memoization, keys, avoiding unnecessary renders, virtualization, and profiling.
- Testing components and user interactions.
- Common Q&A: why keys matter, when effects run, how to avoid prop drilling, how to structure reusable components.

### Next.js

- File-system routing, layouts, loading/error states, nested routes, and dynamic segments.
- Server components vs client components and when each is appropriate.
- Data fetching, caching, revalidation, server actions/forms, API routes/route handlers.
- Rendering strategies: static rendering, dynamic rendering, streaming, and client-side rendering trade-offs.
- Auth/session patterns and deployment considerations.
- Common Q&A: why choose Next.js over Vite React, how SSR improves UX/SEO, what can go wrong with hydration.

### TypeScript

- Type annotations vs inference.
- Interfaces vs type aliases and practical trade-offs.
- Union types, narrowing, discriminated unions, never, unknown, and generics.
- Typing React props, events, hooks, API responses, and async functions.
- Designing safe domain models and avoiding overuse of any.
- Common Q&A: how TypeScript improves refactoring, runtime vs compile-time safety, how to type reusable components.

### React Native

- How React Native maps React concepts to native UI primitives.
- View/Text/Image/Pressable/FlatList/TextInput and styling differences from web CSS.
- Navigation, device APIs, permissions, storage, and platform-specific code.
- Performance concerns with long lists, bridge/native modules concepts, and release constraints.
- Common Q&A: React vs React Native differences, Expo trade-offs, handling platform differences.

### FastAPI

- Path/query/body parameters and validation.
- Pydantic schemas, response models, dependency injection, auth dependencies, and OpenAPI generation.
- async vs sync endpoints and when it matters.
- Testing with pytest and dependency overrides.
- Common Q&A: why FastAPI is fast to build with, how validation works, how to structure routers/services.

### Flask

- Minimal routing, request context, blueprints, app factory pattern, extensions, and testing.
- Building JSON APIs and template-rendered pages.
- Auth/session basics and configuration.
- Common Q&A: Flask vs FastAPI, when Flask is enough, how to structure a larger Flask app.

### Cross-cutting full-stack topics

- HTTP, REST, status codes, cookies, sessions, JWTs, CORS, CSRF, and auth flows.
- API contract design between frontend and backend.
- SQL schema design, migrations, indexing basics, and transactions.
- Testing pyramid: unit, integration, component, e2e.
- Accessibility, performance, deployment, observability, and security basics.
- System design for common products: dashboard, CRUD app, chat, notifications, search, file upload, and scheduling.

## Resource-to-output rule

For every resource block, create at least one of:

1. A flashcard set with 5-10 interview questions.
2. A code exercise with acceptance criteria.
3. A 2-minute spoken answer outline.
4. A mini-feature in the prep platform.
