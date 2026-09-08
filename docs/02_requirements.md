# 2. Requirements: Editorial–DTP Revision Workflow

This document specifies the conceptual digital solution proposed for the pain points identified in [`01_problem_and_scenario.md`](./01_problem_and_scenario.md).

The proposed solution is an **Interactive Layout Preview** — a shared digital view of the current page layout that allows both roles to review composition and track corrections, while allowing the Managing Editor to trial-edit text before requesting a change.

---

## 2.1. Functional Requirements

> For conciseness, closely related system behaviours are grouped into a small number of functional requirements.

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
     The Managing Editor cannot verify whether revised text fits the available space without an updated layout from the DTP Specialist.
    </td>
    <td>
      The system shall allow the Managing Editor to trial-edit body text, headings and captions in the Interactive Layout Preview and show whether the revised text fits the allotted space.
    </td>
  </tr>

  <tr>
    <td><strong>FR-02</strong></td>
    <td>
      🖨️ <strong>Paper-based page review.</strong>
      Reviewing text and visual composition requires repeated printing and physical handoffs between the Managing Editor and DTP Specialist.
    </td>
    <td>
          The system shall display the current page layout, including text, photographs, illustrations and captions, in a shared Interactive Layout Preview accessible to both the Managing Editor and the DTP Specialist.
    </td>
  </tr>

  <tr>
    <td><strong>FR-03</strong></td>
    <td rowspan="2">
      📄 <strong>Corrections recorded across successive proofs.</strong>
      Required changes are distributed across separate marked-up proofs rather than managed as one coherent set of corrections.
    </td>
    <td>
         The system shall allow the Managing Editor to create correction annotations with a free-text description, linked to text or visual elements. New annotations shall have an initial status of `Open`, and the DTP Specialist shall be able to mark them as `Resolved`.
    </td>
  </tr>

  <tr>
    <td><strong>FR-04</strong></td>
    <td>
   The system shall allow the DTP Specialist to update the Interactive Layout Preview with the latest layout version while preserving existing correction annotations and their statuses.
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

## 2.2. Business Rules

### BR-01 — Production File Ownership
Only the DTP Specialist applies accepted text, layout and visual changes to the production source file. Changes made in the Interactive Layout Preview, including trial edits, do not modify the production source file.

### BR-02 — Correction Resolution
The DTP Specialist is responsible for marking an `Open` annotation `Resolved` only after applying the correction to the production source file. The system does not verify that the described correction has been made.

---

## 2.3. Open Questions & Further Considerations

<details>
The following aspects were considered during the analysis but intentionally left outside the scope of this mini case study:

1. **Trial edit → correction creation (FR-01, FR-03):** Should submitting trial-edited text automatically create a correction annotation, or should annotation creation remain a separate action?
2. **Lost annotation association after layout update (FR-03, FR-04):** If a text or visual element associated with an annotation no longer exists in an updated layout, should the annotation remain unassigned, be automatically reassigned where possible, or require manual reassignment by the Managing Editor?
3. **Visibility of resolved corrections (FR-05, BR-02):** After an annotation is marked `Resolved`, should it remain visible in the Interactive Layout Preview, remain accessible only through the correction list, or be hidden entirely?
4. **Correction list filtering (FR-05):** Should the correction list support filtering by annotation status or other criteria?
5. **Navigation from correction list to layout (FR-05):** Should selecting an annotation in the correction list navigate the user directly to the associated text or visual element in the Interactive Layout Preview?
6. **Access to previous layout versions (FR-04):** Should previous layout versions remain accessible after the DTP Specialist updates the Interactive Layout Preview with the latest layout version, and if so, should their associated correction annotations also remain available?
7. **Reopening resolved corrections (FR-03, BR-02):** Should the Managing Editor be able to reopen an annotation after the DTP Specialist has marked it `Resolved`, and under what conditions?
8. **Annotation target scope (FR-03):** Should correction annotations be limited to text and visual elements, or should additional element types be supported?
9. **Concurrent editing and layout updates (FR-01, FR-03, FR-04):** What should happen if the Managing Editor is trial-editing text or creating an annotation while the DTP Specialist updates the Interactive Layout Preview with the latest layout version — should the in-progress work be preserved and reapplied, discarded, or temporarily blocked during the update?

</details>

---

## 2.4. Example User Stories & Acceptance Criteria

### User Story — US-01: Creating a correction

> **As a** Managing Editor,<br>
> **I want** to create correction annotations,<br>
> **so that** I can request corrections.

<details>
<summary>Zobacz pełny scenariusz Gherkin dla US-01</summary>

```gherkin
Scenario: Creating a correction
  Given the Managing Editor is reviewing a text or visual element
  When the Managing Editor creates a correction annotation with a free-text description
  Then the annotation is linked to that element
  And its initial status is "Open"
```
**Related requirements:** FR-03
</details>

### User Story — US-02: Reviewing the consolidated corrections list

> **As a** \<role\>,<br>
> **I want** to review correction annotations for the current chapter,<br>
> **so that** I can quickly identify which issues have been addressed and which still require attention.

<details>
<summary>Zobacz pełny scenariusz Gherkin dla US-02</summary>

```gherkin
Scenario Outline: Reviewing the consolidated corrections list
  Given the chapter contains "Open" and "Resolved" annotations
  When the <role> opens the correction list
  Then all correction annotations for the current chapter are displayed
  And each annotation is displayed with its current status

Examples:
    | role              |
    | Managing Editor   |
    | DTP Specialist    |
```
**Related requirements:** FR-05
</details>

### User Story — US-03: Applying and resolving corrections in the layout

> **As a** DTP Specialist,<br>
> **I want** to see requested corrections at the relevant text or visual elements in the current page layout, <br>
> **so that** I can apply them accurately without relying on marked-up printed proofs.

<details>
<summary>Zobacz pełny scenariusz Gherkin dla US-03</summary>

```gherkin
Scenario: Reviewing a requested correction
  Given the Managing Editor has created an "Open" annotation linked to a text or visual element
  When the DTP Specialist opens the shared Interactive Layout Preview
  Then the annotation marker is rendered anchored to that specific text/visual element (not merely present on the page)

Scenario: Completing a requested correction
  Given the DTP Specialist has applied the requested correction to the production source file
  When the DTP Specialist marks the annotation as "Resolved"
  Then the annotation status changes from "Open" to "Resolved"
  And the updated status is visible to the Managing Editor
```
**Related requirements:** BR-02, FR-02, FR-03
</details>

### User Story — US-04: Checking whether revised text fits

> **As a** Managing Editor,  <br>
> **I want** to trial-edit text directly in the Interactive Layout Preview,  <br>
> **so that** I can check whether a proposed wording change fits before asking the DTP Specialist to apply it to the production file.

<details>
<summary>Zobacz pełny scenariusz Gherkin dla US-04</summary>

```gherkin
Scenario: Checking whether revised text fits
  Given the Managing Editor is reviewing body text, a heading or a caption
  When the Managing Editor trial-edits the text
  Then the system shows whether the revised text fits the allotted space
  And the production source file remains unchanged
```
**Related requirements:** BR-01, FR-01
</details>

### User Story — US-05: Updating the preview with a new layout version

> **As a** DTP Specialist,<br>
> **I want** to update the Interactive Layout Preview with the latest production layout,<br>
> **so that** the Managing Editor can review the current version while existing corrections remain traceable.

<details>
<summary>Zobacz pełny scenariusz Gherkin dla US-05</summary>

```gherkin
Scenario: Updating the preview with a new layout version
  Given the Interactive Layout Preview contains existing correction annotations
  When the DTP Specialist updates the preview with the latest production layout
  Then the latest layout is displayed
  And existing correction annotations are preserved
  And they retain their current status
```
**Related requirements:** FR-04, FR-02
</details>

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
    <td>BR-01</td>
    <td>US-04</td>
  </tr>

  <tr>
    <td>🖨️ <strong>Paper-based page review</strong></td>
    <td>FR-02</td>
    <td>—</td>
    <td>US-03, US-05</td>
  </tr>

  <tr>
    <td rowspan="2">📄 <strong>Corrections recorded across successive proofs</strong></td>
    <td>FR-03</td>
    <td>BR-02</td>
    <td>US-01, US-03</td>
  </tr>

  <tr>
    <td>FR-04</td>
    <td>—</td>
    <td>US-05</td>
  </tr>

  <tr>
    <td>❓ <strong>No consolidated view of outstanding corrections</strong></td>
    <td>FR-05</td>
    <td>—</td>
    <td>US-02</td>
  </tr>
</table>

---

### 2.6. Illustrative NFRs

> The values below are illustrative acceptance targets and would require validation with stakeholders and the technical team.

| ID |  Illustrative NFR |
|---|---|
| NFR-01|	 The Interactive Layout Preview shall load within 3 seconds, consistent with common UX benchmarks for perceived responsiveness. |
| NFR-02 | Annotations shall sync in near real-time (target: within 1 second) to support simultaneous review — informed by experience with a similar internal tool, where slower refresh times were a recurring source of user frustration.|

---

[README →](../README.md) · [01 Problem & Scenario →](./01_problem_and_scenario.md) · **02 Requirements** · [03 Process Diagrams →](./03_process_diagrams.md) · [Additional editorial processes →](../additional_editorial_processes.md)

