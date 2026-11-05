# PM Artifact Pack

## Problem Statement

Independent model validators in financial institutions must cross-check developer-submitted model reports against confidential validation guidance, policies and review criteria. Manual searches, varied terminology and inconsistent report versions can make it difficult to identify missing analyses, incomplete explanations and conflicting evidence consistently. ModelTrace will test whether an internally built AI assistant can improve first-pass gap detection and reduce preparation effort while preserving independent validator judgment.

## Product Vision

Create a secure internal workspace where validators can trace each review requirement to report evidence, identify potential gaps and record reasoned decisions. Release time from evidence preparation for deeper model testing and challenge, while keeping final validation conclusions and model approval with accountable reviewers.

## PRD Summary

- **User problem:** Validators need a consistent, efficient way to assess whether developer reports address applicable validation requirements and to identify issues requiring clarification or further testing.

- **Core workflow:** Select approved guidance and report versions; confirm the applicable checklist; run the AI cross-check; inspect cited passages and potential gaps; confirm, amend or dismiss flags with reasons; obtain developer clarification or revised evidence; export the evidence note and review trail.

- **AI role:** Match validator-created guidance to report sections despite differences in wording, retrieve supporting passages and flag possible omissions or inconsistencies. Each flag must identify the relevant requirement and available evidence. Reliable gap identification is a capability to evaluate, not an established result of the existing lexical prototype.

- **Risks:** Missed genuine gaps, false flags, unsupported conclusions, stale sources, confidential information disclosure and reviewer overreliance. Build and test internally, retain versioned sources and decisions, and require human confirmation of potential gaps. Use synthetic material first; real-data use requires institution-approved access controls, retention and logging.

- **Fallback logic:** If the tool cannot reliably map a report to guidance or determine whether evidence addresses a requirement, assign High validator-review priority and an Unresolved - mapping or evidence uncertainty status. Show the requirement, attempted mapping, available citations and reason for uncertainty. The validator checks the report before confirming a gap, dismissing the flag or requesting clarification. A high review-priority rating is not a gap severity or confidence rating. Processing failures return the user to manual review and approved search; no AI gap conclusion is issued.

## Feature Prioritization

Use MoSCoW prioritization: Must features prove the central review loop, Should features improve repeatability and Could features add convenience after evidence quality is established. Effort is a relative planning estimate. Confidence reflects the feature rationale, not measured AI accuracy. Confidentiality controls and human review remain mandatory before real-data use.

| **Feature** | **User Value** | **Effort** | **Confidence** | **Priority** |
| --- | --- | --- | --- | --- |
| Source selection and validator-confirmed checklist | High | Medium | High | Must |
| Cited requirement-to-evidence mapping | High | Medium | Medium | Must |
| Potential gap flags and unresolved states | High | High | Medium | Must |
| Human decisions, reasons and evidence-note export | High | Medium | High | Must |
| Explicit date and version conflict flags | High | Medium | Medium | Should |
| Comparison of revised reports | Medium | Medium | Medium | Should |
| Draft developer clarification questions | Medium | Medium | Low | Could |
| Autonomous model approval or finding closure | Unproven | High | Low | Exclude |

## MVP Definition

Build a guided internal prototype for one deposit balance forecasting model family using synthetic developer reports and a validator-created checklist. Cover scope, data lineage, backtesting, stress scenarios, monitoring and limitations. Include source selection, checklist confirmation, cited evidence, potential gap flags, unresolved states, reviewer decisions with reasons and evidence-note export.

Use separate development and held-out reports containing complete evidence, known omissions and contradictions. Prove useful gap detection and lower total review effort than manual review with existing search, without worse quality. Disclose simulated access roles. Exclude live integrations, external hosted APIs, automatic statistical testing and autonomous approval.

## Roadmap

- **Phase 1 - Define and build:** Confirm workflow pain with validators, establish the manual-review baseline and create the checklist and synthetic evaluation packs. Build the cited mapping, potential gap flags, reviewer actions and export within an internal test environment. Product owner, validation lead and engineering own this phase.

- **Phase 2 - Evaluate and pilot:** Independently label held-out gaps, test misses and false flags, and improve uncertainty handling. Confirm institutional approval of the environment and data controls before a supervised pilot with approved material. Compare matched manual and assisted tasks, including verification and correction time. Proceed only when quality, confidentiality and efficiency gates pass.

- **Phase 3 - Roll out and improve:** Limit initial use to one model family, with named support and monitoring owners. Track detection, review time, productive utilization and unresolved issues. Route uncertain mappings to high-priority validator review; pause the affected AI capability and revert to manual review if systematic mapping failures, material misses or handling failures occur. Expand only after sustained benefit; internal funding should follow demonstrated value rather than assumed savings.

## Success Metrics

Numerical thresholds are proposed pilot targets, subject to baseline measurement; they are not achieved results.

- **Product metric:** High true-positive gap detection. Against independent reference labels, target at least 90% recall, TP / (TP + FN), where TP is a correctly flagged gap and FN is a missed gap. Count unique requirement-and-report gaps and report results by review area and materiality.

- **Business metric:** Increased efficiency and productive validator utilization. Target at least 20% lower median end-to-end review time for matched tasks, including source verification, false-flag investigation and corrections, without worse quality. Define productive utilization as hours spent on substantive review, testing and model challenge divided by available validation work hours; target an increase of at least 10 percentage points without longer working hours. Measure actual reassignment of released capacity. Time saved is not automatically cash savings.

- **Trust / guardrail metric:** Target at least 85% precision, TP / (TP + FP), where FP is an incorrect gap flag, and 95% citation support. Require no observed material misses in the agreed challenge set, no critical unsupported conclusion and no unauthorized disclosure. Report test coverage. Detected mapping failures must route to High validator-review priority; unresolved items remain visible.

## How PM Artifacts Change for AI Products

| **Standard PM Artifact** | **What Changes in an AI Product** | **Application to ModelTrace** |
| --- | --- | --- |
| Problem Statement | Define the decision or workflow being improved. | Improve the first-pass cross-check of developer reports against validator guidance. Separate evidence preparation from model approval. |
| Persona / User Story | Account for uncertainty, trust and error cost. | A validator needs cited evidence and visible uncertainty. Missing a genuine gap and investigating a false flag both create costs; the reviewer retains judgment. |
| PRD | Include data assumptions, fallback logic and risk. | Use approved, versioned guidance and matching report packs. Start with synthetic data. Failed or uncertain mapping receives High validator-review priority and an unresolved status. |
| Roadmap | Include staged learning and proof gates. | Build with synthetic reports, evaluate on held-out packs, then seek a supervised internal pilot. Advance only after detection, efficiency and handling gates pass. |
| Metrics | Connect model metrics to business outcomes. | Relate gap recall and precision to total review time and productive utilization. Include false-flag investigation, missed gaps and correction effort. |
| Launch Checklist | Include review, rollback and escalation. | Require human review, named owners and an approved environment. Escalate uncertain mapping; pause faulty AI functions and use manual review when quality or handling fails. |
| Pricing Note | Account for inference and operating cost. | Use an internal funding case that includes hosting, compute, inference, support, evaluation and reviewer effort. Confirm capacity value before claiming savings. |
| Review Memo | Separate hype from defensible product logic. | Record measured results, assumptions, known failures and residual risks. Recommend prototype, pilot, rollout or stop based on evidence rather than a polished demonstration. |

## Review Priority and Gap Confirmation

High validator-review priority means the tool needs a human decision; it does not mean a gap is more likely or more severe. Keep review priority, evidence status and confirmed-gap severity as separate fields. The validator assigns any official gap severity only after inspecting the relevant guidance and report evidence.

| **Situation** | **Tool status and priority** | **Required validator action** |
| --- | --- | --- |
| Guidance cannot be mapped reliably | Unresolved mapping; High review priority | Inspect the requirement and report, correct the mapping or request clarification before deciding whether a gap exists. |
| Evidence is absent, incomplete or contradictory | Potential gap or unresolved evidence; High review priority | Check the cited sources and applicable requirement. Confirm a gap, dismiss the flag or leave it unresolved with a reason. |
| Evidence appears to satisfy the requirement | Candidate evidence; Standard review priority | Verify the citation and coverage before recording acceptance. High-priority routing cannot detect every silent AI miss. |
| Systematic mapping failure, material miss or processing failure | Affected AI capability paused; manual review required | Escalate to the validation lead and technical owner. Complete the review with approved search and manual checks. |

In evaluation, independently label whether requirements should be unresolved as well as whether gaps exist. Track the proportion of uncertain or failed mappings correctly routed to High review priority, the volume of such referrals and the time required to resolve them. Target all detected mapping failures being routed before any gap conclusion. Review samples of apparently supported requirements to identify silent misses; a confidently incorrect mapping may not trigger the fallback.

## Launch Checklist and Rollback

- **Review:** Confirm source permissions, approved guidance versions, an applicable checklist, independent evaluation and trained validators. Every reviewed requirement needs a reasoned human decision; unresolved requirements stay visible. An incomplete review cannot be marked complete.

- **Escalation:** Uncertain mappings and unsupported gap flags go to the validator first. Material ambiguity goes to the validation lead; report clarification goes to the developer; technical failures go to engineering; handling incidents go to the security owner.

- **Rollback:** Individual uncertainty triggers manual checking of the affected requirement. Repeated mapping failures, a material quality failure or unauthorized disclosure pause the affected AI capability and return the review to manual checking and approved search. Preserve source versions, flags and prior decisions. Quarantine affected unreviewed outputs and require human reassessment before use.

- **Restart:** Engineering resolves the cause, the validation lead reviews affected outputs and regression results, and the relevant institutional owner authorizes resumption. Do not silently overwrite prior review records.

## Pricing Note and Review Memo

The initial deployment is an internally funded capability. Assess cost per completed review as the allocated hosting, compute and inference, support, maintenance, evaluation and human review costs divided by completed reviews. Internal hosting still consumes resources, and uncertainty referrals add reviewer effort. Training, integration and initial build costs should be recorded separately. No subscription price or cash saving is assumed.

The decision memo should state the permitted use, measured detection and efficiency results, productive utilization, full operating costs, failure cases and residual risks. Compare these with manual review and approved search. The present recommendation is to build and evaluate the narrow prototype; pilot or rollout requires independent evidence and institutional approval. Proposed numerical targets must remain clearly distinguished from achieved results.
