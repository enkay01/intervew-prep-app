# Implementation Backlog

This backlog turns the establish docs into mergeable implementation work. Each epic should produce a useful app state on its own. Each ticket is sized for one agent and includes acceptance criteria that one agent can verify without hidden context.

## Working rules

- Build local-first. Do not add auth, hosted databases, payments, classrooms, or production deployment.
- Prefer Vite, React, TypeScript, and plain CSS for the app shell unless a ticket explicitly says otherwise.
- Use deterministic logic before optional AI.
- Keep each ticket independently testable and committable.
- Use the linked plan for the ticket before changing code.

## Epic E1: Local App Foundation and Curriculum Browser

**Value if merged:** The learner can open the app locally, navigate a real study shell, and browse the core curriculum/resources before any tracking features exist.

| Ticket | Title | Plan | Depends on |
| --- | --- | --- | --- |
| IP-001 | App shell and navigation | [Plan](plans/2026-06-30-ip-001-app-shell.md) | None |
| IP-002 | Curriculum data and resource library | [Plan](plans/2026-06-30-ip-002-curriculum-library.md) | IP-001 |

## Epic E2: Daily Study Loop

**Value if merged:** The learner can set study constraints, see today's work, mark tasks complete, and trust that weak topics come back for revision.

| Ticket | Title | Plan | Depends on |
| --- | --- | --- | --- |
| IP-003 | Learner profile and baseline assessment | [Plan](plans/2026-06-30-ip-003-profile-baseline.md) | IP-001 |
| IP-004 | Daily plan dashboard and task completion | [Plan](plans/2026-06-30-ip-004-daily-dashboard.md) | IP-002, IP-003 |
| IP-005 | Revision scheduler and progress metrics | [Plan](plans/2026-06-30-ip-005-revision-progress.md) | IP-004 |

## Epic E3: Practice Tools

**Value if merged:** The learner can practice interview answers and coding tasks inside the app, with attempts feeding future revision.

| Ticket | Title | Plan | Depends on |
| --- | --- | --- | --- |
| IP-006 | Flashcard and Q&A trainer | [Plan](plans/2026-06-30-ip-006-qa-trainer.md) | IP-002, IP-005 |
| IP-007 | Coding exercise catalog and attempts | [Plan](plans/2026-06-30-ip-007-coding-attempts.md) | IP-002, IP-005 |

## Epic E4: Interview Readiness Review

**Value if merged:** The learner can run mock interviews, score performance, and leave each mock with concrete remediation work.

| Ticket | Title | Plan | Depends on |
| --- | --- | --- | --- |
| IP-008 | Mock interview mode and weekly review | [Plan](plans/2026-06-30-ip-008-mock-review.md) | IP-006, IP-007 |

## Epic E5: Data Durability and Lightweight Access

**Value if merged:** The learner can keep study data safe, move it between machines, and optionally publish the static app shell for phone access.

| Ticket | Title | Plan | Depends on |
| --- | --- | --- | --- |
| IP-009 | Local backup, restore, and static build | [Plan](plans/2026-06-30-ip-009-backup-static-build.md) | IP-008 |

## MVP release line

The first practical MVP is complete when IP-001 through IP-007 are merged. IP-008 and IP-009 make the tool safer and more interview-ready, but the daily learning loop is useful before them.

## Ticket acceptance standard

Every ticket must include:

- User-visible value tied to the epic.
- Clear acceptance criteria.
- At least one automated verification command, unless the repo has no runnable app yet.
- Manual verification steps for the workflow.
- No unrelated refactors.
- Updated docs when behavior or ticket sequencing changes.
