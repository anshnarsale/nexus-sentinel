# Agent State Lifecycle

```mermaid
graph TD
  A[Plan] --> B[Dispatch]
  B --> C[Execute]
  C --> D{Evaluate}
  D -- Pass --> E[Done]
  D -- Fail --> A
```
