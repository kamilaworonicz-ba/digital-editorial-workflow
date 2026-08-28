# Requirements & Specification

This document specifies the conceptual digital solution proposed for the pain points identified in [`01_problem_and_scenario.md`](./01_problem_and_scenario.md).

---

## 1. Functional Requirements

> The functional requirements below were derived from the pain points identified in the AS-IS workflow.
All four functional requirements are considered Must-have requirements for the proposed MVP.

| ID | AS-IS Pain Piont | Functional requirement |
|---|---|---|
| **FR-01** | **🔍 No live text fit-check.** Even a small text correction requires DTP to update the layout before the Managing Editor can verify whether it works. | The system shall allow the Managing Editor to trial-edit text, including body text, headings and captions, directly in the interactive layout preview and immediately show whether the revised text fits the allotted space. |
| **FR-02** | **🖨️ Paper-based page review.** Reviewing text and visual composition requires repeated printing and physical handoffs between the Managing Editor and DTP Specialist. | The system shall display the complete current page layout, including text, photographs, illustrations and captions, in a shared interactive preview accessible to both the Managing Editor and the DTP Specialist. |
| **FR-03** | **📄 Corrections recorded across successive proofs.** Required changes are distributed across separate marked-up proofs rather than managed as one coherent set of corrections. | The system shall allow the Managing Editor to place a coordinate-pinned annotation on any text or visual element and describe the required correction. Each annotation shall have an `Open` or `Resolved` status and shall be visible to the DTP Specialist in the interactive layout preview. |
| **FR-04** | **❓ No consolidated view of outstanding corrections.** Determining which corrections have been addressed and which still require attention requires manual comparison of successive proofs. | The system shall provide both the Managing Editor and the DTP Specialist with a consolidated list of annotations for the current chapter, showing their status, allowing filtering by status and providing direct navigation to the corresponding location in the layout. |

---

## 2. Business Rules

### BR-01 — Trial Edit Scope
The Managing Editor may trial-edit text elements in interactive layout preview solely to evaluate text fit. Layout elements, including photographs and illustrations, cannot be repositioned or resized by the Managing Editor.

### BR-02 — Production File Ownership
Only the DTP Specialist applies accepted text, layout and visual changes to the production source file.

### BR-03 — Correction Resolution
An annotation may be marked as `Resolved` by the Managing Editor only after the requested correction has been verified in the updated layout.

---

## 3. Example User Stories & Acceptance Criteria

### User Story — US-01: Tracking Open Corrections

> **As a** Managing Editor, 
> **I want** to see all corrections raised for the current chapter together with their status,  
> **so that** I can quickly identify which issues have been addressed by DTP and which still require attention.

```gherkin
Feature: Correction Tracking

  Scenario: Reviewing outstanding corrections
    Given the chapter contains open and resolved annotations
    When the Managing Editor opens the correction list
    Then each annotation is displayed with its current status
    And the Managing Editor can filter the list to show only open annotations
    And selecting an annotation takes the Managing Editor to its location in the layout
```

**Related requirements:** FR-03, FR-04 

---

### User Story — US-02: Visual Layout Review

> **As a** Managing Editor,  
> **I want** to indicate the exact location of a required correction directly on the page layout,  
> **so that** the DTP Specialist can clearly identify what needs to be changed without relying on a marked-up printed proof.

```gherkin
Feature: Visual Layout Review

  Scenario: Adding an annotation to a visual element
    Given the Managing Editor is reviewing the current chapter layout
    When the Managing Editor places an annotation on a photograph
    And enters a description of the required correction
    Then the annotation is attached to that specific location
    And its status is set to "Open"
    And the DTP Specialist can see the annotation in the shared preview
```

**Related requirements:** FR-03

---

### User Story — US-03: Text Fit Check

> **As a** Managing Editor,  
> **I want** to trial-edit text directly in the interactive layout preview,  
> **so that** I can check whether a proposed wording change fits before asking the DTP Specialist to apply it to the production file.

```gherkin
Feature: Text Fit Check

  Scenario: Checking whether revised text fits
    Given a text element exceeds its allotted layout space
    When the Managing Editor edits the text in the interactive layout preview
    Then the system immediately shows whether the revised text fits
    And the edit remains preview-only
    And the production source file remains unchanged

  Scenario: Attempting to modify the layout
    Given the Managing Editor is using the interactive layout preview
    When the Managing Editor attempts to move or resize an image
    Then the action is not available
```

**Related requirements:** BR-01, BR-02, FR-01

---

## 4. Requirements Traceability Summary

| Pain point | Requirement | User Story / Rule |
|---|---|---|
| No live text fit-check | FR-01 | BR-01, BR-02, US-03 |
| Paper-based page review | FR-02 | US-02 |
| Corrections recorded across successive printed proofs | FR-03 | US-01, US-02 |
| No consolidated view of outstanding corrections | FR-04 | US-01 |

---

These requirements derive from the AS-IS workflow described in [`01_problem_and_scenario.md`](./01_problem_and_scenario.md) and are reflected in the AS-IS and proposed TO-BE process models in [`03_process_diagrams.md`](./03_process_diagrams.md).
