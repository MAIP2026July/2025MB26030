# Data, Model, and Evaluation Strategy

## Problem as AI Task

ModelTrace combines retrieval and ranking with evidence-status classification. It runs in the background when a new model report or version is submitted to the model inventory portal. For each applicable validator-created requirement, it retrieves relevant passages and proposes one of four states: Candidate evidence, Potential gap, Unresolved mapping or evidence uncertainty, or Explicit inconsistency. These are assistance states, not final validation judgments.

Language-based matching connects differently worded requirements and report passages. Evidence assessment then considers whether the cited passages address the requirement. Retrieval alone cannot establish that a requirement is satisfied. A potential gap may reflect incomplete documentation rather than an underlying model defect; the validator makes that distinction. Generating clarification questions is a later option, conditional on reliable evidence mapping.

## Data Sources

- **Internal:** Approved model development reports and appendices; model inventory metadata; validator-created guidance, policies, checklists and review criteria; historical validation reports, clarification logs and issue records where authorized. Record model ID, document ID, report version, guidance version, effective dates, access scope and source locators. The initial use case is one deposit balance forecasting model family. The MVP checks report evidence rather than ingesting raw customer-level modeling datasets.

- **External:** No external data is required for the initial use case. The tool relies on institution-approved internal sources, with no public-web retrieval or external hosted model API. Any later external source requires a separate decision on relevance, handling and approval.

- **User-generated:** Validator-confirmed checklists, corrected evidence mappings, decisions, reasons and developer clarification responses entered within the portal. These remain internal confidential records. They are candidates for adjudication, not automatic training truth; reviewer acceptance alone does not prove correctness.

For the assignment, use synthetic versions of these internal document types. A real-data pilot requires institutional permission and an approved internal environment. Check parsing quality, tables, page references, missing sections, scanned documents and inconsistent versions before evaluating model behavior. Preserve access restrictions in passages, indexes, outputs and exports. Treat source content as evidence, not instructions to the AI.

## Labeling / Ground Truth

Use the model-report-version and applicable requirement as the evaluation unit. Create a written labeling guide defining what evidence is needed for each requirement and what counts as a documentation gap, insufficient evidence, explicit conflict or unclear applicability. Distinguish a documented limitation from a missing required analysis.

Two qualified validators should independently label each held-out requirement and identify supporting report passages. A validation lead adjudicates disagreements. Record the requirement ID, applicability, reference evidence, gap type, materiality and rationale. Preserve unresolved label disputes for separate reporting rather than forcing false certainty. Assess agreement before adjudication to identify ambiguous guidance.

Use historical findings only as starting points: past reports may omit issues, reflect different guidance or contain superseded judgments. Independently inspect both flagged and apparently complete requirements to identify genuine negatives and missed gaps. Combine duplicate flags before scoring; distinguish genuinely uncertain cases from definite gaps and definite non-gaps.

Keep model families and related document versions together when splitting development and evaluation data. For a single-family prototype, keep related report packs together and report the limited generalization. Keep the held-out labels outside the runtime retriever. The applicable guidance is legitimate runtime input; future reports, future clarifications and finalized findings must not leak into a run on an earlier report version. Do not use later evidence unless it was available at that review snapshot.

## Baseline

Compare ModelTrace with the existing manual validation workflow: a validator uses the same approved checklist, report pack and keyword search to identify evidence and potential gaps. Give both conditions the same source access and review scope. A secondary technical baseline can rank passages using keyword matching or TF-IDF without semantic matching or AI gap assessment.

Measure total task time, including evidence search, source verification, investigation of false flags, correction and clarification effort. Use distinct but matched report tasks and balance reviewer experience and report complexity. Randomize condition and order where practical. Compare final evidence quality as well as time: faster completion with more material misses is not success.

## Model / API Choice

Build the application and workflow internally. Use deterministic controls for submission triggers, report-guidance version matching, source eligibility, permissions, review status and decision logging. Start with a frozen lexical baseline; compare it with an institution-approved, internally hosted embedding model and reranker for semantic retrieval.

If the institution has an approved internally hosted language model, evaluate it for evidence-status assessment using the applicable requirement and retrieved passages. Require structured outputs containing requirement ID, proposed status, citations and a concise evidence-based rationale. Use explicit uncertainty routes rather than forcing a gap or no-gap decision. If adequate evidence cannot be retrieved, leave the requirement unresolved for High validator-review priority; absence of retrieved text does not prove a gap.

No external hosted model API is proposed. Model size and deployment configuration depend on internal infrastructure, licensing, quality and support capacity; no specific model is assumed to be approved. Internal model-service calls may be used within the approved boundary. Do not train a foundation model from scratch for the MVP. Consider fine-tuning only after enough adjudicated examples exist and evaluation demonstrates a need.

Record parser, retrieval, model, prompt and policy versions for each run, together with the model ID, report version and guidance snapshot. A new report submission triggers a new check; duplicate event delivery must not create duplicate reviews. Results remain tied to their own report versions. Validate each component and the full workflow separately, since a correct citation can still support an incorrect conclusion.

## Evaluation Framework

All numerical targets below are proposed decision gates, not observed results. Report counts, denominators and uncertainty, alongside results by review area, materiality, document quality and supported model family. Account for clustering within report packs when assessing uncertainty.

| **Metric Type** | **Metric** | **Why It Matters** |
| --- | --- | --- |
| Technical | Retrieval recall at a fixed k: reference passages retrieved / reference passages labeled relevant; fix k before the held-out test | Tests whether the assessment stage receives the evidence it needs. Retrieval success alone does not prove correct gap detection. |
| Technical | Gap recall = TP / (TP + FN); gap precision = TP / (TP + FP), with duplicate flags combined | Measures genuine gaps caught and unnecessary investigations. Unresolved real gaps are not counted as correctly detected gaps until the validator confirms them; report AI-only and assisted-workflow results separately. |
| Technical | Evidence-status agreement and unresolved-case rate | Tests the proposed routing states and reveals whether apparent safety is achieved by referring almost everything to humans. Report confusion between gap, supported, conflict and uncertainty states. |
| Business | Median end-to-end task-time reduction versus matched manual reviews, with final quality checked independently | Measures whether the tool saves effort after source checking, false flags and corrections. |
| Business | Productive validator utilization: substantive review, testing and model-challenge hours / available validation work hours | Tests whether released capacity is actually used for higher-value validation work. Use consistent time categories, exclude leave and agreed non-validation commitments, and track working hours. |
| Trust / Guardrail | Citation support and critical unsupported conclusions | Tests whether statements are supported by cited text and whether any output could materially mislead the reviewer. |
| Trust / Guardrail | Uncertain-mapping referral coverage, silent material misses and High-priority referral volume | Checks whether mapping failures reach validators before a gap conclusion, while exposing missed failures and excessive manual-review burden. |
| Trust / Guardrail | Source-permission and version-isolation failures; decision-and-reason completeness | Tests confidentiality, current-version handling and human accountability, including excerpts, exports and background processing. |

TP is a unique genuine gap correctly flagged against the adjudicated reference; FN is a reference gap missed; FP is an incorrect gap flag. For AI-only recall, a generic unresolved referral is not a TP. Evaluate whether assisted human review ultimately detects the gap, and include its effort. For definite reference gaps, unresolved AI results remain undetected in AI-only recall; label-ambiguous cases are reported separately. Test with complete reports, genuine omissions, paraphrases, contradictions, unreadable sections, wrong versions and adversarial source instructions.

## Launch Thresholds

Proceed first to a supervised internal pilot, not unrestricted deployment, only when the following proposed gates pass on held-out material and institutional owners accept the permitted scope:

- **Genuine-gap detection:** At least 90% AI-only gap recall and 85% gap precision, with TP, FP and FN counts and separate materiality results. No observed material gap miss in the agreed challenge set. These thresholds require an adequate independently labeled test set; zero observed misses is not proof of zero future risk.

- **Evidence and uncertainty:** At least 95% of assessed output statements supported by their citations, with no critical unsupported conclusion. All detected mapping failures route to High validator-review priority and an unresolved status before any gap declaration. Evaluate silent misses independently; do not infer referral reliability only from failures the system already recognizes.

- **Human control:** Every reviewed requirement retains a validator decision and reason. Unresolved items remain visible and prevent the review being presented as complete. High review priority does not assign gap severity or establish that a gap exists.

- **Efficiency and utilization:** At least 20% lower median total review time on comparable tasks without worse independently assessed quality. Target at least a 10-percentage-point rise in productive utilization without increased working hours; confirm over a sufficient observation period before expansion. Define an acceptable quality margin and sample size before the pilot rather than treating a nonsignificant difference as proof of equal quality.

- **Handling and operations:** Institution-approved data handling and source access; no unauthorized disclosure or cross-version leakage in the agreed tests; validated duplicate-event handling; visible processing failures; and named validation, engineering, support and security owners. Keep the check's completion status distinct from validation approval.

If a requirement cannot be mapped reliably, route it to High-priority validator checking and leave it unresolved until reviewed. Repeated mapping failures, material quality failures or handling incidents pause the affected AI capability and return the workflow to manual review with approved search. Preserve prior outputs and decisions, investigate the cause and require regression evidence and owner approval before resuming.
