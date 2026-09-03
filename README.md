# Editorial–DTP Revision Workflow
### Business Analysis Mini Case Study

`Status: Complete` `Type: Conceptual Case Study` `Domain: Publishing / EdTech` `Methods: BPMN 2.0 / User Stories / Gherkin`

The case study described here is one step within a much broader process: preparing a school textbook. Authors create the source materials, which go through external consultation before the publishing house develops them editorially and visually — the latter handled by a DTP Specialist, who formats and typesets each page. The materials are then tested with a teacher focus group, followed by a further round of revisions and consultation. The print version undergoes a ministry review before publication; the multimedia version is published directly.

`Author manuscript` → `External consultation` → `Editorial content review` → &#128397; **layout & revision loop (this case study)** → 
`Teacher-focus testing` → `Revisions from teacher-focus feedback` → `Author consultation` → `External consultation` → `DTP rework` → `Final version` → `Ministry review` → `Publication`

This case study focuses on one well-defined slice of that process: the revision loop between a Managing Editor and a DTP Specialist while preparing a textbook chapter for teacher focus-testing. It traces one real scenario end-to-end — from the first page layout to sign-off — rather than modelling the entire publishing process; all other stages are outside its scope.

---

## 1. Actors

| Actor | Involved in this workflow? | Role |
|---|---|---|
| **Managing Editor** | ✅ | Reviews successive layout versions, identifies required changes, makes trial text edits, places annotations and gives sign-off |
| **DTP Specialist (Desktop Publishing Specialist)** | ✅ | Prepares and updates the typeset page layout, places visual assets and applies accepted editorial changes to the source file |
| Author | ❌ outside this workflow | Provides the manuscript before the DTP revision process begins |
| Subject-matter Reviewer | ❌ outside this workflow | Reviews the content before typesetting begins |

---

## 2. Context & Disclaimer

- **Domain background:** The process, actors and pain points described here come from real professional experience managing editorial teams in educational publishing. In practice, this revision loop was handled primarily on paper — printed layouts were marked up in red pen &#128397; and physically passed back to DTP for correction.
- **Portfolio nature:** The digital tool proposed below — including its requirements, user stories and business rules — is a conceptual solution created independently for this portfolio. It was never implemented at the company in question. Its purpose is to demonstrate how a Business Analyst could specify a targeted digital improvement for this particular workflow.

---

## 3. Illustrative Scenario

The case study follows the revision of one textbook chapter from the first DTP layout through iterative review and correction cycles to readiness for teacher focus-testing.

`First DTP layout` → `Managing Editor review` → `Corrections by DTP` → `Repeated review cycle` → `Teacher-focus testing readiness`

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

The proposed solution targets these problems through an interactive layout preview that allows the Managing Editor to review page composition, test text fit and track corrections without relying on physical handoffs.

---

## 5. Success Measures & Illustrative NFRs

### Success Measures

- **Revision cycle time:** Within two months of introducing the proposed tool, the time from the first DTP layout of a chapter to focus-testing readiness should not exceed two weeks.
- **Printed proof reduction:** Within two months of introducing the proposed tool, the number of pages printed during the revision of a 20-page chapter should decrease from approximately 200 pages to no more than 40 pages *(approximately an 80% reduction)*.
- **Digital correction tracking:** Within two months of introducing the proposed tool, at least 90% of corrections exchanged between the Managing Editor and the DTP Specialist should be recorded and tracked through the shared interactive preview rather than through printed proofs.

### Illustrative NFRs

> The values below are illustrative acceptance targets and would require validation with stakeholders and the technical team.

| ID | Category | Illustrative NFR |
|---|---|---|
| NFR-01|	Performance	| The interactive layout preview should load within 3 seconds, consistent with common UX benchmarks for perceived responsiveness. |
| NFR-02 | Performance | Annotations should sync in near real-time (target: within 1 second) to support simultaneous review — informed by experience with a similar internal tool, where slower refresh times were a recurring source of user frustration.|
| NFR-03 | Usability | A Managing Editor or DTP Specialist should be able to locate an open correction and navigate to its position in the layout within three user interactions from the correction list. |

---

## 6. Scope

**In scope**

- Shared interactive layout preview for the Managing Editor and DTP Specialist
- Text-only trial editing for body text, headings and captions
- Review of photographs, illustrations and captions within the full page layout
- Digital annotations with `Open` / `Resolved` status
- Consolidated tracking of outstanding corrections with direct navigation to their location

**Out of scope**

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
| [`03_process_diagrams.md`](docs/03_process_diagrams.md) | AS-IS and proposed TO-BE BPMN process models |

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
