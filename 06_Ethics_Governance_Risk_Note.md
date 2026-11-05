# Ethics, Governance, and Risk Note

## Main Risks

- **Risk 1 - Bias and uneven review quality:** The tool may perform better on familiar model families, standard report formats and well-documented requirements than on unusual models, scanned tables or ambiguous guidance. Historical findings and reviewer feedback may encode inconsistent judgments. Treating these records as unquestioned truth could reproduce those differences and miss material issues in less familiar reports.

- **Risk 2 - Privacy and confidentiality:** Developer reports, internal guidance, governance questions and review records may contain confidential modeling information or personal data. Unauthorized retrieval, excessive permissions, exports, caches or logs could expose information across models or teams. Internal hosting alone does not establish confidentiality, and access to the inventory portal does not imply access to every model document.

- **Risk 3 - Hallucination, unsafe conclusions and misuse:** The AI may invent a gap, cite a passage that does not support its conclusion, miss a genuine omission or present an uncertain mapping as complete. Reviewers may over-rely on a confident output. Source instructions may attempt to manipulate the check, and users may misuse flags as automatic findings, employee rankings or grounds for model approval without independent assessment.

## Harm Scenarios

| **Who could be harmed** | **Scenario and consequence** |
| --- | --- |
| Validators and validation leads | A convincing but unsupported evidence mapping hides a material gap. The reviewer reduces independent checking, and the final validation conclusion becomes less reliable. |
| Model developers and model owners | An uncertain mapping is labeled as a confirmed gap or assigned unwarranted severity. Unnecessary remediation, unfair escalation and delays follow. |
| The financial institution and potentially its customers | A missed material issue contributes to an inadequately challenged model being used. Any downstream effect depends on the model and its use; ModelTrace must not claim that its review prevents losses or establishes model soundness. |
| Document owners, employees or customers whose information appears in reports | A cross-model permission failure or unrestricted export reveals confidential information or personal data. |
| Teams using uncommon models or nonstandard documentation | Lower detection quality produces uneven scrutiny, repeated false flags or excessive manual referrals. Report style is mistaken for model quality. |
| Reviewers and developers | Management treats AI acceptance rates, flag counts or utilization measures as individual performance scores, creating pressure to accept outputs or avoid raising issues. |

## Controls

- **Guardrails:** Build and operate within the institution-approved environment using approved internal sources and internally hosted models where available. Apply source-level permissions during ingestion, retrieval, background processing, display and export. Minimize unnecessary personal data; keep sensitive content out of general operational logs. Control encryption, retention, deletion and cache scope under institutional policy. Version reports, guidance and run configurations; keep old results attached to their own report versions. Treat source text as untrusted evidence and test instruction-injection attempts. Use structured outputs with requirement IDs and source locators, and check citation support. Do not issue autonomous model approval, finding closure or official gap severity. Compare quality by model family, requirement type, document format and parsing quality; restrict supported use where performance is insufficient.

- **Review process:** Every reviewed requirement needs a validator decision and reason. If the tool cannot recognize a gap reliably or map the report to guidance, assign High validator-review priority and Unresolved - mapping or evidence uncertainty. The validator checks the guidance and report before confirming a gap, dismissing the flag, correcting the mapping or requesting clarification. Review priority is separate from gap severity and confidence. Unresolved requirements remain visible and prevent a review being presented as complete. Inspect samples of apparently supported requirements for silent misses; the uncertainty route cannot catch every confidently incorrect result. Two qualified validators independently label held-out evidence, with a validation lead adjudicating disagreements. User feedback is reviewed before it becomes evaluation or training material.

- **Escalation path:** The assigned validator handles individual uncertain mappings. The validation lead adjudicates material ambiguity or disagreement; developers provide clarification through the portal's existing process. Engineering investigates parsing, retrieval, model and submission-trigger failures. Security and data owners handle access or disclosure incidents. Repeated mapping failures, material quality failures or unauthorized disclosure pause the affected AI capability and return users to manual review and approved search. Preserve prior records and reassess affected unreviewed outputs. Resume only after correction, regression evidence and authorization by the relevant institutional owner.

- **Logging / auditability:** Record model ID, report and guidance versions, submission time, run ID, parser and model configuration versions, proposed status, review priority, source references, reviewer decision, reason and escalation history. Record processing failures, permission checks and exports. Store the evidence trail under controlled access and retention, with mechanisms to detect unauthorized alteration. Log only what is needed for traceability; avoid unrestricted raw document or prompt capture. A new report triggers a new check without overwriting earlier decisions. Prevent duplicate submission events from creating duplicate reviews. Distinguish AI-check completion from human-review completion and model approval.

The product owner is responsible for permitted use and scope; the validation lead owns evidence quality and human adjudication; engineering owns reliable operation; security and data owners approve handling controls. The institution's existing governance authority retains model approval. These are proposed responsibilities to assign before a pilot, not claims of regulatory compliance or institutional endorsement.

## Launch Blockers

Pause or reject a pilot or rollout if any of the following applies:

- **Confidentiality or handling failure:** Real documents are used without the institution's approval; source permissions cannot be enforced; an unauthorized disclosure occurs; or retention, export and incident ownership are unresolved. Investigate and verify remediation before any resumption.

- **Material quality failure:** A material reference gap is missed in the agreed challenge set, a critical unsupported conclusion appears, or the proposed evidence-quality gates are not met. Proposed gates include at least 90% AI-only gap recall, 85% precision and 95% citation support on adequately sized held-out material. Report test coverage and uncertainty; passing a small test does not establish safety.

- **Unsafe uncertainty handling:** Detected mapping failures are presented as resolved or confirmed gaps without validator review; High review-priority items have no clear owner; unresolved items disappear from the export; or the interface confuses a completed background check with validation approval. A high-priority referral alone does not count as a true-positive gap detection.

- **Unacceptable uneven performance:** Performance for an intended model family, report format or requirement type is too weak for the agreed scope, or material differences remain unexplained. Narrow the supported scope or improve the system before including those cases. Do not hide weak segments behind an aggregate score.

- **Missing human or operational control:** The tool permits approval or finding closure without the required authority; decisions lack reasons or traceability; report versions are mixed; duplicate triggers corrupt the review; or rollback and escalation cannot be demonstrated. Do not launch without named operational owners.

- **No defensible user benefit or evidence of misuse:** Correction and false-flag investigation erase the efficiency benefit, review quality deteriorates, or utilization gains rely on longer working hours. Stop misuse of individual scores or AI flags as automatic judgments about staff or models. Refine or reject the product if benefits do not justify ongoing risk and cost.

An isolated uncertain requirement normally triggers manual checking of that requirement. A systemic or material failure triggers capability-level rollback. Final approval to proceed must document the supported use, residual risks, evaluation evidence and accountable owners; neither a high retrieval score nor a polished portal demonstration authorizes launch.
