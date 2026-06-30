# IP-003 Learner Profile and Baseline Assessment Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Let the learner set interview goals, available hours, and baseline confidence by technology.

**Architecture:** Add a profile domain model and a Settings/Profile view. Store profile state in app memory for this ticket; persistence comes in IP-009 unless localStorage already exists from earlier implementation choices.

**Tech Stack:** React, TypeScript, Vitest, React Testing Library.

---

## Ticket

**Epic:** E2 Daily Study Loop

**User value:** The daily plan can use real constraints instead of hard-coded assumptions.

## Acceptance Criteria

- The learner can enter target role, interview month, weekday hours, Saturday hours, Sunday hours, and current confidence for each technology.
- Confidence uses a 1-5 scale.
- Invalid hours show inline validation and do not update the saved profile.
- The Dashboard shows the saved target role and weekly time budget.
- Tests cover validation and successful save.

## Plan

### Task 1: Add profile domain model

**Files:**
- Create: `src/types/profile.ts`
- Create: `src/domain/profile.ts`
- Create: `src/domain/profile.test.ts`

**Steps:**

1. Define `LearnerProfile` and `TechnologyConfidence`.
2. Add `createDefaultProfile()` with July interview defaults.
3. Add `validateProfile()` for hour ranges and confidence ranges.
4. Test valid defaults, invalid negative hours, and invalid confidence.

### Task 2: Add profile UI

**Files:**
- Create: `src/components/ProfileSettings.tsx`
- Create: `src/components/ProfileSettings.test.tsx`
- Modify: `src/App.tsx`
- Modify: `src/styles.css`

**Steps:**

1. Add controlled form fields for the profile.
2. Show validation errors next to invalid fields.
3. On save, update app-level profile state.
4. Show target role and weekly hours summary on Dashboard.
5. Test editing a role and rejecting invalid hours.

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
git commit -m "Add learner profile baseline"
```
