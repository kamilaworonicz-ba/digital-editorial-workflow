# Editorial–DTP Revision Workflow
### Business Analysis Mini Case Study

`Status: Completed` `Type: Conceptual Case Study` `Domain: Publishing / EdTech` `Methodology: Agile / BPMN 2.0`

A focused BA case study of a single, well-defined process slice: the revision loop between an editor and a DTP specialist while preparing one book chapter for focus-testing with teachers. Rather than modeling an entire publishing platform, this case study traces one real scenario end-to-end — from the first DTP layout to sign-off — to demonstrate requirements analysis, process modeling, and solution specification in depth rather than breadth.

---

## 🗺️ Where This Fits in the Wider Process
 
The full editorial pipeline for a course book is much broader than what's analyzed here:
 
`Author manuscript → External consultation → Editorial content review → `**`DTP layout & revision loop (this case study)`**`→ Teacher focus-group testing → Revisions from focus-group feedback → Author consultation → External consultation → DTP rework → Final version → Ministry review → Publication`
 
This case study zooms into a single highlighted stage — the DTP revision loop for one chapter — and analyzes it in full depth. Everything upstream and downstream is out of scope.


---

## ℹ️ Context & Disclaimer

- **Domain background:** The process, actors, and pain points described here come from real professional experience managing editorial teams in educational/scientific publishing. In practice, this revision loop was handled entirely on paper — printed layouts marked up in red pen and carried between desks.
- **Portfolio nature:** The digital tool proposed below (requirements, user stories, business rules) is a conceptual solution created independently for this portfolio. It was never implemented at the company in question. Its purpose is to demonstrate how a BA would specify a targeted digital fix for this specific bottleneck — not to document an existing system.

---

## 🧩 The Scenario

**Chapter 8 of a course book, DTP version #1 → 3 revision rounds → sign-off.**

| Step | What happens | Actors |
|---|---|---|
| **Input** | Author's manuscript (finalized after external subject-matter consultations, with preliminary editing already done by the Managing Editor) is sent to DTP for first typesetting. | Author → Managing Editor |
| **Round 1 — Text fit** | Managing Editor reviews the typeset layout for text overflow/underflow caused by the page grid; flags lines and paragraphs that no longer fit. | Managing Editor, DTP Specialist |
| **Round 2 — Visual assets** | Stock photographs (Shutterstock, delivered with a visible watermark at this stage — licensing is out of scope here) and illustrations created in-house are placed into the layout; captions are written and fitted. | Managing Editor, DTP Specialist |
| **Round 3 — Final polish** | Remaining small corrections across text and visuals are closed out. | Managing Editor, DTP Specialist |
| **Sign-off** | Managing Editor approves the chapter as ready — *not* for final print, but for use in **focus-testing sessions with teachers**, where it needs to look and feel like a finished textbook. | Managing Editor |

**Out of scope:** the Author and the subject-matter Reviewer do not participate in this loop — their input is already finalized before Round 1 begins.

---

## 🎯 Problem & Goal

Every round above relied on printed proofs, red-pen annotations, and manual re-typing of corrections — with no shared view of what changed between versions, and no way to check whether a text edit would even fit before DTP rebuilt the page. The proposed tool targets exactly that: a shared, live view of the layout that lets the editor check and flag issues directly, without a physical handoff.

---

## 📐 Scope

**In scope (this case study):**
- A live layout preview shared between Managing Editor and DTP Specialist for one chapter
- Text-only trial editing for the editor, to check fit before DTP applies changes
- Placement of stock photos/illustrations with captions
- Pinpoint annotations on text or visual elements
- An approval gate blocking sign-off while issues remain open

**Out of scope:**
- Other roles/stages of the wider editorial process (ingestion, peer review, publication)
- Asset licensing/rights management for stock photography
- Final print-ready production and DAM integration

---

## 📋 Functional Requirements

| ID | Requirement | Round |
|---|---|---|
| **FR-01** | The system shall let the Managing Editor make a trial edit to text (body copy or captions) directly in the live layout preview and immediately show whether the edited text fits the allotted space. This edit is preview-only — it does not modify the source file; the DTP Specialist applies any accepted change manually. | 1, 2 |
| **FR-02** | The system shall let the DTP Specialist place stock photographs (delivered as watermarked drafts) and in-house illustrations into the layout, each with an associated caption field. | 2 |
| **FR-03** | The system shall let the Managing Editor drop a coordinate-pinned annotation on any text or visual element, with a note describing the required correction. | 1–3 |
| **FR-04** | The system shall block the "Focus-Testing Readiness Approval" action while any annotation on the chapter remains unresolved. | 3 |

---

## 🔒 Business Rule

> **Text-Only Sandbox Edit Rule** — Within the live preview, only the Managing Editor's text edits are permitted, and only as a fit check. Layout, image placement, and formatting changes remain the sole responsibility of the DTP Specialist, made in the source file.

---

## 👥 Roles

| Role | Responsibility in this workflow |
|---|---|
| **Managing Editor** | Reviews layout each round, makes trial text edits, places annotations, gives final sign-off |
| **DTP Specialist** | Builds and updates the typeset layout, places visual assets, applies accepted text edits to the source file |

---

## 📄 Requirements Engineering Sample

**User Story — US-01**
> As a Managing Editor,
> I want the sign-off action to be blocked while unresolved annotations exist on the chapter,
> So that a version with open issues can never be mistakenly approved for focus-testing.

```gherkin
Feature: Focus-Testing Readiness Approval

Scenario: Blocking sign-off with open annotations
  Given the chapter has 2 unresolved annotations
  When the Managing Editor attempts to approve "Focus-Testing Readiness"
  Then the action is disabled
  And a validation message displays: "Cannot approve: 2 unresolved annotations remaining."
```

---

## 📁 Repository Structure

```
editorial-dtp-revision-ba/
├── docs/
│   ├── 01_problem_and_scenario.md   # Full narrative: Round 1 → 2 → 3 → sign-off
│   ├── 02_requirements.md           # FR table, business rule, user story & Gherkin
│   └── 03_process_diagram.md        # BPMN diagram for this revision loop
├── diagrams/
│   └── bpmn_revision_loop.png
└── README.md                         # This file
```

---

## 📬 Contact

**Kamila Woroniecz, PhD**
*Business Analyst / Product Manager (career transition)*

- Email: kamila.woronicz@gmail.com
- Location: Gdańsk, Poland
