# IP-005 Revision Scheduler and Progress Metrics Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Add deterministic revision scheduling and progress metrics based on task outcomes and confidence.

**Architecture:** Keep scheduling in pure domain functions. UI reads computed revision debt and readiness metrics from app state.

**Tech Stack:** React, TypeScript, Vitest.

---

## Ticket

**Epic:** E2 Daily Study Loop

**User value:** Mistakes and low-confidence topics come back for revision instead of disappearing.

## Acceptance Criteria

- The app tracks completed tasks, score, confidence, and next revision date.
- Low score or low confidence schedules near-term revision.
- High score and high confidence schedules light revision later.
- Dashboard shows revision due count, study streak, and readiness by technology.
- Tests cover scheduling rules and readiness calculation.

## Plan

### Task 1: Add progress domain model

**Files:**
- Create: `src/types/progress.ts`
- Create: `src/domain/revisionScheduler.ts`
- Create: `src/domain/revisionScheduler.test.ts`
- Create: `src/domain/progressMetrics.ts`
- Create: `src/domain/progressMetrics.test.ts`

**Steps:**

1. Define `AttemptLike`, `RevisionItem`, and `ReadinessScore`.
2. Implement `scheduleNextRevision({ score, confidence, completedAt })`.
3. Implement `calculateReadiness(attempts, technologies)`.
4. Implement `calculateStreak(studySessions)`.
5. Test low-confidence, failed, and confident-pass revision intervals.

### Task 2: Add progress UI

**Files:**
- Create: `src/components/ProgressSummary.tsx`
- Create: `src/components/ProgressSummary.test.tsx`
- Modify: `src/components/DailyDashboard.tsx`
- Modify: `src/App.tsx`
- Modify: `src/styles.css`

**Steps:**

1. Add progress cards for due revisions, streak, and weakest technology.
2. Add a simple scoring/confidence control when completing a task.
3. Feed completed task outcomes into progress state.
4. Test that low-confidence completion increases due revision count.

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
git commit -m "Add revision scheduler and progress metrics"
```
