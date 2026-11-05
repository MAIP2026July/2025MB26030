# ModelTrace Project Roadmap

## Project Goal

Build an internal validation evidence assistant that automatically checks newly submitted model reports against validator-created guidance within the model inventory portal. Help validators identify genuine evidence gaps, reduce preparation effort and use more of their capacity for substantive model testing and challenge. Human reviewers retain responsibility for evidence sufficiency, gap severity and model approval.

## Current Position

A local browser-based demonstrator has been created using synthetic reports, a fixed six-area checklist, lexical retrieval and scripted checks. It demonstrates submission-triggered processing, cited passages, High validator-review priority for uncertain evidence, human decisions with reasons, version-specific history and JSON evidence-note export.

Thirteen controlled core checks pass, and the main interaction loop has been checked in a browser. These results establish limited demonstrator behavior, not independent AI accuracy, enterprise security or business value. There is no live bank inventory integration, internally hosted language-model assessment or real-data pilot yet.

## Delivery Principles

- Build and test inside the institution's approved environment. Keep confidential reports, guidance, prompts, indexes, outputs and logs within the approved boundary.
- Begin with one deposit balance forecasting model family and six review areas: scope, data lineage, backtesting, stress scenarios, monitoring and limitations.
- A new report or report version triggers a new check automatically. Keep results tied to the model, report version and guidance snapshot; preserve earlier decisions.
- Uncertain or failed mappings receive High validator-review priority and remain unresolved until a validator checks them. Review priority is separate from confirmed-gap severity.
- Advance against evidence gates rather than dates alone. Dates below are indicative planning windows, not commitments or completed milestones.

## Phased Roadmap

The timeline starts when the internal sponsor approves discovery and allocates the relevant team. Procurement, infrastructure access, document permissions and reviewer availability may change the schedule.

| Phase | Indicative timing | Main activities | Deliverables | Accountable roles | Evidence needed to proceed |
|---|---|---|---|---|---|
| 1. Validate the workflow and scope | Weeks 1-2 | Interview validators and developers; observe the current review; confirm applicable guidance, portal submission events and intended users; measure baseline effort. | Agreed problem statement, confirmed checklist, workflow map, baseline measurement plan, data-handling proposal and initial backlog. | Product owner and validation lead, supported by the portal owner. | Material review friction is demonstrated; the first use case and source ownership are agreed; an internal sponsor accepts the proposed scope. |
| 2. Build and evaluate the evidence engine | Weeks 3-4 | Create separate development and held-out synthetic packs; independently label requirements and gaps; compare lexical retrieval with an approved internally hosted semantic approach where available; test evidence-status assessment. | Versioned evidence engine, reference labels, per-requirement evaluation, failure analysis and updated PRD. | Engineering and evaluation lead; two validators label independently and a lead adjudicates. | Detection and citation quality meet the agreed technical gates on held-out material. Uncertainty is routed to human review. If quality is insufficient, remain at prototype stage. |
| 3. Integrate and harden the internal workflow | Weeks 5-6 | Connect approved portal submission events; implement background jobs, permissions, version isolation, review actions, export, retry and monitoring; test failures and duplicate events. | Integrated test environment, source-access controls, version-specific audit trail, incident path, rollback procedure and pilot plan. | Portal engineering, security and data owners, with validation operations. | Institutional approval for the handling environment; no unauthorized disclosure in the agreed tests; version and duplicate-event checks pass; manual fallback and operational ownership are demonstrated. |
| 4. Run a supervised internal pilot | Weeks 7-10 | Use approved reports from one model family; compare matched manual and assisted tasks; measure genuine-gap detection, false flags, quality, total time and productive utilization; record reviewer feedback. | Pilot evidence register, corrected task-time analysis, quality assessment, utilization results, operating-cost estimates and go/no-go memo. | Validation lead and product owner, with engineering support. | Quality and confidentiality remain acceptable; task-time savings survive verification and correction effort; referral burden is manageable. Observe utilization long enough to support any benefit claim. |
| 5. Make the rollout decision | Weeks 11-12 | Review pilot evidence and residual risks; finalize permitted use, reviewer training, support and operating budget; rehearse disabling the assistant and returning to manual review. | Sponsor decision, limited rollout plan, operating runbook, named support owners and release record. | Internal sponsor, validation governance authority, product owner and relevant control owners. | Authorize only the supported model family and workflow. Proceed, extend the pilot, narrow scope or stop based on the evidence; a successful demonstration alone is insufficient. |
| 6. Monitor and expand selectively | After limited rollout | Monitor detection, silent misses, false flags, unresolved cases, reviewer effort and costs; re-evaluate changed guidance or models; assess one additional use case at a time. | Monitoring reports, regression results, updated evaluation packs and evidence-backed backlog. | Product owner, validation lead, engineering and operational owners. | Sustained quality and practical benefit. Each new model family or document type needs separate suitability and access assessment. |

## MVP Scope and Feature Sequence

| Stage | Included capabilities | Deferred capabilities |
|---|---|---|
| Local demonstrator - available | Synthetic report submission, six-area checklist, lexical evidence mapping, scripted flags, human decisions, version history and export. | Real portal connection, production authentication, semantic evidence assessment and real-data processing. |
| Internal MVP - proposed | Approved guidance selection, report-to-guidance mapping, citations, explicit uncertainty, human decisions with reasons, controlled export and internal operational records. | Broad model-family coverage, unrestricted document ingestion and automated statistical model testing. |
| Limited rollout - conditional | Production portal trigger, authorized sources, support, monitoring, failure recovery and validated operating controls for the approved scope. | Autonomous model approval, official gap severity assignment by AI and finding closure without the required human authority remain outside scope. |

## Success Measures and Decision Gates

These thresholds are proposed targets to confirm after baseline measurement and evaluation design. They are not achieved results. Report the test size, gap materiality, supported model families, document quality and uncertainty alongside aggregate figures.

| Outcome | Proposed measure | When assessed |
|---|---|---|
| Genuine-gap detection | At least 90% AI-only gap recall: TP / (TP + FN). Count unique gaps and do not count a generic unresolved referral as a true positive. | Held-out evaluation before a pilot, then monitored in the pilot. |
| Useful flags | At least 85% gap precision: TP / (TP + FP), with duplicate flags combined. | Held-out evaluation and pilot. |
| Evidence quality | At least 95% citation support and no critical unsupported conclusion. No observed material gap miss in the agreed challenge set; zero observed failures is not proof of zero future risk. | Before pilot and throughout the supported use. |
| Uncertainty and human control | All detected mapping failures route to High review priority before a gap conclusion. Retain decisions and reasons; unresolved items stay visible. Sample apparently supported requirements for silent misses. | Before pilot and during operation. |
| Efficiency | At least 20% lower median end-to-end review time for comparable tasks, including source verification, false-flag investigation, corrections and clarification effort, without worse quality. | Supervised pilot before rollout. |
| Productive utilization | Target at least a 10-percentage-point increase in time spent on substantive review, testing and model challenge as a share of available validation work hours, without longer working hours. | Baseline versus pilot or limited rollout, using a sufficient observation period. |
| Confidentiality and reliable operation | Approved data handling; no unauthorized disclosure or cross-version leakage in the agreed tests; visible failures, named owners and a demonstrated return to manual review. | Before real-data pilot and every material release. |

TP means a correctly flagged genuine gap, FN a missed reference gap and FP an incorrect gap flag. Independent validator labels provide the reference. Define an acceptable quality margin and a sufficiently informative test sample before evaluating performance.

## Internal Funding and Value Realization

| Funding stage | Evidence requested | Value being tested |
|---|---|---|
| Discovery and synthetic prototype | Sponsor accepts the narrow problem, scope and evaluation plan. Estimate staff time and infrastructure needs. | Whether the workflow problem is material and technically testable. |
| Supervised pilot | Technical quality, access controls and fallback gates pass. Approve a capped internal pilot budget based on actual delivery estimates. | Whether better detection and lower corrected effort create usable validation capacity. |
| Limited rollout | Pilot supports the permitted use and the expected benefit justifies full operating costs. | Whether released time is reassigned to substantive validation and the benefit is sustained. |

Include build and integration effort, hosting, compute and inference, support, maintenance, ongoing evaluation, training and human verification in the value case. The current strategy is internal funding, not a commercial subscription launch. Released capacity is not automatically cash savings or revenue. No customer sale, paid pilot or funding commitment is claimed.

## Escalation and Rollback

- **Individual uncertainty:** Keep the requirement unresolved, assign High validator-review priority and have the validator inspect the guidance and report before declaring a gap.
- **Material or repeated quality failure:** Pause the affected AI capability, escalate to validation and engineering owners, and use manual review with approved search. Preserve earlier outputs and reassess affected unreviewed items.
- **Confidentiality failure:** Stop the affected capability and engage security and data owners. Do not resume until the handling issue is resolved and the relevant owner authorizes it.
- **Restart:** Correct the cause, run appropriate regression and independent quality checks, document residual risks and obtain the required internal approval. Do not overwrite prior review records.

## Immediate Next Steps

1. Confirm the internal sponsor, product owner, validation lead, portal engineering owner and data/security contacts.
2. Confirm the first model family, applicable guidance and checklist with validators.
3. Establish the manual-review baseline and independent labeling guide.
4. Challenge the local prototype with held-out synthetic reports and preserve its failure cases.
5. Agree the internal environment, operating-cost estimate and evidence gates before connecting real reports or committing to a pilot.
