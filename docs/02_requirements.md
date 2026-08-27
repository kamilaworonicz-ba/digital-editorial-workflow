# Requirements & Specification

This document specifies the conceptual digital solution proposed for the pain points and workflow limitations identified in [`01_problem_and_scenario.md`](./01_problem_and_scenario.md).

---

## 1. Traceability: Pain Points → Requirements

| Pain point / workflow limitation | Addressed by | Coverage |
|---|---|---|
| No live way to check text fit | FR-01 | Full |
| Paper-based review of complete page composition | FR-02 | Full |
| No shared view of what changed between versions | — | Deferred / Out of scope |
| No enforced completeness check at sign-off | FR-03, FR-04 | Full |

> **Scope decision:** A full visual comparison between consecutive DTP versions was intentionally left out of scope. Implementing reliable automatic change detection would significantly increase the complexity of the proposed solution. For this focused case study, the solution instead supports coordinate-pinned annotations and explicit issue statuses, allowing requested corrections to be tracked through the revision cycle.

---

## 2. Functional Requirements

| ID | Requirement | Priority |
|---|---|---|
| **FR-01** | The system shall let the Managing Editor make a trial edit to text, including body copy and captions, directly in the live layout preview and immediately show whether the edited text fits the allotted space. The edit is preview-only and does not modify the source file; the DTP Specialist applies any accepted change manually. | High |
| **FR-02** | The system shall display the current page layout, including text, photographs, illustrations and captions, so that the Managing Editor can review their placement, visual balance and interaction with surrounding content without requiring a printed proof. | High |
| **FR-03** | The system shall let the Managing Editor place a coordinate-pinned annotation on any text or visual element, describe the required correction, and track the annotation as `Open` or `Resolved`. | High |
| **FR-04** | The system shall disable the Focus-Testing Readiness Approval action while at least one annotation on the chapter has the status `Open`. | High |

---

## 3. Business Rules

### BR-01 — Text-Only Sandbox Edit Rule

- Within the live preview, the Managing Editor may edit text only for the purpose of checking whether it fits the allotted layout space.
- These edits are preview-only and do not modify the production source file.
- Layout changes, image placement, resizing and formatting remain the responsibility of the DTP Specialist and are made in the source layout file.

This rule keeps responsibility for the production file unambiguous: the live preview acts as a decision-support sandbox for the Managing Editor rather than a second production editor.

### BR-02 — Focus-Testing Approval Rule

- A chapter cannot be approved for teacher focus-testing while unresolved annotations exist.
- The system enforces this rule through FR-04 by disabling the approval action whenever at least one annotation has the status `Open`.

---

## 4. Example User Stories & Acceptance Criteria

### User Story — US-01: Focus-Testing Readiness Approval

> As a Managing Editor,
> I want the sign-off action to be blocked while unresolved annotations exist on the chapter,
> so that a chapter with unresolved issues cannot be approved for focus-testing.

```gherkin
Feature: Focus-Testing Readiness Approval

  Scenario: Blocking sign-off with open annotations
    Given the chapter has 2 annotations with the status "Open"
    When the Managing Editor attempts to approve "Focus-Testing Readiness"
    Then the approval action is disabled
    And a validation message displays:
      "Cannot approve: 2 unresolved annotations remaining."
```

**Traceability:** BR-02 → FR-04 → US-01

### User Story — US-02: Text-Only Trial Edit

> As a Managing Editor,
> I want to trial-edit a caption directly in the live layout preview,
> so that I can confirm that the revised text fits before asking the DTP Specialist to apply the change.

```gherkin
Feature: Text-Only Trial Edit

  Scenario: Checking whether a shortened caption fits
    Given a caption exceeds its allotted layout space
    When the Managing Editor edits the caption text in the live preview
    Then the system immediately shows whether the revised caption fits
    And the edit is marked as a trial edit
    And the source layout file remains unchanged

  Scenario: Attempting to edit layout or image placement
    Given the Managing Editor is using the live layout preview
    When the Managing Editor attempts to move or resize an image
    Then the action is not available
    And only text fields are editable
```

**Traceability:** BR-01 → FR-01 → US-02

---

These requirements map back to the workflow described in [`01_problem_and_scenario.md`](./01_problem_and_scenario.md) and are illustrated in the AS-IS and TO-BE process diagrams in [`03_process_diagrams.md`](./03_process_diagrams.md).
