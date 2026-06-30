# IP-007 Coding Exercise Catalog and Attempts Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Add a coding exercise catalog with timed manual attempts and self-scored results.

**Architecture:** Keep exercise prompts as typed data. The app records attempt metadata and self-scoring; it does not run remote code or create a sandbox.

**Tech Stack:** React, TypeScript, Vitest, React Testing Library.

---

## Ticket

**Epic:** E3 Practice Tools

**User value:** The learner can run timed coding practice and track weak implementation areas.

## Acceptance Criteria

- Practice view has a Coding mode with filters for technology, difficulty, and exercise type.
- Each exercise shows prompt, acceptance criteria, expected time, hints, and model-solution summary.
- The learner can start/stop a timer and submit score, confidence, notes, and completion status.
- Submitted attempts affect revision/progress state.
- No hidden remote code execution is added.
- Tests cover filtering and attempt submission.

## Plan

### Task 1: Add exercise data and timer logic

**Files:**
- Create: `src/types/exercise.ts`
- Create: `src/data/exercises.ts`
- Create: `src/domain/exerciseTimer.ts`
- Create: `src/domain/exerciseTimer.test.ts`

**Steps:**

1. Seed exercises for React, Next.js, TypeScript, FastAPI, Flask, React Native, and algorithms.
2. Include prompt, acceptance criteria, hints, expected minutes, difficulty, and model summary.
3. Implement timer formatting and elapsed-minute helpers.
4. Test timer formatting and exercise data completeness.

### Task 2: Add coding practice UI

**Files:**
- Create: `src/components/CodingPractice.tsx`
- Create: `src/components/CodingPractice.test.tsx`
- Modify: `src/App.tsx`
- Modify: `src/styles.css`

**Steps:**

1. Render filters and exercise cards.
2. Add selected exercise detail view.
3. Add timer controls.
4. Add attempt form for score, confidence, notes, and completed status.
5. Test filtering and submitting an attempt.

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
git commit -m "Add coding exercise attempts"
```
