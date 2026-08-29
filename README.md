# Editorial–DTP Revision Workflow
### Business Analysis Mini Case Study

`Status: In Progress` `Type: Conceptual Case Study` `Domain: Publishing / EdTech` `Methods: BPMN 2.0 / User Stories / Gherkin`

A focused BA case study of a single, well-defined process slice: the revision loop between a Managing Editor and a DTP Specialist while preparing one textbook chapter for focus-testing with teachers.

Rather than modelling an entire publishing platform, this case study traces one real scenario end-to-end — from the first DTP layout to sign-off — to demonstrate requirements analysis, process modelling and solution specification in depth rather than breadth.

---

## 1. Where This Fits in the Wider Process

This case study focuses only on the DTP layout and revision loop for one textbook chapter. The stages before and after this loop — such as authoring, external consultation, focus-group testing, final revisions and publication — are outside the scope of the analysis.

`Author manuscript` → `External consultation` → `Editorial content review` → **DTP layout & revision loop (this case study)** → `Teacher-focus testing` → `Revisions from teacher-focus feedback` → `Author consultation` → `External consultation` → `DTP rework` → `Final version` → `Ministry review` → `Publication`

---

## 2. Actors

| Actor | Involved in this workflow? | Role |
|---|---|---|
| **Managing Editor** | ✅ | Reviews successive layout versions, identifies required changes, makes trial text edits, places annotations and gives sign-off |
| **DTP Specialist (Desktop Publishing Specialist)** | ✅ | Prepares and updates the typeset page layout, places visual assets and applies accepted editorial changes to the source file |
| Author | ❌ (upstream / outside this workflow) | Provides the manuscript before the DTP revision process begins |
| Subject-matter Reviewer | ❌ (upstream / outside this workflow) | Reviews the content before typesetting begins |

---

## 3. Context & Disclaimer

- **Domain background:** The process, actors and pain points described here come from real professional experience managing editorial teams in educational publishing. In practice, this revision loop was handled primarily on paper — printed layouts were marked up in red pen &#128397; and physically passed back to DTP for correction.
- **Portfolio nature:** The digital tool proposed below — including its requirements, user stories and business rule — is a conceptual solution created independently for this portfolio. It was never implemented at the company in question. Its purpose is to demonstrate how a Business Analyst could specify a targeted digital improvement for this particular workflow.

---

## 4. Illustrative Scenario

The case study follows the revision of one textbook chapter from the first DTP layout through iterative review and correction cycles to readiness for teacher focus-testing.

**First DTP layout → Managing Editor review → corrections by DTP → repeated review cycle → focus-testing readiness**

A detailed AS-IS scenario and identified pain points are described in [`01_problem_and_scenario.md`](docs/01_problem_and_scenario.md).

---

## 4. Problem & Goal

Each revision cycle relied on printed proofs, red-pen annotations and manual application of corrections.

This created several recurring problems:

- the Managing Editor could not check whether revised text would fit the available space before DTP rebuilt the page,
- reviewing complete page composition required a new printed proof,
- corrections existed mainly as handwritten annotations on successive paper versions,
- determining which corrections were still outstanding required manual comparison of proofs.

**The goal is to reduce unnecessary paper-based handoffs and make the revision loop faster, clearer and easier to track.**

The proposed solution targets these problems through a interactive layout preview that allows the Managing Editor to review page composition, test text fit and track corrections without relying on physical handoffs.

---

## 5. Success Measures & Illustrative NFRs

### Success Measures

- **Revision cycle time:** Within two months of introducing the proposed tool, the time from the first DTP layout of a chapter to focus-testing readiness should not exceed two weeks.
- **Printed proof reduction:** Within two months of introducing the proposed tool, the number of pages printed during the revision of a 20-page chapter should decrease from approximately 200 pages to no more than 40 pages *(approximately an 80% reduction)*.
- **Digital correction tracking:** Within two months of introducing the proposed tool, at least 90% of corrections exchanged between the Managing Editor and the DTP Specialist should be recorded and tracked through the shared interactive preview rather than through printed proofs.

### Illustrative NFRs

>The NFRs below are hypothetical examples created for this portfolio case study. They are not derived from measured production-system constraints and are included to demonstrate how non-functional requirements could be defined for the proposed solution.

| ID | Category | Illustrative NFR |
|---|---|---|
| NFR-01|	Performance	| The interactive layout preview should load within 3 seconds under normal operating conditions. |
| NFR-02 | Performance | Creating or updating an annotation should be reflected in the shared preview within 2 seconds. |
| NFR-03 | Usability | A Managing Editor or DTP Specialist should be able to locate an open correction and navigate to its position in the layout within three user interactions from the correction list. |

---

## 6. Scope

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

## 7. Requirements

The proposed solution is specified through functional requirements, business rules, user stories and acceptance criteria. Full specification and traceability:
➡️ [`02_requirements.md`](docs/02_requirements.md) 

---

## 8. Case Study Contents

| Document |	Purpose |
|---|---|
| [`01_problem_and_scenario.md`](docs/01_problem_and_scenario.md) |	AS-IS problem, scenario and pain points |
| [`02_requirements.md`](docs/02_requirements.md) | Functional requirements, business rules, user stories, acceptance criteria and traceability |
| [`03_process_diagrams.md`](03_process_diagrams.md) | AS-IS and proposed TO-BE BPMN process models |

---
## 💡 Skills Demonstrated

`Requirements analysis and functional requirements definition`
`Business rules identification`
`User Stories and Acceptance Criteria in Gherkin`
`Requirements traceability`
`AS-IS / TO-BE process analysis and BPMN modelling`
`Pain-point identification and process improvement`
`Scope definition and MVP thinking`

---

## 📬 Contact

**Kamila Woronicz**
Business Analyst | Product Manager *(career transition)*

- Email: kamila.woronicz@gmail.com
- Location: Gdańsk, Poland
