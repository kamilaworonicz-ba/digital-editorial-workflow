# 1. Problem & Scenario: Editorial–DTP Revision Workflow

## 1.1. AS-IS Problem

This case study covers the revision loop from the initial page layout to the point when the materials are ready for teacher focus testing.

Once a manuscript was typeset for the first time, it entered an iterative revision loop between the **Managing Editor** and the **DTP Specialist**.
The workflow was primarily **paper-based** 🖍. DTP Specialist produced a printed proof, the Managing Editor reviewed the layout and marked corrections by hand, and the marked-up pages were returned to DTP Specialist for another revision.

This created several recurring problems:
- 🔍 **No live text fit-check.**  Even a small text correction requires DTP Specialist to update the layout before the Managing Editor can verify whether it works.
- 🖨️ **Paper-based page review.** Reviewing text and visual composition requires repeated printing and physical handoffs.
- 📄 **Corrections recorded across successive proofs.** Required changes are difficult to manage as one coherent set of issues.
- ❓ **No consolidated view of outstanding corrections.**  The Managing Editor must manually determine which corrections have been completed and which still require attention.

These pain points provide the basis for the functional requirements defined in [`02_requirements.md`](./02_requirements.md).

| Actor |  Role |
|---|---|
| **Managing Editor** |  Reviews successive layout versions, identifies and marks required changes, and confirms readiness for teacher focus testing |
| **DTP Specialist (Desktop Publishing Specialist)** | Prepares and updates the typeset page layout, places visual assets and applies editorial changes to the source file |

---

## 1.2. Illustrative Scenario

The sequence below illustrates a typical revision path rather than a fixed number of rounds. Text, caption and visual issues could overlap and reappear across multiple iterations.

```mermaid
flowchart LR
    A["First DTP layout"] --> B["Managing Editor reviews chapter layout"]
    B --> C{"Corrections required?"}
    C -- Yes --> D["Mark text, caption or visual corrections"]
    D --> E["DTP Specialist updates source layout"]
    E --> B
    C -- No --> F["Chapter ready for teacher focus testing"]

    style D fill:#c0392b,stroke:#333,stroke-width:2px,color:#fff
    style F fill:#2e7d32,stroke:#333,stroke-width:2px,color:#fff
```

<p align="center"><em>Figure 1. AS-IS Editorial–DTP Revision Workflow.</em></p>

---
[README →](../README.md) · **01 Problem & Scenario** · [02 Requirements →](./02_requirements.md) · [03 Process Diagrams →](./03_process_diagrams.md) · [Additional editorial processes →](../additional_editorial_processes.md)



