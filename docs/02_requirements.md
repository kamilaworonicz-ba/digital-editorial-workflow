# 2. Requirements: Editorial–DTP Revision Workflow

This document specifies the conceptual digital solution proposed for the pain points identified in [`01_problem_and_scenario.md`](./01_problem_and_scenario.md).

The proposed solution is an **Interactive Layout Preview** — a shared digital view of the current page layout that allows both roles to review composition and track corrections, while allowing the Managing Editor to trial-edit text before requesting a change.

---

## 2. 1. Functional Requirements

> Some requirements below combine several tightly coupled system behaviours into a single functional requirement, where splitting them would describe an incomplete or non-functional step in isolation.

<table>
  <tr>
    <th>ID</th>
    <th>AS-IS Pain Point</th>
    <th>Functional Requirement</th>
  </tr>

  <tr>
    <td><strong>FR-01</strong></td>
    <td>
      🔍 <strong>No live text fit-check.</strong>
      Even a small text correction requires DTP to update the layout before the Managing Editor can verify whether it works.
    </td>
    <td>
      The system shall allow the Managing Editor to trial-edit body text, headings and captions in the interactive layout preview and show whether the revised text fits the allotted space.
    </td>
  </tr>

  <tr>
    <td><strong>FR-02</strong></td>
    <td>
      🖨️ <strong>Paper-based page review.</strong>
      Reviewing text and visual composition requires repeated printing and physical handoffs between the Managing Editor and DTP Specialist.
    </td>
    <td>
          The system shall display the current page layout, including text, photographs, illustrations and captions, in a shared interactive preview accessible to both the Managing Editor and the DTP Specialist.
    </td>
  </tr>

  <tr>
    <td><strong>FR-03</strong></td>
    <td rowspan="2">
      📄 <strong>Corrections recorded across successive proofs.</strong>
      Required changes are distributed across separate marked-up proofs rather than managed as one coherent set of corrections.
    </td>
    <td>
      The system shall allow the Managing Editor to create correction annotations, consisting of a free-text description of the required correction, linked to text or visual elements with an initial status of `Open`. The DTP Specialist shall be able to mark them as `Resolved`, and the Managing Editor to reopen them if further correction is required.
    </td>
  </tr>

  <tr>
    <td><strong>FR-04</strong></td>
    <td>
   The system shall allow the DTP Specialist to update the interactive preview with the latest layout version while preserving existing correction annotations and their statuses.
    </td>
  </tr>

  <tr>
    <td><strong>FR-05</strong></td>
    <td>
      ❓ <strong>No consolidated view of outstanding corrections.</strong>
      Determining which corrections have been addressed and which still require attention requires manual comparison of successive proofs.
    </td>
    <td>
    The system shall provide both the Managing Editor and the DTP Specialist with a consolidated list of correction annotations for the current chapter, showing their status.
    </td>
  </tr>
</table>

---

## 2.2. Open Questions & Further Considerations

The following aspects were considered during the analysis but intentionally left outside the scope of this mini case study:

1. Should submitting trial-edited text automatically create a correction annotation?
2. What should happen to annotations if the associated text or visual element no longer exists in a new layout version?
3. Should the Managing Editor be able to manually reassign such annotations to another element?
4. Should resolved corrections remain visible in the layout, or only in the correction list?
5. Should users be able to filter corrections by status or other criteria?
6. Should the correction list provide direct navigation to the associated element in the layout?
7. Should previous layout versions and their corrections remain accessible?
---

## 2.3. Business Rules

### BR-01 — Trial Edit Scope
The Managing Editor may trial-edit body text, headings and captions in the interactive preview to evaluate text fit.

### BR-02 — Production File Ownership
Only the DTP Specialist applies accepted text, layout and visual changes to the production source file. Changes made in the interactive preview, including trial edits, do not modify the production source file.

### BR-03 — Correction Resolution
The DTP Specialist is responsible for marking an `Open` annotation `Resolved` only after applying the correction to the production source file. The system does not verify that the described correction has been made.

---

## 2.4. Example User Stories & Acceptance Criteria

### User Story — US-01: Managing Corrections

> **As a** Managing Editor,<br>
> **I want** to create, reopen and review correction annotations for the current chapter,<br>
> **so that** I can quickly identify which issues have been addressed and which still require attention.

```gherkin
Scenario: Creating a correction
  Given the Managing Editor is reviewing a text or visual element
  When the Managing Editor creates a correction annotation
  Then the annotation is linked to that element
  And its initial status is "Open"

Scenario: Reopening a correction
  Given an annotation has status "Resolved"
  When the Managing Editor reopens the annotation
  Then its status changes to "Open"

Scenario: Reviewing chapter corrections
  Given the chapter contains "Open" and "Resolved" annotations
  When the Managing Editor opens the correction list
  Then all correction annotations for the current chapter are displayed
  And each annotation is displayed with its current status
```
**Related requirements:** FR-03, FR-05 

---

### User Story — US-02: Handling Annotated Corrections

> **As a** DTP Specialist,<br>
> **I want** to see requested corrections at the relevant text or visual elements in the current page layout, <br>
> **so that** I can apply them accurately without relying on marked-up printed proofs.

```gherkin
Scenario: Reviewing a requested correction
  Given the Managing Editor has created an "Open" annotation linked to a text or visual element
  When the DTP Specialist opens the shared Interactive Layout Preview
  Then the current page layout is displayed
  And the annotation is visible at the relevant element

Scenario: Completing a requested correction
  Given the DTP Specialist has applied the requested correction to the production source file
  When the DTP Specialist marks the annotation as "Resolved"
  Then the annotation status changes from "Open" to "Resolved"
  And the updated status is visible to the Managing Editor
```

**Related requirements:** BR-02, BR-03, FR-02, FR-03, FR-05

---

### User Story — US-03: Text Fit Check

> **As a** Managing Editor,  <br>
> **I want** to trial-edit text directly in the Interactive Layout Preview,  <br>
> **so that** I can check whether a proposed wording change fits before asking the DTP Specialist to apply it to the production file.

```gherkin
Scenario: Checking whether revised text fits
  Given the Managing Editor is reviewing a text element in the Interactive Layout Preview
  When the Managing Editor trial-edits the text
  Then the system shows whether the revised text fits the allotted space
  And the trial edit is visible only to the Managing Editor
  And the production source file remains unchanged
```

**Related requirements:** BR-01, BR-02, FR-01

### User Story — US-04: Updating the Layout Preview

> **As a** DTP Specialist,<br>
> **I want** to update the interactive preview with the latest production layout,<br>
> **so that** the Managing Editor can review the current version while existing corrections remain traceable.

```gherkin
Scenario: Updating the preview with a new layout version
  Given the Interactive Layout Preview contains existing correction annotations
  When the DTP Specialist updates the preview with the latest production layout
  Then the latest layout is displayed
  And existing correction annotations are preserved
  And they retain their current status
```

**Related requirements:** FR-04

---

## 2.5. Requirements Traceability Summary

<table>
  <tr>
    <th>Pain point</th>
    <th>Functional requirement</th>
    <th>Business Rule</th>
    <th>User Story</th>
  </tr>

  <tr>
    <td>🔍 <strong>No live text fit-check</strong></td>
    <td>FR-01</td>
    <td>BR-01, BR-02</td>
    <td>US-03</td>
  </tr>

  <tr>
    <td>🖨️ <strong>Paper-based page review</strong></td>
    <td>FR-02</td>
    <td>—</td>
    <td>US-02</td>
  </tr>

  <tr>
    <td rowspan="2">📄 <strong>Corrections recorded across successive proofs</strong></td>
    <td>FR-03</td>
    <td>BR-03</td>
    <td>US-02</td>
  </tr>

  <tr>
    <td>FR-04</td>
    <td>—</td>
    <td>US-04</td>
  </tr>

  <tr>
    <td>❓ <strong>No consolidated view of outstanding corrections</strong></td>
    <td>FR-05</td>
    <td>—</td>
    <td>US-01</td>
  </tr>
</table>

---

### 2.6. Illustrative NFRs

> The values below are illustrative acceptance targets and would require validation with stakeholders and the technical team.

| ID | Category | Illustrative NFR |
|---|---|---|
| NFR-01|	Performance	| The interactive layout preview shall load within 3 seconds, consistent with common UX benchmarks for perceived responsiveness. |
| NFR-02 | Performance | Annotations shall sync in near real-time (target: within 1 second) to support simultaneous review — informed by experience with a similar internal tool, where slower refresh times were a recurring source of user frustration.|
| NFR-03 | Usability | A Managing Editor or DTP Specialist shall be able to locate an open correction and navigate to its position in the layout within three user interactions from the correction list. |

---

[README →](../README.md) · [01 Problem & Scenario →](./01_problem_and_scenario.md) · **02 Requirements** · [03 Process Diagrams →](./03_process_diagrams.md) · [Additional editorial processes →](../additional_editorial_processes.md)

