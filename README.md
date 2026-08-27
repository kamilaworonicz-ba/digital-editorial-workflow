# Editorial–DTP Revision Workflow
### Business Analysis Mini Case Study

`Status: Completed` `Type: Conceptual Case Study` `Domain: Publishing / EdTech` `Methods: BPMN 2.0 / User Stories / Gherkin`

A focused BA case study of a single, well-defined process slice: the revision loop between a Managing Editor and a DTP Specialist while preparing one textbook chapter for focus-testing with teachers.

Rather than modelling an entire publishing platform, this case study traces one real scenario end-to-end — from the first DTP layout to sign-off — to demonstrate requirements analysis, process modelling and solution specification in depth rather than breadth.

---

## 🗺️ Where This Fits in the Wider Process

This case study focuses only on the DTP layout and revision loop for one textbook chapter. The stages before and after this loop — such as authoring, external consultation, focus-group testing, final revisions and publication — are outside the scope of the analysis.

`Authoring & review` → `DTP layout & revision loop` → `Focus testing` → `Final revisions` → `Publication`


---

## ℹ️ Context & Disclaimer

- **Domain background:** The process, actors and pain points described here come from real professional experience managing editorial teams in educational publishing. In practice, this revision loop was handled primarily on paper — printed layouts were marked up in red pen and physically passed back to DTP for correction.
- **Portfolio nature:** The digital tool proposed below — including its requirements, user stories and business rule — is a conceptual solution created independently for this portfolio. It was never implemented at the company in question. Its purpose is to demonstrate how a Business Analyst could specify a targeted digital improvement for this particular workflow.

---

## 🧩 The Scenario

Illustrative scenario: Chapter 8 → first DTP layout → iterative review and corrections → sign-off.

The sequence below illustrates a typical revision path rather than a fixed number of rounds. In practice, text, caption and visual issues could overlap and reappear across multiple iterations.

| Step | What happens | Actors |
|---|---|---|
| Input | Author's manuscript, finalized after external subject-matter consultations and preliminary editing by the Managing Editor, is sent to DTP for first typesetting. | Managing Editor, DTP Specialist |
| Initial layout review | The Managing Editor reviews the first typeset version, including text fit and overall page composition, and identifies required corrections. | Managing Editor, DTP Specialist |
| Visual assets & captions review | Photographs, illustrations and captions are reviewed within the actual page layout. Text and visual issues may overlap with those identified earlier. | Managing Editor, DTP Specialist |
| Further revision cycles | DTP applies corrections and prepares updated versions. The Managing Editor reviews successive versions until the remaining text, caption and visual issues are resolved. | Managing Editor, DTP Specialist |
| Sign-off | The Managing Editor confirms that the chapter is ready for focus-testing with teachers. This is not the final publication sign-off. | Managing Editor |

**Out of scope:** the Author and the subject-matter Reviewer do not participate in this workflow — their input is already finalized before this process begins.

---

## 🎯 Problem & Goal

Each revision cycle relied on printed proofs, red-pen annotations and manual application of corrections.

This created several recurring problems:

- the Managing Editor could not check whether revised text would fit the available space before DTP rebuilt the page,
- reviewing complete page composition required a new printed proof,
- corrections existed mainly as handwritten annotations on successive paper versions,
- determining which corrections were still outstanding required manual comparison of proofs.

The proposed solution targets these problems through a shared digital layout preview that allows the Managing Editor to review page composition, test text fit and track corrections without relying on physical handoffs.

---

## 📐 Scope

**In scope**

- Live layout preview shared between the Managing Editor and DTP Specialist
- Text-only trial editing for checking text and caption fit
- Digital preview of photographs, illustrations and captions within the complete page layout
- Coordinate-pinned annotations on text and visual elements
- Open / Resolved status for annotations
- Consolidated view of outstanding corrections
- Navigation from a correction directly to its location in the layout

**Out of scope**

- Other roles and stages of the wider editorial process
- Asset licensing and rights management for stock photography
- Final print-ready production
- DAM integration
- Automatic visual comparison between consecutive DTP versions

---

## 📋 Functional Requirements

| ID | Requirement |
|---|---|
| FR-01 | The system shall allow the Managing Editor to trial-edit text directly in the live layout preview and immediately see whether the revised text fits the allotted space. The edit is preview-only and does not modify the source file. |
| FR-02 | The system shall display the complete current page layout, including text, photographs, illustrations and captions, so that the Managing Editor can review page composition without requiring a printed proof. |
| FR-03 | The system shall allow the Managing Editor to place a coordinate-pinned annotation on any text or visual element, describe the required correction, and assign the annotation a status of Open or Resolved. |
| FR-04 | The system shall provide a consolidated list of annotations for the current chapter, showing their status and allowing the Managing Editor to filter the list by status and navigate directly to the corresponding location in the layout. |

Full requirement detail, priorities and traceability: [`02_requirements.md`](docs/02_requirements.md)

---

## 🔒 Business Rule

**BR-01 – Text-Only Sandbox Edit Rule**

Within the live preview, the Managing Editor may edit text only for the purpose of checking whether it fits the assigned layout space.

These edits are preview-only and do not modify the production source file.

Layout changes, image placement, resizing and formatting remain the responsibility of the DTP Specialist and are made in the source layout file.

---

## 👥 Roles

| Role | Responsibility in this workflow |
|---|---|
| Managing Editor | Reviews successive layout versions, makes trial text edits, identifies required changes, places annotations and gives final sign-off |
| DTP Specialist | Builds and updates the typeset layout, places visual assets and applies accepted changes to the source file |

---

## 📄 Example User Stories & Acceptance Criteria

### User Story — US-01: Tracking Open Corrections

**As a** Managing Editor,
**I want** to see all corrections raised for the current chapter together with their status,
**so that** I can quickly identify which issues have been addressed by DTP and which still require attention.

```gherkin
Feature: Correction Tracking

  Scenario: Reviewing outstanding corrections
    Given the chapter contains open and resolved annotations
    When the Managing Editor opens the correction list
    Then each annotation is displayed with its current status
    And the Managing Editor can filter the list to show only open annotations
    And selecting an annotation takes the Managing Editor to its location in the layout
```

Traceability: FR-03 → FR-04 → US-01

### User Story — US-02: Visual Layout Review

**As a** Managing Editor,
**I want** to place a pinpoint annotation directly on a photograph, illustration or other page element,
**so that** I can clearly indicate what needs to be changed without marking and returning a printed proof.

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

Traceability: FR-02 → FR-03 → US-02

---

## 📁 Repository Structure

```
editorial-dtp-revision-ba/
├── docs/
│   ├── 01_problem_and_scenario.md   # AS-IS problem, actors and iterative revision scenario
│   ├── 02_requirements.md           # Functional requirements, business rule, user stories & Gherkin
│   └── 03_process_diagrams.md       # AS-IS and TO-BE process analysis
├── diagrams/
│   ├── bpmn_as_is.png
│   └── bpmn_to_be.png
└── README.md
```

---

## 📬 Contact

**Kamila Woronicz, PhD**
Business Analyst / Product Manager (career transition)

- Email: kamila.woronicz@gmail.com
- Location: Gdańsk, Poland
