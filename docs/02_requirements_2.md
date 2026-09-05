# 2. Requirements & Specification

This document specifies the conceptual digital solution proposed for the pain points identified in [`01_problem_and_scenario.md`](./01_problem_and_scenario.md).

The proposed solution is an **Interactive Layout Preview** — a shared digital view of the current page layout that allows both roles to review composition and track corrections, while allowing the Managing Editor to trial-edit text before requesting a change.

---

## 2. 1. Functional Requirements

> The functional requirements below were derived from the pain points identified in the AS-IS workflow. All five are considered in scope for the proposed MVP.
> 
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
The system shall allow the Managing Editor to trial-edit text, including body text, headings and captions, directly in the interactive layout preview. The system shall show whether the revised text fits the allotted space. The Managing Editor shall be able to submit the proposed text as a requested correction regardless of whether it fits. Where the text does not fit, the resulting correction shall be flagged as requiring a layout adjustment.
    </td>
  </tr>

  <tr>
    <td><strong>FR-02</strong></td>
    <td>
      🖨️ <strong>Paper-based page review.</strong>
      Reviewing text and visual composition requires repeated printing and physical handoffs between the Managing Editor and DTP Specialist.
    </td>
    <td>
      The system shall display the complete current page layout, including text, photographs, illustrations and captions, in a shared interactive preview accessible to both the Managing Editor and the DTP Specialist.
    </td>
  </tr>

  <tr>
    <td><strong>FR-03</strong></td>
    <td rowspan="2">
      📄 <strong>Corrections recorded across successive proofs.</strong>
      Required changes are distributed across separate marked-up proofs rather than managed as one coherent set of corrections.
    </td>
    <td>
      The system shall allow the Managing Editor to create an annotation — linked to a text or visual element, or automatically generated from submitted trial-edited text — describing the required correction, with an initial status of `Open`. The system shall allow the DTP Specialist to mark an annotation `Resolved`, and the Managing Editor to reopen it if further correction is required.
    </td>
  </tr>

  <tr>
    <td><strong>FR-05</strong></td>
    <td>
     The system shall allow the DTP Specialist to update the interactive preview with the latest version of the production layout, while preserving existing annotations, their statuses and their association with the relevant text or visual elements. If the element associated with an `Open` annotation is no longer available after the update, the annotation shall remain `Open` and be flagged for reassignment. If the element associated with a `Resolved` annotation is no longer available, the annotation shall remain `Resolved` and accessible from the correction list, but shall no longer be displayed in the current layout.
    </td>
  </tr>

  <tr>
    <td><strong>FR-04</strong></td>
    <td>
      ❓ <strong>No consolidated view of outstanding corrections.</strong>
      Determining which corrections have been addressed and which still require attention requires manual comparison of successive proofs.
    </td>
    <td>
     The system shall provide both the Managing Editor and the DTP Specialist with a consolidated list of annotations for the current chapter, showing their status, allowing filtering by status and providing direct navigation to the associated text or visual element where that element is available in the current layout.
    </td>
  </tr>
</table>

---

## 2.2. Business Rules

### BR-01 — Trial Edit Scope
The Managing Editor may trial-edit body text, headings and captions in the interactive preview to evaluate text fit and submit it as a requested correction. Trial edits are visible only to the Managing Editor and are not shared with the DTP Specialist unless submitted as a requested correction. The Managing Editor cannot reposition, resize or otherwise modify layout or visual elements in the preview.

### BR-02 — Production File Ownership
Only the DTP Specialist applies accepted text, layout and visual changes to the production source file. Changes made in the interactive preview do not modify the production source file.

### BR-03 — Correction Resolution
The DTP Specialist may change an annotation's status from `Open` to `Resolved` only after applying the requested correction to the production source file.

---

## 2.3. Example User Stories & Acceptance Criteria

### User Story — US-01: Tracking Open Corrections

> **As a** Managing Editor,<br>
> **I want** to see all corrections raised for the current chapter together with their status,<br>
> **so that** I can quickly identify which issues have been addressed by DTP and which still require attention.

```gherkin
Feature: Correction Tracking

Scenario: Reviewing outstanding corrections
  Given the chapter contains "Open" and "Resolved" annotations
  When the Managing Editor opens the correction list
  Then each annotation is displayed with its current status
  And the Managing Editor can filter the list to show only "Open" annotations
  And selecting an annotation whose associated element is available takes the Managing Editor to that element in the Interactive Layout Preview
```
**Related requirements:** BR-03, FR-03, FR-04 

---

### User Story — US-02: Handling Annotated Corrections

> **As a** DTP Specialist,<br>
> **I want** to see requested corrections directly at the relevant text or visual elements in the current page layout, including their description, <br>
> **so that** I can apply them accurately without relying on marked-up printed proofs.

```gherkin
Feature: Handling Annotated Corrections

Scenario: Reviewing a requested correction
  Given the Managing Editor has created an "Open" annotation in the current chapter layout
  When the DTP Specialist opens the shared Interactive Layout Preview
  Then the complete current page layout is displayed
  And the annotation is visible at the location where the correction is required
  And the annotation displays the description of the requested correction
  And the DTP Specialist can navigate to the associated element from the correction list

Scenario: Completing a requested correction
  Given the DTP Specialist has applied the requested correction to the production source file
  When the DTP Specialist marks the annotation as "Resolved"
  Then the annotation status changes from "Open" to "Resolved"
  And the updated status is visible to the Managing Editor
```

**Related requirements:** BR-02, BR-03, FR-02, FR-03, FR-04

---

### User Story — US-03: Text Fit Check

> **As a** Managing Editor,  <br>
> **I want** to trial-edit text directly in the Interactive Layout Preview,  <br>
> **so that** I can check whether a proposed wording change fits before asking the DTP Specialist to apply it to the production file.

```gherkin
Feature: Text Fit Check

Scenario: Checking whether revised text fits
  Given the Managing Editor is reviewing a text element in the Interactive Layout Preview
  When the Managing Editor edits the text
  Then the system shows whether the revised text fits
  And the trial edit is visible only to the Managing Editor
  And the production source file remains unchanged

Scenario: Attempting to modify the layout
  Given the Managing Editor is using the Interactive Layout Preview
  When the Managing Editor attempts to move or resize an image
  Then the action is not available


Scenario: Submitting a trial-edited text as a correction
  Given the Managing Editor has trial-edited a text element
  And the revised text fits the allotted space
  When the Managing Editor submits the proposed text change
  Then an "Open" annotation is created for that text element
  And the annotation contains the proposed replacement text
  And the production source file remains unchanged

Scenario: Submitting text that does not fit
  Given the Managing Editor has trial-edited a text element
  And the revised text does not fit the allotted space
  When the Managing Editor submits the proposed text change
  Then an "Open" annotation is created for that text element
  And the annotation is flagged as requiring a layout adjustment
  And the annotation contains the proposed replacement text
```

**Related requirements:** BR-01, BR-02, FR-01, FR-03

### User Story — US-04: Updating the Layout Preview

> **As a** DTP Specialist,<br>
> **I want** to update the interactive preview with the latest production layout,<br>
> **so that** the Managing Editor can review the current version while existing corrections remain traceable.

```gherkin
Feature: Layout Preview Update

Scenario: Updating the preview with a new layout version
  Given the interactive preview contains existing annotations
  When the DTP Specialist updates the preview with the latest production layout
  Then the latest layout is displayed
  And existing annotations are preserved
  And they retain their current status

Scenario: Preserving annotation associations after a layout update
  Given an annotation is linked to a text or visual element
  When the DTP Specialist updates the preview
  Then the content-linked annotation remains associated with its element
  And is displayed at the element's new location

Scenario: "Open" annotation target no longer exists
  Given an "Open" annotation's original target is no longer present in the updated layout
  When the DTP Specialist updates the preview
  Then the annotation remains "Open"
  And is flagged for manual reassignment by the Managing Editor

Scenario: "Resolved" annotation target no longer exists
  Given a "Resolved" annotation's original target is no longer present in the updated layout
  When the DTP Specialist updates the preview
  Then the annotation remains "Resolved"
  And is accessible from the correction list
  And is no longer displayed in the current layout
```

**Related requirements:** FR-05

---

## 2.4. Requirements Traceability Summary

<table>
  <tr>
    <th>Pain point</th>
    <th>Requirement</th>
    <th>User Story / Rule</th>
  </tr>

  <tr>
    <td>🔍 <strong>No live text fit-check</strong></td>
    <td>FR-01</td>
    <td>BR-01, BR-02, BR-03, US-03</td>
  </tr>

  <tr>
    <td>🖨️ <strong>Paper-based page review</strong></td>
    <td>FR-02</td>
    <td>US-02</td>
  </tr>

  <tr>
    <td rowspan="2">📄 <strong>Corrections recorded across successive proofs</strong></td>
    <td>FR-03</td>
    <td>US-01, US-02, US-03</td>
  </tr>

  <tr>
    <td>FR-05</td>
    <td>US-04</td>
  </tr>

  <tr>
    <td>❓ <strong>No consolidated view of outstanding corrections</strong></td>
    <td>FR-04</td>
    <td>US-01</td>
  </tr>
</table>

---

These requirements derive from the AS-IS workflow described in [`01_problem_and_scenario.md`](./01_problem_and_scenario.md) and are reflected in the AS-IS and proposed TO-BE process models in [`03_process_diagrams.md`](./03_process_diagrams.md).
