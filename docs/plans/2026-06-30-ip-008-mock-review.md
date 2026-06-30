# IP-008 Mock Interview Mode and Weekly Review Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Add mock interview sessions, scoring rubrics, and weekly readiness review.

**Architecture:** Model mock interviews as local sessions composed of rounds. Scores create remediation tasks that reuse existing revision/progress logic.

**Tech Stack:** React, TypeScript, Vitest, React Testing Library.

---

## Ticket

**Epic:** E4 Interview Readiness Review

**User value:** The learner can simulate interviews, identify gaps, and turn feedback into the next study plan.

## Acceptance Criteria

- Mock Interview view supports 30, 45, and 60 minute session templates.
- Templates include behavioral, Q&A, system/API design, and coding rounds.
- The learner can score each round and add notes.
- Completing a mock generates top gaps and remediation tasks.
- Weekly review shows completed study days, exercise count, mock count, weakest topics, and next-week focus.
- Tests cover mock scoring and remediation generation.

## Plan

### Task 1: Add mock interview domain logic

**Files:**
- Create: `src/types/mockInterview.ts`
- Create: `src/domain/mockInterview.ts`
- Create: `src/domain/mockInterview.test.ts`

**Steps:**

1. Define session templates for 30, 45, and 60 minutes.
2. Implement `scoreMockInterview(roundScores)`.
3. Implement `generateRemediationTasks(mockResult)`.
4. Test scoring and remediation for weak rounds.

### Task 2: Add mock interview UI and weekly review

**Files:**
- Create: `src/components/MockInterview.tsx`
- Create: `src/components/WeeklyReview.tsx`
- Create: `src/components/MockInterview.test.tsx`
- Modify: `src/App.tsx`
- Modify: `src/styles.css`

**Steps:**

1. Render session template selection.
2. Render round scoring and notes.
3. Show generated gaps after completion.
4. Add weekly review summary to Dashboard or Mock Interview view.
5. Test selecting a template and completing a mock.

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
git commit -m "Add mock interview review"
```
