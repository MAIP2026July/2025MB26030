No	Full name	Student ID	GitHub ID
1	Priya M	2025MB26030	Priya-bits237


# ModelTrace local inventory portal demonstrator

A runnable, synthetic human-in-the-loop capstone prototype. Open `dist/index.html` in a modern desktop browser after extracting the complete ZIP. No installation, account, API key or external service is required. Keep `core.js`, `app.js` and `style.css` beside `index.html`.

## Team details

| Full name | Student ID | GitHub ID |
|---|---|---|
| Priya M | 2025MB26030 | Priya-bits237 |

Actual individual contribution disclosure must be completed by the student. ChatGPT generated this local implementation, synthetic fixtures, tests, screenshots and supporting draft; do not describe AI generation as independently completed human work.

## What works

- Select a synthetic scenario or paste synthetic text, then submit a new report version.
- Submission queues local processing automatically: Queued -> Processing -> Ready for review, or Needs attention on a parser failure.
- Inspect six requirements, source paragraphs and high-priority candidate issues.
- Confirm checklist applicability, choose a decision and record a reason. Accepting evidence also requires a selected report passage.
- Request clarification or keep unresolved; these actions do not mark the review complete.
- Submit a revised report. Older results and decisions stay attached to their own report versions and are marked superseded.
- Export a JSON evidence note, including unresolved states and the review trail. This is not a model approval.

## Processing method and limits

`core.js` performs local bag-of-words TF-IDF-like ranking and scripted evidence-pattern checks. This is a lexical prototype of the proposed AI experience, not an implemented language-model assessor. The checks are deliberately narrow and can be fooled by irrelevant, negated or differently formatted text. A candidate evidence state does not prove requirement satisfaction. Retrieved backtesting evidence can include an irrelevant monitoring passage because of overlapping error terminology. The reviewer can inspect the whole report and correct the mapping.

The scenario named ambiguous backtesting explicitly states that the period and numerical error are not provided; the rule therefore produces a Potential gap with High review priority. To demonstrate an unresolved mapping instead, remove that sentence or replace it with vague text without an explicit omission statement. Neither state is a confirmed gap.

The fixed G1 checklist and passage locators P1, P2, etc. are synthetic. There is no PDF/OCR parser, bank inventory connection, server job queue, guidance selection engine, real authentication or production audit store. An interruption while the page is closed is recovered as Needs attention. Role permissions, enterprise encryption, tamper resistance, multi-user use and true background execution while the browser is closed are not established.

All data is processed in this browser. Local browser storage may retain synthetic reports and decisions, and the JSON export contains report passages. Do not enter confidential documents. Reset demo clears this demonstrator's stored synthetic records after a confirmation. Browser storage behavior for local files can differ; records may not persist across browsers or file moves.

## Demonstration scenarios

Complete evidence; omitted stress analysis; backtesting evidence needing clarification; contradictory monitoring frequencies; unreadable report; a narrow known instruction-attempt pattern. The last case does not demonstrate general injection resistance.

## Run checks

With Node.js installed, run from this directory:

```bash
node tests/core.test.cjs
```

Thirteen checks pass on the included synthetic fixtures. These are controlled regression checks rather than independent accuracy estimates. Browser interactions were also checked for report submission, checklist gating, clarification saving, parsing fallback, version isolation and export. See `evidence/test_results.txt` and `evidence/sample_evidence_note.json`.

## Files

- `dist/`: application and screening logic.
- `tests/`: controlled checks.
- `screenshots/`: actual browser captures of the working local demonstrator.
- `evidence/`: test output and one synthetic exported evidence note.
- `DEMO_GUIDE.md`: suggested walkthrough.
- `AI_Self_Evaluation.md`: limitations and next decision.

No hosted demo or GitHub repository has been created. The ZIP is the delivered source package. The localhost preview used for QA is temporary and is not a live demo URL.
