# Product Strategy

## Product Vision

Enable model validators to identify potential evidence gaps efficiently through a secure internal tool that checks developer-submitted reports against validator-created guidance. Provide traceable references and consistent review support while preserving independent human judgment.

## JTBD

When I am reviewing a model development report, I want to cross-check it against our validation guidance and identify potential gaps with supporting references, so that I can focus on material issues and raise clear, evidence-based questions to the developer.

## Opportunity Framing

- **Why this problem matters:** Validators repeatedly interpret requirements, search report sections and assess whether evidence is sufficient. Missing analyses, incomplete explanations or inconsistent versions can increase review effort and obscure important gaps. Better first-pass coverage could free time for deeper model challenge; the benefit must be measured.

- **Why current alternatives are weak:** Manual checklists depend on reviewers locating and interpreting evidence consistently. Keyword search can locate terms but may miss relevant passages expressed differently, and a matching phrase does not establish that a requirement is satisfied. Generic external AI tools do not meet the proposed internal-only handling approach for confidential reports and governance material.

- **Why AI may help:** AI can match validator-created guidance to relevant report sections despite differences in terminology, organize candidate evidence and flag possible omissions or inconsistencies. Each flag should include the relevant requirement and available source references. Validators confirm whether the issue is a documentation gap or requires further model testing. The opportunity is worth testing now through a narrow synthetic prototype; reliable gap detection and time savings remain unproven.

## Opportunity Matrix

| **Idea** | **Business Value** | **Feasibility** | **Priority** |
| --- | --- | --- | --- |
| Map guidance to cited report sections | High: reduce repeated evidence searches | High for a narrow text-based prototype | High - MVP |
| Flag potential evidence gaps | High: improve first-pass review coverage | Medium: requires independent labels and careful testing | High - MVP with human review |
| Flag explicit version or date conflicts | High: expose inconsistent evidence | Medium for clearly stated metadata and claims | Medium - after core mapping |
| Draft developer clarification questions | Medium: make confirmed gaps easier to communicate | Medium once evidence quality is established | Medium - later |
| Approve models or close findings autonomously | Unproven: high cost of incorrect decisions | Low for accountable independent judgment | Exclude |

## Build vs Buy vs Partner/API

- **Recommended path:** Build and test ModelTrace internally within the financial institution's approved environment. Reuse approved libraries and internally hosted language or embedding models where available. Keep confidential reports, validation guidance, governance questions, indexes, prompts, outputs and logs within that boundary. Exclude external hosted model APIs from the initial MVP.

- **Why:** The institution needs control over confidential modeling information and internal policies, along with access permissions, document versions, review records and changes to the tool. An internal build also allows the workflow and evaluation to reflect its own validation requirements. A purchased product or external partner would require separate assessment of deployment, data handling, integration and supplier terms; neither is selected for the MVP.

- **Main trade-offs:** Internal development requires engineering capacity, infrastructure, security reviews, model maintenance and ongoing evaluation, and may take longer than buying an application. The institution gains control and customization but assumes the operating burden. Building internally does not require training a foundation model from scratch, and internal hosting still requires access controls, retention rules and testing.

## First Wedge

Start with a first-pass evidence review for one deposit balance forecasting model. Use one synthetic developer report pack and a validator-created checklist covering scope, data lineage, backtesting, stress scenarios, monitoring and limitations.

For each requirement, show relevant report excerpts and citations, flag potential gaps and let the validator confirm, amend or dismiss the flag with a reason. Confirmed gaps become clarification requests to the developer. Model approval and final validation conclusions remain outside the tool's authority.

Test against manual review supported by the existing search process, using held-out reports with known gaps and independently reviewed labels. Measure gap detection, false flags, citation support and total review time. Consider a supervised internal pilot only after useful performance is demonstrated and the handling environment is approved.
