# Editorial–DTP Revision Workflow
### Business Analysis Mini Case Study

`Status: In Progress` `Type: Conceptual Case Study` `Domain: Publishing / EdTech` `Methods: BPMN 2.0 / User Stories / Gherkin`

A focused BA case study of a single, well-defined process slice: the revision loop between a Managing Editor and a DTP Specialist while preparing one textbook chapter for focus-testing with teachers.

Rather than modelling an entire publishing platform, this case study traces one real scenario end-to-end — from the first DTP layout to sign-off — to demonstrate requirements analysis, process modelling and solution specification in depth rather than breadth.

---

## 🗺️ Where This Fits in the Wider Process

This case study focuses only on the DTP layout and revision loop for one textbook chapter. The stages before and after this loop — such as authoring, external consultation, focus-group testing, final revisions and publication — are outside the scope of the analysis.

`Author manuscript` → `External consultation` → `Editorial content review` → **DTP layout & revision loop (this case study)** → `Teacher-focus testing` → `Revisions from teacher-focus feedback` → `Author consultation` → `External consultation` → `DTP rework` → `Final version` → `Ministry review` → `Publication`

---

## 👥 Actors

| Actor | Involved in this workflow? | Role |
|---|---|---|
| **Managing Editor** | ✅ | Reviews successive layout versions, identifies required changes, makes trial text edits, places annotations and gives sign-off |
| **DTP Specialist (Desktop Publishing Specialist)** | ✅ | Prepares and updates the typeset page layout, places visual assets and applies accepted editorial changes to the source file |
| Author | ❌ (upstream / outside this workflow) | Provides the manuscript before the DTP revision process begins |
| Subject-matter Reviewer | ❌ (upstream / outside this workflow) | Reviews the content before typesetting begins |

---

## ℹ️ Context & Disclaimer

- **Domain background:** The process, actors and pain points described here come from real professional experience managing editorial teams in educational publishing. In practice, this revision loop was handled primarily on paper — printed layouts were marked up in red pen &#128397; and physically passed back to DTP for correction.
- **Portfolio nature:** The digital tool proposed below — including its requirements, user stories and business rule — is a conceptual solution created independently for this portfolio. It was never implemented at the company in question. Its purpose is to demonstrate how a Business Analyst could specify a targeted digital improvement for this particular workflow.

---

## 🧩 Illustrative Scenario

The case study follows the revision of one textbook chapter from the first DTP layout through iterative review and correction cycles to readiness for teacher focus-testing.

**First DTP layout → Managing Editor review → corrections by DTP → repeated review cycle → focus-testing readiness**

A detailed AS-IS scenario and identified pain points are described in [`01_problem_and_scenario.md`](docs/01_problem_and_scenario.md).

---

## 🎯 Problem & Goal

Each revision cycle relied on printed proofs, red-pen annotations and manual application of corrections.

This created several recurring problems:

- the Managing Editor could not check whether revised text would fit the available space before DTP rebuilt the page,
- reviewing complete page composition required a new printed proof,
- corrections existed mainly as handwritten annotations on successive paper versions,
- determining which corrections were still outstanding required manual comparison of proofs.

**The goal is to reduce unnecessary paper-based handoffs and make the revision loop faster, clearer and easier to track.**

The proposed solution targets these problems through a interactive layout preview that allows the Managing Editor to review page composition, test text fit and track corrections without relying on physical handoffs.

---

## 📐 Scope

**In scope**

- Shared interactive layout preview for the Managing Editor and DTP Specialist
- Text-only trial editing for body text, headings and captions
- Review of photographs, illustrations and captions within the full page layout
- Digital annotations with Open / Resolved status
- Consolidated tracking of outstanding corrections with direct navigation to their location

**Out of scope**

- Other roles and stages of the wider editorial process
- Asset licensing and rights management
- Final print-ready production and DAM integration
- Automatic visual comparison between DTP versions

---

## 📋 Requirements

The proposed solution is specified through functional requirements, business rules, user stories and acceptance criteria. Full specification and traceability:
➡️ [`02_requirements.md`](docs/02_requirements.md) 

---

## 📄 Example User Stories & Acceptance Criteria

### User Story — US-01: Tracking Open Corrections

> **As a** Managing Editor,  
> **I want** to see all corrections raised for the current chapter together with their status,  
> **so that** I can quickly identify which issues have been addressed by DTP and which still require attention.

See full User Stories & Acceptance Criteria and traceability: [`02_requirements.md`](docs/02_requirements.md)

---

## 📚 Case Study Contents

| Document |	Purpose |
|---|---|
| [`01_problem_and_scenario.md`](docs/01_problem_and_scenario.md) |	AS-IS problem, scenario and pain points |
| [`02_requirements.md`](docs/02_requirements.md) | Functional requirements, business rules, user stories, acceptance criteria and traceability |
| [`03_process_diagrams.md`](03_process_diagrams.md) | AS-IS and proposed TO-BE BPMN process models |

---

## 📬 Contact

**Kamila Woronicz**
Business Analyst | Product Manager (career transition)

- Email: kamila.woronicz@gmail.com
- Location: Gdańsk, Poland
