# Requirements & Specification

This document specifies the conceptual digital solution proposed for the pain points identified in [`01_problem_and_scenario.md`](./01_problem_and_scenario.md).

---

## 1. Traceability: Pain Points → Requirements

| Pain point | Addressed by |
|---|---|
| No live text fit-check | FR-01 | 
| Paper-based page review | FR-02 | 
| Corrections recorded across successive printed proofs | FR-03 | 
| No consolidated view of outstanding corrections | FR-04 | 

> **Scope note:** Automatic visual comparison between consecutive DTP versions is intentionally outside the scope of this case study. The proposed solution focuses on tracking explicitly raised corrections through digital annotations rather than automatically detecting every change between versions.

---

## 2. Functional Requirements

All four functional requirements are considered Must-have requirements for the proposed MVP.

| ID | Requirement |
|---|---|---|
| **FR-01** | The system shall allow the Managing Editor to trial-edit text, including body copy and captions, directly in the interactive layout preview and immediately show whether the revised text fits the allotted space. The edit is preview-only and does not modify the production source file. |
| **FR-02** | The system shall display the complete current page layout, including text, photographs, illustrations and captions, so that the Managing Editor can review page composition without requiring a printed proof. |
| **FR-03** | The system shall allow the Managing Editor to place a coordinate-pinned annotation on any text or visual element, describe the required correction, and track the annotation using `Open` and `Resolved` statuses. |
| **FR-04** | The system shall provide a consolidated list of annotations for the current chapter, showing their status and allowing the Managing Editor to filter the list by status and navigate directly to the corresponding location in the layout. |

---

## 3. Business Rules

### BR-01 — Trial Edit Scope
The Managing Editor may trial-edit text elements in interactive layout preview solely to evaluate text fit. Layout elements, including photographs and illustrations, cannot be repositioned or resized by the Managing Editor.

### BR-02 — Production File Ownership
Only the DTP Specialist applies accepted text, layout and visual changes to the production source file.

### BR-03 — Correction Resolution
An annotation may be marked as `Resolved` by the Managing Editor only after the requested correction has been verified in the updated layout.

---

## 4. Example User Stories & Acceptance Criteria

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

## 5. Requirements Traceability Summary

| Pain point | Requirement | User Story / Rule |
|---|---|---|
| No live text fit-check | FR-01 | BR-01, BR-02, US-03 |
| Paper-based page review | FR-02 | US-02 |
| Corrections recorded across successive printed proofs | FR-03 | US-01, US-02 |
| No consolidated view of outstanding corrections | FR-04 | US-01 |

---

These requirements derive from the AS-IS workflow described in [`01_problem_and_scenario.md`](./01_problem_and_scenario.md) and are reflected in the AS-IS and proposed TO-BE process models in [`03_process_diagrams.md`](./03_process_diagrams.md).
