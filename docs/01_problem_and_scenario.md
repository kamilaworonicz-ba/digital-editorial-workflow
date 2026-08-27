# Problem & Scenario: Editorial–DTP Revision Workflow

## 1. Problem Statement (AS-IS)

Once a manuscript was typeset for the first time, it entered an iterative revision loop between the Managing Editor and the DTP Specialist. In the process this case study is based on, the workflow was primarily paper-based.

Each revision cycle followed a similar pattern: DTP produced a printed proof, the Managing Editor marked corrections by hand in red pen &#x1F58D;, and the marked-up pages were returned to DTP for another layout revision.

This created three recurring problems:

- **No live way to check text fit.** The Managing Editor could not verify whether shortened or rewritten text would actually fit the available space until DTP rebuilt the page and produced another proof.
- **No shared view of what changed.** Each proof was a static snapshot, making it difficult to identify changes between consecutive DTP versions without reviewing the pages again.
- **No enforced completeness check.** Final approval relied on manually checking marked-up proofs. There was no mechanism preventing sign-off while a previously identified correction remained unresolved.

The scenario below illustrates these problems using one textbook chapter, from its first DTP layout to approval for teacher focus-testing.

---

## 2. Actors

| Actor | Involved in this workflow? | Role |
|---|---|---|
| **Managing Editor** | ✅ | Reviews the layout, identifies required corrections and gives final sign-off |
| **DTP Specialist** | ✅ | Builds and updates the typeset layout based on editorial feedback |
| Author | ❌ (upstream / outside this workflow) | Provides the manuscript before the DTP revision process begins |
| Subject-matter Reviewer | ❌ (upstream / outside this workflow) | Reviews the content before typesetting begins |

---

## 3. Illustrative Scenario: Chapter 8

*Note: The sequence below illustrates a typical revision path rather than a fixed three-round process. In practice, text, caption and visual issues could overlap and reappear across multiple iterations.*

### Process Input

DTP receives the Chapter 8 manuscript: a Word file containing the finalized text, already through external subject-matter consultation and a preliminary editorial pass by the Managing Editor.

The input also includes a page plan indicating where photographs and illustrations are expected to appear.

DTP prepares the first typeset version using the textbook's standard page grid.

### Initial Layout Review

The Managing Editor reviews the first DTP version page by page.

At this stage, issues often become visible that could not be reliably predicted from the source manuscript. For example:

- a paragraph may no longer fit the space allocated to it once it is set in the actual typeface and column width,
- a heading or highlighted text element may require shortening,
- planned captions may need adjustment to fit their designated space.

The Managing Editor marks required corrections directly on the printed proof.

The proof is then returned to the DTP Specialist, who applies the requested changes in the source layout file and prepares the next version.

The Managing Editor must review the updated pages again to verify whether the corrections have been applied successfully.

### Visual Assets & Caption Review

Photographs and illustrations are also reviewed as part of the chapter layout.

The visual material may include:

- stock photographs used in watermarked draft form at this stage,
- illustrations created in-house,
- captions written or adjusted during editorial work.

The Managing Editor needs to see how these elements function within the actual page layout, not in isolation.

For example:

- a photograph may not work well with other visual elements on the same page,
- image colours may conflict with the surrounding page design,
- an illustration may require different positioning,
- a caption may be too long for the available space,
- adding or repositioning an image may affect the surrounding text flow.

These issues are again marked on the proof and returned to DTP for correction.

### Subsequent Revision Cycles

Further DTP versions are reviewed until the remaining text, caption and visual issues are resolved.

Corrections may involve:

- issues already identified in an earlier version,
- adjustments created as a side effect of previous changes,
- newly noticed problems with text or visual composition.

The exact number of revision cycles varies depending on the chapter.

Because each version is reviewed as a separate printed proof, the Managing Editor must manually verify that requested corrections were applied and that no new problems were introduced.

### Sign-off — Focus-Testing Readiness Approval

Once the Managing Editor confirms that the identified issues have been resolved, the chapter is approved as ready for teacher focus-testing.

**This is not the final publication sign-off.**

At this stage:

- stock photographs may still contain watermarks,
- teacher focus-testing has not yet taken place,
- further editorial revisions may still follow,
- the material will undergo additional stages before final publication.

The sign-off only confirms that the chapter is sufficiently complete and visually polished to be presented to teachers in a form resembling a finished textbook.

---

## 4. Pain Points Summary

| Pain point | Where it appears | Business impact |
|---|---|---|
| No live fit-check for text | Throughout revision cycles, particularly for body text and captions | A text correction cannot be validated until DTP updates the layout, creating unnecessary back-and-forth |
| No visual comparison between versions | Between consecutive DTP versions | The Managing Editor must manually review updated pages to identify changes and possible side effects |
| No enforced completeness check | At sign-off | Approval depends on manually reconciling corrections across multiple printed proofs, creating a risk that an unresolved issue is missed |

These pain points map directly to the functional requirements defined in [`02_requirements.md`](./02_requirements.md).
