# Architecture

```mermaid
  graph TB
      A(Agent) -->|Fetch jobs| B[Data source]
      subgraph INTERNAL
          A(Agent) -->|Push new jobs| C>Queue]
          D(Manager) -->|Pull jobs| C>Queue]
          D(Manager) -->|Send jobs events| F(Notification Service)
          D(Manager) -->|Store jobs| E((Database))
          F(Notifier) -->|Send message| G(Discord)
          F(Notifier) -->|Send message| H(Slack)
          F(Notifier) -->|Send message| I(Email)
      end
          J(API) -->|Query jobs| E((Database))
          K(Website) -->|Display jobs| J(API)
```