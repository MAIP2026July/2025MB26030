# UX and Workflow Design

## Main Workflow

ModelTrace operates as a background capability within the existing model inventory portal. Validators use the portal to inspect results; they do not need a separate application or a manual start action for each submission. This is a proposed integration, not a claim that the portal connection already exists.

1. **Report submitted:** A developer submits a new report or report version for a specific model. The portal records its model ID, report ID, version and submission time and emits a submission event.

2. **Background check triggered:** The event queues a check using the applicable approved guidance version. Repeated delivery of the same event must not create duplicate reviews. The portal shows Queued, then Processing. If guidance is unavailable or applicability is unclear, the check routes to Needs attention.

3. **Evidence mapped:** The tool maps requirements to report passages, proposes candidate evidence and flags possible omissions, conflicts or uncertain mappings. Partial processing is visible; an unfinished check is never presented as complete.

4. **Results available:** The portal displays Ready for review or Needs attention against that exact report version. An in-portal indicator alerts the assigned validator. This means the AI check has finished or needs intervention, not that validation is approved.

5. **Validator reviews:** The validator opens the evidence-review panel, checks citations and addresses High review-priority items first. The validator confirms a gap, dismisses a flag, requests clarification or keeps it unresolved, with a reason.

6. **Revisions and record:** A revised report triggers a new version-specific check. Preserve prior decisions and mark earlier results as superseded. A validator may inspect earlier evidence, but it must not be presented as current or have its decisions carried forward automatically. The portal retains the evidence note and review trail; model approval uses existing governance.

![04 UX Workflow Trust Design figure 1](assets/04_UX_Workflow_Trust_Design_figure_1.png)

## Wireframes / Screens

Illustrative model inventory portal wireframes showing the proposed experience.

**Screen 1 Model report list**

![Screen 1 Model report list illustrative portal wireframe](assets/04_UX_Workflow_Trust_Design_figure_2.png)

**Screen 2 Validation evidence review**

![Screen 2 Validation evidence review illustrative portal wireframe](assets/04_UX_Workflow_Trust_Design_figure_3.png)

Display AI-processing and human-review statuses separately. Use text labels alongside color and provide keyboard-accessible controls. A finished background check is not a validation approval.

## Trust and Explainability

- **What does the user need to know?** The tool proposes evidence mappings and potential gaps. It can miss a real issue or flag a complete report incorrectly. A missing passage is not proof that analysis was never performed. The validator decides whether evidence is sufficient and whether an official gap exists.

- **What must be visible?** Applicable requirement and guidance reference; report and guidance versions; submission and check times; processing status and incomplete sections; cited excerpts with source locators; why an item was flagged; evidence status; review priority; validator decision and reason; unresolved items and prior review history. When a revision is submitted, identify the older results as superseded. Source access must follow portal permissions, including excerpts and exports.

- **What should be hidden?** Unnecessary technical detail such as embeddings, token counts and raw prompts belongs outside the normal validator workflow. Restricted sources must not appear in results. Do not expose internal chain-of-thought or unsupported confidence percentages. Provide concise evidence-based explanations, not claims that the AI has proved a conclusion. Authorized support staff may access relevant operational diagnostics under institutional controls.

## Uncertainty Handling

- **High confidence behavior:** Where evidence maps clearly to a requirement, show Candidate evidence with citations and Standard review priority. Require validator verification before acceptance. Do not auto-close the requirement or assign model approval. Use confidence categories only after evaluation supports their meaning; avoid uncalibrated numerical scores.

- **Low confidence behavior:** If the tool cannot reliably recognize a gap or map the report to guidance, assign High validator-review priority and Unresolved - mapping or evidence uncertainty. Show the relevant requirement, attempted mapping, available sources and a concise reason. The validator checks the report before confirming or dismissing a gap. Keep review priority separate from gap severity and confidence: a higher review rating indicates a need for human attention.

- **Failure or fallback behavior:** Missing guidance, unreadable sections, inaccessible sources, conflicting versions or a processing failure must produce a visible Needs attention status. Identify the affected requirements and leave them unresolved. The validator continues using manual review and approved search. A retry may be offered after the cause is addressed, with a new run record; it must preserve prior decisions. Repeated mapping failures, material quality failures or unauthorized disclosure pause the affected AI capability and trigger escalation. Resume only after correction, testing and the relevant owner's approval.

When some requirements finish and others fail, show partial coverage explicitly and route failed items to High review priority. Check a sample of apparently supported items for silent misses; an incorrectly confident mapping may not trigger the uncertainty route.

## Human-in-the-Loop

Validators confirm the applicability of the selected guidance and checklist before relying on the results. Background processing may prepare candidate mappings in advance, but they remain provisional until this confirmation. Validators inspect evidence, confirm or override each reviewed item and record a reason. They may correct a mapping without declaring a gap, request developer clarification or escalate material ambiguity to the validation lead. Official gap severity is assigned only after human confirmation.

Developers respond through the portal's existing clarification process and submit revisions through the inventory. The validation lead adjudicates material disagreement; engineering investigates technical failures; security handles access or disclosure incidents. All handoffs retain the model, report, guidance and run identifiers. Prior records remain traceable, and unresolved issues cannot be hidden by exporting a clean summary. Final model approval remains with the institution's established validation authority.
