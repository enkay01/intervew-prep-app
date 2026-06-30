# IP-009 Local Backup, Restore, and Static Build Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Persist local study state, add JSON backup/restore, and make the static app build suitable for optional GitHub Pages hosting.

**Architecture:** Use browser localStorage for MVP persistence. Add import/export around a versioned app-state object. Add a static build check without adding hosted databases or auth.

**Tech Stack:** React, TypeScript, Vitest, Vite, GitHub Actions only if Pages workflow is desired.

---

## Ticket

**Epic:** E5 Data Durability and Lightweight Access

**User value:** The learner does not lose study progress and can move data between browsers or machines.

## Acceptance Criteria

- App state persists after browser refresh.
- Settings includes Export JSON and Import JSON controls.
- Exported data includes schema version, profile, sessions, attempts, and mock interviews.
- Import validates schema version and rejects malformed data with a visible error.
- `npm run build` creates a static artifact.
- Optional Pages workflow deploys only the static artifact and does not add a backend.

## Plan

### Task 1: Add versioned persistence

**Files:**
- Create: `src/types/appState.ts`
- Create: `src/domain/appState.ts`
- Create: `src/domain/appState.test.ts`
- Create: `src/storage/localStore.ts`
- Create: `src/storage/localStore.test.ts`
- Modify: `src/App.tsx`

**Steps:**

1. Define a versioned `AppState` type.
2. Implement `serializeAppState(state)` and `parseAppState(json)`.
3. Implement localStorage load/save wrappers.
4. Wire app state load on startup and save on state changes.
5. Test parse success, malformed JSON, and unsupported version.

### Task 2: Add backup and restore UI

**Files:**
- Create: `src/components/BackupRestore.tsx`
- Create: `src/components/BackupRestore.test.tsx`
- Modify: `src/components/ProfileSettings.tsx`
- Modify: `src/styles.css`

**Steps:**

1. Add Export JSON button that downloads the current app state.
2. Add Import JSON file input.
3. Show success or validation error messages.
4. Test export button availability and invalid import error.

### Task 3: Add static build readiness

**Files:**
- Modify: `package.json`
- Optional create: `.github/workflows/pages.yml`

**Steps:**

1. Ensure `npm run build` writes the Vite static output.
2. If adding Pages, configure the workflow to run build and upload `dist`.
3. Do not add secrets, databases, auth providers, or server deployment steps.

### Task 4: Verify and commit

Run:

```bash
npm run build
npm test -- --run
```

Expected: both commands exit 0.

Commit:

If a Pages workflow was added, run:

```bash
git add src package.json .github/workflows/pages.yml
git commit -m "Add local backup and static build"
```

If no Pages workflow was added, run:

```bash
git add src package.json
git commit -m "Add local backup and static build"
```
