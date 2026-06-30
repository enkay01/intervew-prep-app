# Codex Autonomous Implementation Workflow

## Rule: establish before implementation

No application code should be written until the requirements, resource map, July learning plan, architecture diagrams, data flow, and tech stack decision are reviewed and accepted.

## Purpose

Codex builds the study app. That build process does not teach the learner the interview technologies. Learning happens when the finished app makes the learner answer questions, write code, revise mistakes, and explain trade-offs.

Keep Codex implementation tracking outside the app unless a tiny status note helps the learner know which study features are ready.

## Long-running session strategy

1. Convert docs into a backlog of vertical slices.
2. Start Codex cloud session for one slice only.
3. Keep each slice independently testable and committable.
4. Let the session run until completion or limit pause.
5. On limit reset, continue from the latest checkpoint rather than expanding scope.
6. Check build progress from phone through Codex/GitHub/chat status, not through a core study-app feature.

## Slice template

- Goal:
- Files expected to change:
- Acceptance criteria:
- Tests required:
- Manual review notes:
- Follow-up backlog:

## Ticket source of truth

Use [implementation-backlog.md](implementation-backlog.md) for epics, tickets, dependencies, and per-ticket plans. The list below is a historical slice outline; the backlog is the implementation queue to execute.

## Recommended initial slices

1. Scaffold the smallest local app shell that fits the accepted tech stack.
2. Add static curriculum/resource pages from docs.
3. Build dashboard layout and daily checklist with mock data.
4. Implement deterministic scheduling domain logic with tests.
5. Add flashcard/Q&A trainer.
6. Add exercise catalog and attempt tracking.
7. Add local persistence with JSON/localStorage.
8. Upgrade to SQLite only if attempt history and revision queries need it.
9. Add phone-friendly responsive layout for study use.
10. Add mock interview mode.
11. Add FastAPI, Flask, Next.js, and React Native practice modules as curriculum content.

## Phone build-progress update format

```text
Status: green/yellow/red
Current slice:
Done:
Blocked:
Tests:
Next checkpoint:
Needs human decision:
```

## Limit reset checklist

- Pull latest branch state.
- Read last checkpoint and failing tests.
- Continue the same slice unless acceptance criteria changed.
- Commit only coherent, tested progress.
- Update docs/backlog when scope changes.
