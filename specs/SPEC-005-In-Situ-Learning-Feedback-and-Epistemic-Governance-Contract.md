# SPEC-005 — In-Situ Learning, Feedback, and Epistemic Governance Contract

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Release target:** v1.0.0 — Research Framework and Contracts  
**Status:** Proposed normative research contract; no implementation or empirical conformance certified  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**License:** Apache-2.0  
**Primary dependencies:** SPEC-001, SPEC-002, SPEC-003, SPEC-004; OCSRE-007, OCSRE-009  
**Forward dependency:** SPEC-006 (WE-native CDE and composite-state promotion)  
**Primary hypothesis:** OCSH-004; supporting OCSH-001, OCSH-003, OCSH-005, OCSH-006, OCSH-007, OCSH-008, OCSH-009, OCSH-010, OCSH-011

## Abstract

This specification proposes an auditable contract for **in-situ object learning, feedback attribution, epistemic revision, and evidence governance** in Object-Centric Structural Reasoning and Evolution (OCSRE). *In-situ* denotes accountability to a World Entity (WE), composite object, perspective, and versioned context—not a requirement that computation physically run inside an object. A learning loop may attach observations, derive measurements, form inferences, recommend decisions, observe outcomes, and revise models or policies. These steps MUST NOT be conflated. In particular, statistical association is not causal attribution; a metric score is not a deductive proof; model promotion is not an authorized real-world action; and a candidate CDE delta is not a committed state transition. The contract defines evidence and feedback envelopes, update classes, promotion gates, dependency-aware invalidation, multi-perspective and multi-agent controls, conformance profiles, adversarial tests, and measurable hypotheses. It follows **Specifications/Contracts First, Conformance Before Runtime, Explicit Leftover**. All requirements are proposed; no system is asserted to have passed them.

**Keywords:** World Entity; in-situ learning; feedback attribution; epistemic separation; evidence provenance; object differential kernel; model revision; governance; WE-native CDE; collective learning; conformance.

## 1. Purpose, scope, and non-goals

OCSRE-007 describes an object-anchored intelligence loop; OCSRE-009 establishes the need to distinguish observations, derived measurements, deductions, probabilistic inferences, hypotheses, evaluations, recommendations, authorizations, and validated outcomes. This document translates those research proposals into an interoperable contract. Its consumers include WE adapters, Object Differential Kernel (ODK) services, learning plugins, decision services, provenance registries, CDE proposal generators, SIF controllers, and UIERU/MLIU relay coordinators.

The specification governs **observable interfaces and safety-relevant transitions**, not a particular training algorithm, causal estimator, probabilistic formalism, agent architecture, or persistence engine. Learning MAY use online updates, batch estimation, symbolic revision, rules, simulation, or human review. A conforming implementation MUST demonstrate that its observable behavior respects the declared semantics and authority boundaries.

Non-goals include proving general intelligence, defining consciousness, replacing WE-SIO identity semantics, certifying model correctness in every domain, guaranteeing causal discovery from observational data, or asserting a structural scaling law.

## 2. Normative language and precedence

**MUST / MUST NOT** are mandatory for a future implementation claiming conformance to this *proposed* specification; **SHOULD / SHOULD NOT** require documented exceptions; **MAY** denotes an option. These words do not imply independent standards certification.

- **SPEC-001** owns identity, state/version, perspective, temporal scope, ownership, and permissions.
- **SPEC-002** owns `Object[metricIndices]`, ODK evaluation, comparator and metric alignment semantics.
- **SPEC-003** owns classical validity preservation and cross-granularity inference contracts.
- **SPEC-004** owns plugin manifests, capability composition, invocation effects, and dependency governance.
- **SPEC-005** owns learning feedback, epistemic states, revision, and promotion of *knowledge/model artifacts*.
- **SPEC-006** owns WE-native CDE candidate transitions, composite constraints, and operational state promotion.

Where obligations overlap, an implementation MUST satisfy all applicable requirements; a less restrictive downstream policy MUST NOT silently override an upstream semantic or permission restriction.

## 3. Foundational distinctions and prohibited collapses

A conforming system MUST preserve at least these distinctions:

1. **WE identity ≠ object state ≠ learning-model identity.** A model update need not change the entity or its real-world state.
2. **Source record ≠ observation ≠ verified fact.** Records may be erroneous, incomplete, stale, or adversarial.
3. **Observation ≠ derived metric.** Transformations introduce assumptions and versioned semantics.
4. **Metric similarity / differential ≠ deductive entailment.** ODK scores require their own interpretation.
5. **Statistical association ≠ causal effect.** Attribution requires a declared identification strategy or an explicit noncausal label.
6. **Inference ≠ hypothesis ≠ policy preference.** Epistemic and normative statuses are different.
7. **Decision recommendation ≠ authorization ≠ execution ≠ observed outcome.** Each transition needs its own record.
8. **Learning update ≠ CDE typed delta ≠ committed state transition.** SPEC-006 governs the last two steps.
9. **High confidence ≠ evidence independence.** Correlated sources must not be double-counted as independent support.
10. **Successful local feedback ≠ transferable capability.** Receiving-domain validation is mandatory for promoted relay claims.
11. **Missing feedback ≠ negative feedback.** Absence, censoring, and observation delay require explicit representation.
12. **A newer artifact ≠ a better artifact.** Promotion depends on validation, not chronology.

## 4. Minimal object learning context

The following language-neutral reference record is illustrative; machine-readable schema finalization is an Explicit Leftover.

```text
ObjectLearningContext {
  contextId: StableIdentifier
  objectScope: Set<WERef> | CompositeStateRef
  identityVersion: VersionRef
  stateSnapshotRef: VersionedStateRef
  perspectiveRef: PerspectiveRef
  temporalWindow: Interval
  metricContracts: Set<VersionedMetricRef>
  comparatorContracts: Set<VersionedComparatorRef>
  reasoningRuleRefs: Set<VersionedRuleRef>
  learningPolicyRef: VersionedPolicyRef
  objectiveAndConstraints: VersionedObjectiveRef
  evidencePolicyRef: VersionedEvidencePolicyRef
  permissions: PermissionContextRef
  provenanceRoot: ProvenanceGraphRef
  unresolvedResiduals: Set<ResidualRef>
}
```

Every learning event MUST bind to an identifiable context or explicitly declare why the scope is unresolved. A composite scope MUST specify membership semantics and the version at which membership was evaluated. A perspective-specific policy MUST NOT silently become an objective fact about the object.

## 5. Epistemic class system

A conforming implementation MUST represent epistemic class as a first-class field, rather than inferring it from a free-text description. At minimum:

| Class | Meaning | Example | Prohibited promotion |
|---|---|---|---|
| `source_record` | Received artifact, not yet interpreted | SQL row, log entry | Directly to verified fact |
| `observation` | Scoped report of an event or state | GPS arrival reading | Directly to causal claim |
| `derived_measurement` | Computed under typed transformation | Normalized delay | Directly to deductive proof |
| `deductive_conclusion` | Derived by declared valid rules | Syllogistic conclusion | Outside the rule's formal scope |
| `statistical_inference` | Model-based estimate | Probability of late arrival | Directly to certainty |
| `hypothesis` | Candidate explanation or mechanism | Congestion causes delays | Directly to accepted fact |
| `evaluation` | Perspective-bound scoring | Route quality score | Directly to authorization |
| `recommendation` | Proposed decision | Change departure time | Directly to execution |
| `authorization` | Scoped permission decision | Approve sandbox trial | Beyond authorized scope |
| `execution_record` | Evidence of attempted/performed action | Route deployed | Directly to verified outcome |
| `validated_outcome` | Outcome assessed against criteria | Verified reduction in delay | Automatically to universal claim |

Epistemic labels MUST be versioned and traceable. Contradictory claims MAY coexist with conflict status; forced resolution without evidence is prohibited.

## 6. Evidence envelope and provenance graph

```yaml
evidence_id: EV-EXAMPLE-001
class: observation
object_scope: [WE-REF]
identity_version: identity-v1
state_version: state-v7
perspective_ref: perspective-v2
event_time: 2026-01-01T08:00:00Z
recorded_time: 2026-01-01T08:01:00Z
source_ref: source-with-integrity-record
transformation_chain: []
rule_or_model_version: null
uncertainty: {kind: declared, value: not-assessed}
independence_group: sensor-family-A
permission_context_ref: permissions-v3
status: unreviewed
residuals: [calibration-unverified]
```

This example is not a finalized schema or a real observation. Evidence MUST carry stable identifiers, source/provenance references, object and time scope, epistemic class, relevant model/rule versions, uncertainty qualification, and access constraints. Transformations MUST create derivation edges, not erase the original source. A derivation graph MUST distinguish **depends-on**, **corroborates**, **contradicts**, **derived-by**, **supersedes**, and **invalidates** relations when those semantics are supported. Cycles in evidence dependencies MUST be detected and MUST NOT be counted as independent corroboration.

A revoked or corrected source MUST trigger dependency-aware re-evaluation of affected inferences, feedback records, models, decisions, and relay artifacts. The system MAY preserve historical decisions for audit but MUST flag their now-invalid support.

## 7. Feedback envelope and attribution

```text
FeedbackEnvelope {
  feedbackId: StableIdentifier
  learningContextRef: ObjectLearningContextRef
  observationWindow: Interval
  predictionRef?: EvidenceRef
  recommendationRef?: DecisionRef
  authorizationRef?: AuthorizationRef
  executionRef?: ExecutionRef
  outcomeEvidenceRefs: Set<EvidenceRef>
  baselineOrComparatorRef?: VersionedComparatorRef
  attributionStatus: observed | associated | causal_supported | unknown
  attributionMethodRef?: VersionedMethodRef
  uncertaintyAndMissingness: QualificationRef
  confounderAndSelectionNotes: Set<ResidualRef>
  provenanceRef: ProvenanceGraphRef
  permissionContextRef: PermissionContextRef
  feedbackStatus: pending | qualified | disputed | invalidated | accepted
}
```

The attribution field MUST distinguish an observed outcome from a causal claim about an earlier action. `causal_supported` MUST identify a design or justified identification method, its assumptions, and sensitivity limits; it does not mean causality is proven without qualification. Missing, delayed, censored, or selectively observed outcomes MUST be represented explicitly. Outcome measurement windows MUST be compatible with the intervention and baseline windows or the mismatch MUST be disclosed.

A feedback record SHOULD include rejected alternatives and known interventions from other agents. In multi-agent settings, attribution MUST consider concurrent changes and source dependence; an agent's self-reported success alone is insufficient for independent promotion.

## 8. Learning update classes and allowed effects

| Update class | Typical effect | Required gate |
|---|---|---|
| Evidence attachment | Append source-qualified observation | Provenance, permissions, validity |
| Epistemic revision | Reweight or retract inference | Dependency and uncertainty audit |
| Metric/comparator calibration | Change normalization, threshold, or scoring | Semantic regression, holdout evaluation |
| Policy revision | Change decision preferences or candidate selection | Objective ownership, safety review |
| Capability revision | Replace or add a learning/reasoning plugin | SPEC-004 composition and security tests |
| Relay candidate creation | Package a learned capability for another domain | Receiving-context sandbox and negative-transfer tests |

An **operational state mutation** is not a learning-update class. It MUST pass SPEC-006 authorization and constraint checks. Update effects MUST be declared before invocation. An evidence-append capability MUST NOT silently perform network publication, policy deployment, or external actuation.

## 9. Decision and action separation

The reference decision chain is:

```text
Evidence -> Qualified inference -> Candidate recommendation
         -> Authorization decision -> Execution attempt
         -> Outcome observation -> Feedback attribution
         -> Proposed learning revision -> Validation -> Promotion
```

Every edge MUST preserve a link to its predecessor and the responsible authority. Recommendations MUST identify objective and constraint versions and SHOULD record rejected alternatives. An authorization MUST be scoped to a principal, object set, operation, version, and time window. Execution MUST be idempotent or explicitly describe retry hazards where feasible. Irreversible actions MUST NOT be treated as rollback-capable simply because the model or local simulation state can be reverted.

## 10. Learning promotion gates

A proposed knowledge or model update SHOULD move through the following auditable states:

`proposed -> sandboxed -> evaluated -> reviewed -> authorized -> promoted -> monitored`

The system MUST support `rejected`, `quarantined`, `superseded`, and `revoked` dispositions, with reasons. Promotion requires (a) source and scope validity, (b) contract compatibility, (c) appropriate baseline and holdout evidence, (d) uncertainty and counterexample review, (e) security/permission approval, and (f) an explicit residual register. A model artifact MUST record its training/evaluation data lineage and leakage controls. Monitoring MUST be able to detect performance regression and distribution shift; a detected violation MUST trigger a documented containment or rollback procedure where technically possible.

Promotion of a model is not promotion of a CDE state. If an update proposes a state delta, it MUST be passed as a candidate to the SPEC-006 boundary and evaluated there.

## 11. Multi-perspective and multi-granular learning

Feedback may be valid for one perspective but not another. For example, reducing fleet size may improve an operator's objective while increasing student ride time. A conforming system MUST preserve perspective ownership, competing objective functions, and hard constraints. Aggregation from a bus to a fleet, a student to a cohort, or a function to a repository MUST use a declared granularity bridge compatible with SPEC-003. Group averages MUST NOT be attributed to individual members without an appropriate inference rule.

Cross-granularity updates SHOULD record aggregation method, population coverage, missingness, temporal scope, and potential selection bias. Disagreement between perspectives MUST be represented as disagreement, not automatically averaged into a single universal truth.

## 12. ODK, plugins, SQL, and CDE interfaces

**ODK (SPEC-002):** A feedback evaluation MAY invoke Resolve -> Project -> Align -> Evaluate -> Qualify -> Trace. The resulting differential is a typed measurement with a trace; it is not itself a learning-policy authorization or proof of causation.

**Plugins (SPEC-004):** A learning plugin MUST declare input/output types, epistemic effects, data access, model version, dependencies, and permitted side effects. Plugin composition MUST preserve upstream restrictions.

**SQL adaptation (OCSRE-006):** Row keys MUST NOT be treated as WE identity without resolution. `NULL`, join multiplicity, aggregation grain, row/column permissions, and transformations such as Bucketize, Normalize, Combine, Encode, and Derive MUST retain their SQL semantics and provenance. Training data extraction MUST respect source permissions.

**WE-native CDE (SPEC-006):** A learned policy MAY propose a typed delta against a single WE or composite State-Container. The delta MUST NOT be committed before state-version checks, global constraints, authority checks, and promotion criteria succeed. A locally beneficial delta can be globally invalid.

## 13. Collective learning, relay, and negative transfer

A candidate relay package SHOULD contain: originating domain and object scope; versioned model/plugin/metric; training and evaluation provenance; semantic preconditions; applicable perspectives and granularities; uncertainty; negative cases; licensing and permissions; security constraints; integration cost; and unresolved residuals. The receiving domain MUST independently validate compatibility and usefulness before claiming successful transfer.

UIERU and MLIU may coordinate candidate discovery, sandbox trials, and portfolio decisions. ISGFTR motivates spillover hypotheses; it does not establish that transfer, sustained growth, or a scaling law has occurred. Relay evidence MUST distinguish successful transfer, failed transfer, no measurable gain, and harmful negative transfer. Repeated execution can contribute evidence accumulation, but repeated observations from one source MUST NOT be misrepresented as independent trials.

## 14. AI-generated code governance example

A code-change object may be associated with a calling graph, UTN addresses, differential impact candidates, tests, and security policies. Calling-graph reachability can help localize potentially affected code, but it does not capture all data flow, dynamic dispatch, control flow, reflection, configuration, or external effects. A conforming learning loop SHOULD distinguish: generated patch; static analysis; inferred impact set; test selection recommendation; actual test execution; regression evidence; human or automated authorization; deployment; and post-deployment outcomes.

If a learned test-selection policy reduces tests while missing a security regression, the negative outcome MUST be recorded against the policy and its supporting evidence. A passed unit test MUST NOT automatically authorize deployment. Code-governance capability relay to another repository requires rechecking language, build system, dependency structure, and security assumptions. This is the **Calling Graph -> UTN -> OCSRE** research interface, not a claim of complete program semantics.

## 15. Illustrative scenarios and expected boundaries

### 15.1 School-bus scheduling

A composite WE State-Container includes buses, routes, students, schedules, and resource constraints. Feedback compares planned versus observed ride times, missed pickups, and fleet utilization. A policy update that reduces vehicles but breaches an individual ride-time constraint MUST fail promotion or be scoped as an infeasible candidate. Observational improvement following a route change MUST NOT be labeled causal without a defensible comparison.

### 15.2 Transaction and compositional identity

A transaction pattern may support competing hypotheses about composite actors. A high similarity score MUST remain a qualified inference; it MUST NOT become a verified identity assertion. New contradictory evidence MUST propagate to dependent inferences. External identifying information requires separate lawful access and provenance controls.

### 15.3 SQL-native object learning

A SQL-derived normalized metric is versioned with its transform and source query. Changing a join or bucket boundary can alter apparent performance. The system MUST test for duplication, NULL semantics, leakage, and authorization before using such metrics to revise policies.

### 15.4 Cross-domain relay

A delay-prediction plugin learned in transport MAY be proposed for warehouse dispatch. Its metric semantics, time windows, objectives, and failure cases MUST be checked in the receiving domain; schema compatibility alone is insufficient.

## 16. Conformance profiles and required artifacts

A future implementation MAY claim one or more profiles, but MUST name them precisely:

- **L0 — Evidence/trace profile:** identity-anchored evidence, epistemic class, provenance, and access controls.
- **L1 — Feedback profile:** L0 plus prediction/outcome separation, missingness, attribution qualification, and dependency-aware invalidation.
- **L2 — Learning profile:** L1 plus versioned updates, sandbox evaluation, promotion, monitoring, and regression handling.
- **L3 — Relay profile:** L2 plus cross-domain semantic conformance, independent receiving-domain evaluation, and negative-transfer reporting.

A conformance claim MUST publish a profile declaration, versioned schemas or equivalent field mappings, test cases/results, permission model, evaluation protocol, unresolved failures, and evidence for every mandatory requirement in that profile. An incomplete implementation MUST declare a narrower profile rather than claim full conformance.

## 17. Normative conformance requirements

| ID | Requirement | Priority | Verification evidence |
|---|---|---|---|
| ISG-001 | Bind every accepted learning record to an object/composite scope and version or an explicit unresolved-scope status. | P0 | Missing-identity tests |
| ISG-002 | Preserve perspective, time, granularity, and authority context across feedback transformations. | P0 | Context-mismatch tests |
| ISG-003 | Represent epistemic classes explicitly; prohibit silent class promotion. | P0 | Class-transition audit |
| ISG-004 | Preserve source provenance and typed derivation dependencies. | P0 | Trace reconstruction |
| ISG-005 | Detect circular or duplicated evidence support and qualify independence. | P0 | Dependency-graph tests |
| ISG-006 | Distinguish observation, prediction, recommendation, authorization, execution, and outcome. | P0 | Event-sequence tests |
| ISG-007 | Distinguish association from causal attribution and document causal assumptions. | P0 | Attribution counterexamples |
| ISG-008 | Represent missing, delayed, censored, or selectively observed feedback. | P0 | Missingness fixtures |
| ISG-009 | Propagate source correction/revocation to dependent artifacts for review. | P0 | Invalidation replay |
| ISG-010 | Enforce data permissions and least authority across learning and evidence flows. | P0 | Access-denial tests |
| ISG-011 | Prohibit model or policy promotion from directly committing WE/CDE operational state. | P0 | Mutation-boundary tests |
| ISG-012 | Require explicit promotion gates, approval records, and rejection reasons. | P0 | Lifecycle-state tests |
| ISG-013 | Validate metric/comparator compatibility and record ODK evaluation traces. | P0 | Typed comparator tests |
| ISG-014 | Enforce granularity-bridge contracts and prohibit unjustified member/group inheritance. | P0 | Aggregation counterexamples |
| ISG-015 | Record update class, version, declared effects, and model/data lineage. | P1 | Artifact audit |
| ISG-016 | Evaluate updates against declared baselines, holdouts, and regression criteria. | P1 | Reproducible evaluation |
| ISG-017 | Preserve contradictions, uncertainty, and explicit unresolved residuals. | P0 | Conflict/abstention tests |
| ISG-018 | Require independent receiving-domain validation before claiming successful relay. | P1 | Transfer trials |
| ISG-019 | Report negative transfer, costs, and failure cases rather than only successes. | P1 | Trial accounting |
| ISG-020 | Monitor promoted artifacts and support containment, revocation, or documented rollback limits. | P1 | Drift/revocation tests |
| ISG-021 | Separate code-impact localization from proof of complete behavior or deployment authorization. | P0 | Dynamic-dispatch and security tests |
| ISG-022 | Publish profile-specific conformance evidence and unresolved exceptions. | P1 | Release checklist |

A requirement's priority does not weaken its mandatory status within a claimed profile. Profile-specific applicability MUST be documented; semantic-safety and authority boundaries are not optional merely because a deployment omits advanced learning features.

## 18. Counterexample and adversarial test matrix

| Test | Counterexample | Expected conforming response |
|---|---|---|
| CE-001 | Same SQL row key reused for distinct WEs | Reject automatic identity merge |
| CE-002 | Feedback tied to stale state version | Quarantine or rebase with trace |
| CE-003 | Observation described as verified causal outcome | Reject epistemic promotion |
| CE-004 | Same source republished by three agents | Detect correlated support |
| CE-005 | Circular evidence chain supports itself | Reject independent corroboration |
| CE-006 | Metric units or windows mismatch | Reject or explicitly align |
| CE-007 | Group average assigned to each member | Reject invalid granularity inference |
| CE-008 | Missing feedback interpreted as failure | Preserve missingness status |
| CE-009 | Positive association declared causal | Require identification evidence |
| CE-010 | Training data leaks into holdout | Invalidate evaluation claim |
| CE-011 | Unauthorized private SQL column enters training | Deny and audit access |
| CE-012 | Revoked source remains active in promoted model | Flag dependency and re-evaluate |
| CE-013 | Model promotion directly deploys a bus route | Block unauthorized state mutation |
| CE-014 | Local bus-fleet gain violates student constraint | Reject global promotion |
| CE-015 | Plugin update changes effects without version change | Reject manifest/artifact mismatch |
| CE-016 | One perspective's score represented as universal | Preserve perspective disagreement |
| CE-017 | Transferred plugin fails on receiving-domain data | Record negative transfer |
| CE-018 | Agent grades its own output as independent validation | Require independence qualification |
| CE-019 | Calling graph misses reflection/dynamic dispatch | Mark incomplete impact coverage |
| CE-020 | Passed tests presented as deployment permission | Require separate authorization |

Each test MUST have a reproducible fixture or equivalent executable assertion before a future system claims relevant conformance. The table is a *test plan*, not evidence that tests have been run.

## 19. Evaluation protocol and hypothesis mapping

**OCSH-004 (primary):** Does object-scoped in-situ learning improve feedback utilization or knowledge traceability relative to a non-object-scoped baseline? Pre-register trace completeness, invalidation latency, feedback attribution errors, decision quality, and integration cost. Compare matched tasks under controlled evidence access. Include cases where object anchoring adds overhead without benefit.

**OCSH-003:** Evaluate whether contract-based learning plugins lower adaptation cost without degrading semantic correctness.  
**OCSH-005:** Test whether learning proposals integrate with single and composite WE-native CDE under shared promotion boundaries.  
**OCSH-006:** Measure invalid inference rates across granularity changes with and without explicit bridge contracts.  
**OCSH-007:** Test SQL-to-WE learning transformations for semantic/security preservation.  
**OCSH-008:** Measure validated cross-domain transfer, including negative transfer and total integration cost.  
**OCSH-009:** Test untargeted tasks after a new learning capability is introduced; separate incidental improvements from leakage.  
**OCSH-010:** Study repeated validated capability/question accumulation over multiple cycles; do not infer a scaling law from a short sequence.  
**OCSH-011:** Compare code-impact localization, regression targeting, and traceability against established code-governance baselines.

All hypotheses remain **proposed / E0** at repository inception. Evaluation MUST distinguish contract conformance from measured task benefit and from longer-term structural growth claims. Negative and null results MUST be retained.

## 20. Explicit leftovers and unresolved research questions

1. Final machine-readable schema for learning context, evidence, and feedback envelopes.
2. Formal epistemic type system and permitted transition calculus.
3. Proof obligations for provenance graph acyclicity and independence semantics.
4. Operational definition of sufficient evidence for `causal_supported` across domains.
5. Calibration and comparability of uncertainty measures across heterogeneous plugins.
6. Handling of unbounded delayed feedback and censored outcomes.
7. Temporal consistency under distributed and asynchronous observation.
8. Privacy-preserving provenance without revealing protected sources.
9. Revocation propagation across already-trained models and derived artifacts.
10. Exact semantics of model rollback when effects cannot be fully undone.
11. Stable ownership of perspectives and competing multi-stakeholder objectives.
12. Formal cross-granularity learning and inheritance rules.
13. Adversarial feedback poisoning, sybil corroboration, and strategic reporting.
14. Evaluation under nonstationarity and intervention-induced distribution shift.
15. Counterfactual evaluation where randomized trials are infeasible.
16. Minimum independent review requirements for multi-agent collective learning.
17. Cost models for lineage storage, replay, monitoring, and conformance.
18. Learning/plugin compatibility across schema and metric version changes.
19. Cross-domain transfer thresholds and negative-transfer stop conditions.
20. Alignment of learning promotion with SPEC-006 composite state transactions.
21. Code-governance completeness for dynamic languages and external effects.
22. Formal mapping of residuals to AQSI-style question generation and SIF localization.
23. Empirical benchmarks and baseline selection for OCSH-004 and OCSH-008.
24. Long-horizon evidence required to evaluate OCSH-010 without overclaiming scaling.

These leftovers MUST NOT be silently represented as resolved in downstream papers, release notes, or conformance claims.

## 21. Research interfaces and companion artifacts

- **Core theory:** [OCSRE-007](../docs/OCSRE-007-In-Situ-Object-Learning-Decision-and-Feedback.md), [OCSRE-009](../docs/OCSRE-009-Epistemic-Separation-and-Object-Centric-Evidence-Governance.md), [OCSRE-011](../docs/OCSRE-011-Object-Capability-Spillover-Relay-and-Collective-Structural-Learning.md), [OCSRE-012](../docs/OCSRE-012-Open-Ended-Object-Centric-Structural-Intelligence.md).
- **Upstream contracts:** [SPEC-001](SPEC-001-Object-Identity-Perspective-and-State-Contract.md), [SPEC-002](SPEC-002-Object-Differential-Kernel-and-Comparator-Contract.md), [SPEC-003](SPEC-003-Classical-Reasoning-Preservation-and-Granularity-Contract.md), [SPEC-004](SPEC-004-Object-Plugin-and-Capability-Composition-Contract.md).
- **Forward contract:** [SPEC-006](SPEC-006-WE-Native-CDE-Composite-State-and-Relay-Contract.md).
- **Cases:** [CASE-002](../cases/CASE-002-SQL-Native-Object-Adaptation.md), [CASE-003](../cases/CASE-003-School-Bus-Scheduling-and-Composite-WE-State.md), [CASE-004](../cases/CASE-004-Transaction-and-Compositional-Identity.md), [CASE-005](../cases/CASE-005-Cross-Domain-Object-Plugin-Relay.md), [CASE-006](../cases/CASE-006-AI-Generated-Code-Governance-Through-Calling-Graphs-and-CDE.md).
- **Research trace:** [HYPOTHESIS-REGISTRY](../research-trace/HYPOTHESIS-REGISTRY.md), [COUNTEREXAMPLE-REGISTRY](../research-trace/COUNTEREXAMPLE-REGISTRY.md), [UNRESOLVED-RESIDUALS](../research-trace/UNRESOLVED-RESIDUALS.md).

## 22. Release discipline and conclusion

This specification defines a proposed, falsifiable contract for object-scoped learning and epistemic governance. Its central rule is that **learning is a traceable revision process, not a license to collapse evidence, inference, preference, authorization, and action**. Shared WE interfaces enable learning to be situated in a meaningful object context; ODK and plugins provide reusable computations; CDE provides a separately governed path for state evolution; UIERU/MLIU may relay validated capabilities. None of these connections establishes algorithmic equivalence or automatic transfer benefit.

For v1.0.0, the deliverable is a **research framework and contract proposal**, not a validated runtime, safety certification, or demonstrated scaling law. Future work should first publish schemas, adversarial fixtures, conformance results, and controlled baselines, while preserving explicit unresolved residuals and negative findings.
