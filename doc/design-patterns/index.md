# Design Patterns

There are some design patterns to:

1. Router
2. Skills
3. Subagents
4. Handoffs

## Summary

| Pattern Name | Core Behavior | State / Memory Management | Best Used For |
| :--- | :--- | :--- | :--- |
| **1. Router** | A dedicated step classifies the query, triggers specialized vertical agents, and merges the results. | **Isolated / Stateless:** No shared history between parallel routes. | Querying distinct enterprise knowledge bases simultaneously. |
| **2. Subagents** | A main supervisor agent dynamically delegates subtasks to subagents and retains full context. | **Semi-Shared:** History is managed and filtered by the main supervisor. | Open-ended reasoning tasks requiring centralized management. |
| **3. Handoffs** | Agents execute their tasks sequentially and transfer control to another agent. | **Sequential Handoff:** State and message threads transfer cleanly down the chain. | Tiered customer support escalations or structured multi-stage pipelines. |
| **4. Skills** | A single conversational agent dynamically shifts its behavior by changing tools/instructions. | **Fully Shared:** Single state schema and message pool for the entire run. | Lightweight bots needing highly centralized but flexible skills. |
