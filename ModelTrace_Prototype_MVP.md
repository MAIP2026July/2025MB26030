## Prototype / MVP

### Prototype Type

A local browser-based human-in-the-loop demonstrator of the model inventory portal. It runs from the supplied source package by opening `dist/index.html`, with no installation or external model API. It is a functional workflow prototype using synthetic reports and a fixed G1 validation checklist; the production portal integration is simulated.

### What It Demonstrates

A developer submits a new report version for model DEP-001. The submission automatically queues a local background check, followed by Ready for review or Needs attention. The validator inspects six requirements: scope, data lineage, backtesting, stress scenarios, monitoring and limitations.

Each requirement shows the guidance, candidate report passages, proposed evidence state and review priority. Uncertain or conflicting mappings receive High review priority before the validator decides whether a gap exists. Checklist confirmation, a human decision and a reason are required; accepting evidence also requires a selected source passage. Clarification requests and unresolved items keep the review incomplete.

A revised report creates a fresh check. Prior results and decisions remain with their original version and are marked superseded. An unreadable-report scenario routes to manual review without issuing a gap conclusion. The validator can export a JSON evidence note containing identifiers, source passages, decisions and the review trail. Model approval remains outside the tool.

### AI Role

The intended AI contribution is matching validator-created guidance to differently worded report evidence and identifying potential gaps for human review. The current demonstrator implements a local lexical ranking baseline and scripted evidence checks, with no language-model call. It therefore demonstrates where AI would support the workflow, while making the limits of the implemented screening method explicit.

The included cases cover complete evidence, an explicit omission, backtesting needing clarification, monitoring conflict, parsing failure and a narrow known instruction attempt. High review priority signals the need for human checking; it does not assign confirmed-gap severity or claim calibrated confidence.

### What It Does Not Yet Prove

The prototype does not establish reliable semantic gap detection, independent model accuracy, reduced review time, higher utilization or business savings. The same assistant authored the synthetic cases and tests. Thirteen controlled core checks pass and browser QA verifies the main interaction loop; these do not establish real-world quality or security.

There is no connection to a financial institution's inventory portal, authentic identity or role-based permissions, production audit store, PDF/OCR parsing, server-side background processing or internally hosted language model. Local processing stops if the browser closes; interrupted work returns to Needs attention on reopening. Browser storage and exported files are for synthetic content only.

Before a real-data pilot, independently evaluate held-out report packs, compare with manual review, assess uncertain-referral burden and obtain approval for the internal handling environment. Sample apparently supported requirements for silent misses. Retain manual review and approved search as the fallback.

### Links

- **Repository:** No GitHub repository has been created. Full source is supplied in `ModelTrace_Local_MVP.zip`.
- **Live Demo:** Local runnable demo: extract the ZIP and open `ModelTrace_Local_MVP/dist/index.html` in a modern desktop browser. No hosted URL is claimed.
- **Screenshots / Video:** Actual browser screenshots are in `screenshots/portal_review.jpg` and `screenshots/portal_fallback.jpg` inside the ZIP; the Word section includes the review screenshot. No video has been recorded.

