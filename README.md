# Editorial–DTP Revision Workflow
### Business Analysis Mini Case Study

`Status: Complete` `Type: Real-World Process / Conceptual Solution` `Domain: Publishing / EdTech` <br>
`Methods: Requirements Analysis / User Stories / Gherkin / Traceability/ BPMN 2.0`

This case study focuses on a real editorial–DTP revision workflow observed in educational publishing. In the AS-IS process, successive textbook layouts were reviewed primarily on paper, with corrections marked by hand and passed back to the DTP Specialist *(responsible for page layout and typesetting)*.

The proposed digital solution is conceptual and was created independently for this portfolio. It was not implemented at the company.
Its purpose is to show how a Business Analyst could define requirements for a targeted digital improvement.

The case study covers only the revision loop between the Managing Editor and DTP Specialist, from the first page layout to sign-off for teacher focus testing *(review of the material by a group of teachers before further revisions)*.

The typical AS-IS revision loop was:

`First DTP layout` → &#128397; `Managing Editor review` → `Corrections by DTP Specialist` → `Repeated review cycle` → `Teacher focus testing readiness`

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

📈 Proposed Success Measures & Illustrative NFRs

### Success Measures

> The success measures below are based on observed characteristics of the real AS-IS process and define proposed targets for the conceptual solution.

- **Revision cycle time:** Within two months of introducing the proposed tool, the time from the first DTP layout of a chapter to focus-testing readiness should not exceed two weeks.
- **Printed proof reduction:** Within two months of introducing the proposed tool, the number of pages printed during the revision of a 20-page chapter should decrease from approximately 200 pages to no more than 40 pages *(approximately an 80% reduction)*.
- **Digital correction tracking:** Within two months of introducing the proposed tool, at least 90% of corrections exchanged between the Managing Editor and the DTP Specialist should be recorded and tracked through the shared interactive preview rather than through printed proofs.

### Illustrative NFRs

> The values below are illustrative acceptance targets and would require validation with stakeholders and the technical team.

| ID | Category | Illustrative NFR |
|---|---|---|
| NFR-01|	Performance	| The interactive layout preview shall load within 3 seconds, consistent with common UX benchmarks for perceived responsiveness. |
| NFR-02 | Performance | Annotations shall sync in near real-time (target: within 1 second) to support simultaneous review — informed by experience with a similar internal tool, where slower refresh times were a recurring source of user frustration.|
| NFR-03 | Usability | A Managing Editor or DTP Specialist shall be able to locate an open correction and navigate to its position in the layout within three user interactions from the correction list. |

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

## 8. Case Study Contents

| Document |	Purpose |
|---|---|
| [`01_problem_and_scenario.md`](docs/01_problem_and_scenario.md) |	AS-IS problem, scenario and pain points |
| [`02_requirements.md`](docs/02_requirements.md) | Functional requirements, business rules, user stories, acceptance criteria and traceability |
| [`03_process_diagrams.md`](docs/03_process_diagrams.md) | AS-IS and proposed TO-BE BPMN process models |

---

## 📬 Contact

**Kamila Woronicz**

Business Analyst | Product Manager *(career transition)*

- Email: kamila.woronicz@gmail.com
- Location: Gdańsk, Poland
