# Let AI continuously review the codebase

This is where I think your idea gets particularly interesting.

Instead of using AI only when developing features, how about we create a Codebase Health Agent.

Something like:

  ```mermaid
graph TD
    GIT[Git Repository] --> AGENT[Code Health Agent]
    
    %% Split to Metrics
    AGENT --> COMP[Complexity]
    AGENT --> DUP[Duplication]
    AGENT --> ARCH[Architecture]
    
    %% Metrics to Sub-metrics
    COMP --> DEAD[Dead code]
    DUP --> ABS[Abstractions]
    ARCH --> DEP[Dependencies]
    
    %% Merge to Report
    DEAD --> REP[Health Report]
    ABS --> REP
    DEP --> REP
    
    %% Report to Cleanups
    REP --> CLEAN[Suggested cleanups]
```

It could periodically report:

CODEBASE HEALTH

Complexity:        ⚠ 3 functions increasing
Duplication:       ✓ Low
Dependencies:      ⚠ 2 unused dependencies
Dead code:         ⚠ 4 candidates
Architecture:      ✓ Healthy
Test coverage:     ✓ 87%
Large modules:     ⚠ 2
AI-generated risk: ⚠ 5 recent changes need review

Suggested actions:

1. Simplify Collab Session Ingestion flow
2. Remove duplicated validation logic
3. Consolidate DateUtils
4. Add tests for retry behavior

Importantly, the agent shouldn't automatically refactor everything.

It should create proposals/PRs.

Human approves.
