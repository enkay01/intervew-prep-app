# IP-004 Daily Plan Dashboard and Task Completion Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Show today's study plan and let the learner mark tasks complete.

**Architecture:** Add deterministic plan generation from profile, curriculum, and current date. Store completion state in app memory for this ticket. Keep scheduling simple until IP-005.

**Tech Stack:** React, TypeScript, Vitest, React Testing Library.

---

## Ticket

**Epic:** E2 Daily Study Loop

**User value:** The learner can open the app and know exactly what to study today.

## Acceptance Criteria

- Dashboard shows today's date, total planned minutes, and a list of study tasks.
- Tasks include revision, concept learning, build exercise, interview output, and coding screen practice.
- Each task has title, technology/topic, estimated minutes, and done state.
- Marking tasks complete updates daily completion percentage.
- Tests cover plan generation and task completion.

## Plan

### Task 1: Add daily plan domain logic

**Files:**
- Create: `src/types/studyPlan.ts`
- Create: `src/domain/dailyPlan.ts`
- Create: `src/domain/dailyPlan.test.ts`

**Steps:**

1. Define `StudyTask`, `StudySession`, and `DayType`.
2. Add `buildDailyPlan(profile, resources, date)` using the July daily structure.
3. Prefer React, TypeScript, and Next.js topics first.
4. Test that a weekday plan fits weekday available hours.
5. Test that every generated task has an estimated minute value.

### Task 2: Add dashboard task UI

**Files:**
- Create: `src/components/DailyDashboard.tsx`
- Create: `src/components/DailyDashboard.test.tsx`
- Modify: `src/App.tsx`
- Modify: `src/styles.css`

**Steps:**

1. Render the generated tasks on the Dashboard.
2. Add checkboxes for completion.
3. Calculate and render completion percentage.
4. Test checking a task updates the displayed progress.

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
git commit -m "Add daily study dashboard"
```
