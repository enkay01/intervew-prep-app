# Architecture, Data Flow, and System Diagrams

## System context

```mermaid
flowchart LR
  Learner["Learner"] --> Web["Interview Prep Web App"]
  Web --> Auth["Auth Provider"]
  Web --> API["Application API"]
  API --> DB[("PostgreSQL")]
  API --> Queue["Background Jobs"]
  Queue --> Scheduler["Plan + Revision Scheduler"]
  API --> Resources["Curated Resource Metadata"]
  API --> CodexLog["Codex Session Log"]
  Learner --> Phone["Phone Progress View"]
  Phone --> Web
```

## Container architecture

```mermaid
flowchart TB
  subgraph Client
    NextUI["Next.js UI"]
    MobileView["Responsive phone dashboard"]
  end

  subgraph Backend
    ApiRoutes["Next.js API/BFF routes"]
    PythonAPI["FastAPI learning/exercise service"]
    FlaskLabs["Flask comparison labs"]
    Worker["Scheduler worker"]
  end

  subgraph Data
    Postgres[("PostgreSQL")]
    ObjectStore[("Exports and artifacts")]
  end

  NextUI --> ApiRoutes
  MobileView --> ApiRoutes
  ApiRoutes --> PythonAPI
  PythonAPI --> Postgres
  FlaskLabs --> Postgres
  Worker --> Postgres
  Worker --> ObjectStore
```

## Core data model

```mermaid
erDiagram
  USER ||--o{ STUDY_SESSION : completes
  USER ||--o{ ATTEMPT : submits
  USER ||--o{ MOCK_INTERVIEW : takes
  TECHNOLOGY ||--o{ TOPIC : contains
  TOPIC ||--o{ RESOURCE : references
  TOPIC ||--o{ FLASHCARD : drills
  TOPIC ||--o{ EXERCISE : practices
  EXERCISE ||--o{ ATTEMPT : receives
  STUDY_SESSION ||--o{ STUDY_TASK : includes
  STUDY_TASK }o--|| TOPIC : targets
  CODEX_SESSION ||--o{ CODEX_CHECKPOINT : reports

  USER {
    uuid id
    string email
    string target_role
    int daily_hours
  }
  TECHNOLOGY {
    uuid id
    string name
    int priority
  }
  TOPIC {
    uuid id
    uuid technology_id
    string name
    string interview_weight
  }
  EXERCISE {
    uuid id
    uuid topic_id
    string type
    int estimated_minutes
    string difficulty
  }
  ATTEMPT {
    uuid id
    uuid user_id
    uuid exercise_id
    int score
    string confidence
    datetime next_revision_at
  }
```

## Daily plan generation flow

```mermaid
sequenceDiagram
  participant User
  participant UI as Next.js UI
  participant API as App API
  participant Scheduler
  participant DB as PostgreSQL

  User->>UI: Open today's plan
  UI->>API: GET /daily-plan
  API->>DB: Load readiness, attempts, revision debt
  API->>Scheduler: Build plan for available hours
  Scheduler->>Scheduler: Prioritize weak high-value topics
  Scheduler->>Scheduler: Add revision from prior mistakes
  Scheduler->>DB: Persist study session and tasks
  API-->>UI: Return tasks, timings, and success criteria
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

```mermaid
flowchart LR
  Backlog["Established docs + backlog"] --> Slice["Select small vertical slice"]
  Slice --> Codex["Codex cloud session"]
  Codex --> Checkpoint["Commit + tests + notes"]
  Checkpoint --> Phone["Phone progress check"]
  Phone --> Decision{"Continue after limit reset?"}
  Decision -- Yes --> Slice
  Decision -- No --> Review["Manual review + merge"]
```

## Architecture principles

- Keep interview curriculum data separate from presentation so plans can be regenerated.
- Make scheduling/scoring deterministic and testable before adding AI enhancements.
- Use the platform itself as a portfolio project demonstrating React, Next.js, TypeScript, FastAPI, and Flask knowledge.
- Prefer small vertical slices that can be built and reviewed independently by long-running Codex sessions.
