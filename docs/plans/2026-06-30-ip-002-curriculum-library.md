# IP-002 Curriculum Data and Resource Library Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Add structured interview curriculum data and a browsable resource library.

**Architecture:** Keep curriculum as static typed data under `src/data`. Render it through reusable list and detail components. Do not add network calls or persistence.

**Tech Stack:** React, TypeScript, Vitest, React Testing Library.

---

## Ticket

**Epic:** E1 Local App Foundation and Curriculum Browser

**User value:** The learner can browse what to study by technology, topic, source, difficulty, and interview use.

## Acceptance Criteria

- The app includes seed data for React, Next.js, TypeScript, React Native, FastAPI, Flask, JavaScript fundamentals, and coding interviews.
- Each resource has title, URL, technology, topic, difficulty, estimated minutes, and interview use.
- The Resources view supports filtering by technology and difficulty.
- Selecting a resource shows its interview output requirement.
- Tests cover the data shape and at least one filter path.

## Plan

### Task 1: Add typed curriculum data

**Files:**
- Create: `src/types/curriculum.ts`
- Create: `src/data/curriculum.ts`
- Create: `src/data/curriculum.test.ts`

**Steps:**

1. Define `Technology`, `Topic`, and `Resource` types.
2. Seed resources from `docs/learning-resources.md`.
3. Write a test that every resource has a non-empty URL, topic, difficulty, and interview use.
4. Run `npm test -- --run src/data/curriculum.test.ts`.

### Task 2: Build resource library UI

**Files:**
- Create: `src/components/ResourceLibrary.tsx`
- Create: `src/components/ResourceLibrary.test.tsx`
- Modify: `src/App.tsx`
- Modify: `src/styles.css`

**Steps:**

1. Render resource filters and a list of matching resources.
2. Add a detail panel for the selected resource.
3. Show the resource-to-output rule from the data.
4. Test technology filtering and detail selection.

### Task 3: Verify and commit

Run:

```bash
npm run build
npm test -- --run
```

Expected: both commands exit 0.

Commit:

```bash
git add src
git commit -m "Add curriculum resource library"
```
