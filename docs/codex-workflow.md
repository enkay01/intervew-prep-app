# Codex Autonomous Implementation Workflow

## Rule: establish before implementation

No application code should be written until the requirements, resource map, July learning plan, architecture diagrams, data flow, and tech stack decision are reviewed and accepted.

## Long-running session strategy

1. Convert docs into a backlog of vertical slices.
2. Start Codex cloud session for one slice only.
3. Keep each slice independently testable and committable.
4. Let the session run until completion or limit pause.
5. On limit reset, continue from the latest checkpoint rather than expanding scope.
6. Check progress from phone using concise status updates.

## Slice template

- Goal:
- Files expected to change:
- Acceptance criteria:
- Tests required:
- Manual review notes:
- Follow-up backlog:

## Recommended initial slices

1. Scaffold Next.js + TypeScript app shell.
2. Add static curriculum/resource pages from docs.
3. Build dashboard layout and daily checklist with mock data.
4. Implement deterministic scheduling domain logic with tests.
5. Add flashcard/Q&A trainer.
6. Add exercise catalog and attempt tracking.
7. Add FastAPI service for exercises.
8. Add Flask comparison lab.
9. Add mobile progress view.
10. Add mock interview mode.

## Phone progress update format

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
