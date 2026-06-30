# Architecture, Data Flow, and System Diagrams

## System context

```mermaid
flowchart LR
  Learner["Learner"] --> App["Personal Study App"]
  App --> Storage[("Local Storage / JSON / SQLite")]
  App --> Scheduler["Plan + Revision Logic"]
  App --> Resources["Curated Resource Metadata"]
  App --> Practice["Q&A, Flashcards, Coding Prompts"]
  Learner --> Phone["Optional Phone Browser"]
  Phone --> App
```

## Container architecture

```mermaid
flowchart TB
  subgraph LocalApp["Local-first app"]
    UI["Responsive study UI"]
    Planner["Daily planner and revision queue"]
    Trainer["Flashcards, Q&A, mock interview checklists"]
    Exercises["Exercise catalog and attempt forms"]
  end

  subgraph Data
    LocalStore[("localStorage / JSON")]
    SQLite[("SQLite after MVP")]
    Backup["Manual Markdown/JSON backup"]
  end

  subgraph StudyContent["Interview practice content"]
    ReactNext["React / Next.js / TypeScript tasks"]
    PythonAPIPractice["FastAPI / Flask tasks"]
    NativePractice["React Native tasks"]
  end

  UI --> Planner
  UI --> Trainer
  UI --> Exercises
  Planner --> LocalStore
  Trainer --> LocalStore
  Exercises --> LocalStore
  LocalStore -. upgrade when needed .-> SQLite
  LocalStore --> Backup
  Exercises --> StudyContent
```

## Core data model

```mermaid
erDiagram
  LEARNER_PROFILE ||--o{ STUDY_SESSION : completes
  LEARNER_PROFILE ||--o{ ATTEMPT : submits
  LEARNER_PROFILE ||--o{ MOCK_INTERVIEW : takes
  TECHNOLOGY ||--o{ TOPIC : contains
  TOPIC ||--o{ RESOURCE : references
  TOPIC ||--o{ FLASHCARD : drills
  TOPIC ||--o{ EXERCISE : practices
  EXERCISE ||--o{ ATTEMPT : receives
  STUDY_SESSION ||--o{ STUDY_TASK : includes
  STUDY_TASK }o--|| TOPIC : targets

  LEARNER_PROFILE {
    string id
    string target_role
    int daily_hours
    string interview_month
  }
  TECHNOLOGY {
    string id
    string name
    int priority
  }
  TOPIC {
    string id
    string technology_id
    string name
    string interview_weight
  }
  EXERCISE {
    string id
    string topic_id
    string type
    int estimated_minutes
    string difficulty
  }
  ATTEMPT {
    string id
    string exercise_id
    int score
    string confidence
    datetime next_revision_at
  }
```

## Daily plan generation flow

```mermaid
sequenceDiagram
  participant User
  participant UI as Study UI
  participant Scheduler
  participant Store as Local Store

  User->>UI: Open today's plan
  UI->>Store: Load readiness, attempts, revision debt
  UI->>Scheduler: Build plan for available hours
  Scheduler->>Scheduler: Prioritize weak high-value topics
  Scheduler->>Scheduler: Add revision from prior mistakes
  Scheduler->>Store: Save study session and tasks
  UI-->>User: Show daily checklist
```

## Exercise attempt flow

```mermaid
flowchart TD
  A["Choose exercise"] --> B["Read prompt and timer"]
  B --> C["Write solution"]
  C --> D["Run tests or self-check rubric"]
  D --> E["Submit attempt"]
  E --> F["Score accuracy, time, confidence"]
  F --> G{"Passed confidently?"}
  G -- Yes --> H["Schedule light revision"]
  G -- No --> I["Schedule near-term revision and remediation"]
  H --> J["Update readiness score"]
  I --> J
```

## Codex autonomous implementation flow

Codex progress is about building the app, not studying for interviews. It should live in project notes, commits, PRs, or chat updates. The study app may include a small "what changed" note only if that helps the learner know which study features are ready to use.

```mermaid
flowchart LR
  Backlog["Established docs + backlog"] --> Slice["Select small vertical slice"]
  Slice --> Codex["Codex cloud session"]
  Codex --> Checkpoint["Commit + tests + notes"]
  Checkpoint --> Phone["Phone check of Codex/chat status"]
  Phone --> Decision{"Continue after limit reset?"}
  Decision -- Yes --> Slice
  Decision -- No --> Review["Manual review + merge"]
```

## Optional AI assistance

AI integrations should support practice, not infrastructure. Good uses are follow-up interview questions, concise answer feedback, weak-topic summaries, and daily-plan adjustments. MVP features should work without AI so the study loop stays reliable.

## Architecture principles

- Keep interview curriculum data separate from presentation so plans can be regenerated.
- Make scheduling/scoring deterministic and testable before considering AI enhancements.
- Use AI only where it directly improves study: generating follow-up questions, drafting answer rubrics, or summarizing weak spots. Keep the learner's active recall and coding practice central.
- Do not add auth, hosted databases, queues, background jobs, or production deployment until a real single-user need appears.
- Prefer small vertical slices that can be built and reviewed independently by long-running Codex sessions.
