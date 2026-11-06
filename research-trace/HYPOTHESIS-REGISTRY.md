# HYPOTHESIS-REGISTRY — OCSRE Research Trace

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Version:** v1.0.0 — Research Framework and Contracts  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**Status:** Research registry; all core hypotheses proposed / E0, not empirically validated  
**License:** Apache-2.0  
**Canonical location:** `research-trace/HYPOTHESIS-REGISTRY.md`

## 1. Purpose and epistemic boundary

This is the canonical index of falsifiable claims in OCSRE. It records what each hypothesis predicts, what would count as evidence against it, which specifications and cases provide a testing surface, and what must be reported before status changes. **A published design, a worked synthetic example, a passing interface check, or agent agreement is not empirical confirmation.** Hypotheses are not the same as normative contract requirements. Requirements may be tested for conformance while a hypothesis about usefulness remains unverified.

The identifiers **OCSH-001 through OCSH-011** and their formulations follow the repository blueprint. This registry adds operationalizations and proposed experiments; these are *research designs*, not retrospectively claimed results. Companion local hypotheses in extensions are subordinate, not replacements for the eleven core identifiers.

## 2. Registry conventions

### 2.1 Status model

| Code | Meaning | Minimum evidence |
|---|---|---|
| E0 — Proposed | Defined claim; no executed evidence | Statement, scope, disconfirmation conditions |
| E1 — Specified | Reproducible protocol and fixtures reviewed | Frozen tasks, measures, baselines, negative tests |
| E2 — Tested | At least one executed study with archived outputs | Executable artifacts, environment, results, failures |
| E3 — Replicated | Independent repetition across relevant settings | Independent run(s), variance, boundary conditions |
| E4 — Qualified support | Multiple rigorous studies support a bounded claim | Effect estimates, uncertainty, limitations, negative evidence |
| EX — Refuted / restricted | Original scope fails or is narrowed | Counterexamples, failure analysis, revised claim |
| EH — On hold | Unresolved confound or inaccessible evidence | Blocking issue and restart condition |

**Current state: every OCSH entry is E0.** The status scale is a proposed research governance convention, not a claim of completed validation. Status changes MUST reference an immutable evidence artifact and an accountable reviewer; a change of wording MUST NOT silently preserve an earlier status.

### 2.2 Mandatory record fields

`id`, `claim`, `scope`, `independent_variable`, `outcome_measure`, `baseline`, `protocol`, `disconfirming_result`, `threats`, `contract_dependencies`, `research_sources`, `evidence_ids`, `status`, `owner`, `last_reviewed`, `leftovers`. Missing fields are recorded as `TBD`, never invented. All observations must identify dataset/fixture versions, evaluation dates, budgets, seeds where applicable, and independent verification status.

### 2.3 Separation of assurance layers

- **Logical assurance:** validity in a precisely declared proof fragment; not evidence about factual premises.
- **Semantic conformance:** typed identity, units, perspectives, granularity, time, access, and provenance preserved.
- **Empirical utility:** measurable performance improvement over an appropriate baseline.
- **Governance:** candidate proposal, verification, authorization, deployment, and rollback are separate states.
- **Growth claims:** longitudinal, resource-accounted gains; artifact count alone is insufficient.

## 3. Master index

| ID | Canonical proposed hypothesis | Primary research surfaces | Status |
|---|---|---|---|
| OCSH-001 | A restricted OCSRE subsystem can preserve classical deductive validity. | OCSRE-002; SPEC-003; CASE-001; EXT-001 | E0 |
| OCSH-002 | A common Object Differential Kernel can be reused across domains without core changes. | OCSRE-004; SPEC-002; CASE-002/003/004/005 | E0 |
| OCSH-003 | Contract-based Object Plugins reduce domain adaptation costs. | OCSRE-005; SPEC-004; CASE-005; EXT-004 | E0 |
| OCSH-004 | In-situ object learning improves feedback use or knowledge traceability. | OCSRE-007/009; SPEC-005; CASE-004/006 | E0 |
| OCSH-005 | WE-native CDE supports both single-object and composite state transitions under shared contracts. | OCSRE-008; SPEC-006; CASE-003/004/006 | E0 |
| OCSH-006 | Explicit cross-granularity contracts reduce invalid inheritance and aggregation. | OCSRE-003; SPEC-001/003; CASE-001/002/003 | E0 |
| OCSH-007 | SQL-to-WE transformations support reusable capabilities while preserving SQL semantics and security. | OCSRE-006; SPEC-001/004/005; CASE-002 | E0 |
| OCSH-008 | Validated capability relay yields measurable cross-domain transfer. | OCSRE-011; SPEC-004/006; CASE-005; EXT-003 | E0 |
| OCSH-009 | New structural capabilities yield measurable gains on untargeted tasks. | OCSRE-011/012; CASE-005; EXT-005 | E0 |
| OCSH-010 | Controlled accumulation and relay can generate sustained, validated new capabilities/questions; scaling behavior remains unproven. | OCSRE-012; EXT-003/004/005 | E0 |
| OCSH-011 | Object-centric code governance improves impact localization, validation targeting and traceability across projects. | OCSRE-010; CASE-006; EXT-002 | E0 |

The canonical statements above are preserved from the repository structure. Slash-separated references denote separate documents, not sections or confirmed dependencies.

## 4. Detailed hypothesis cards

### OCSH-001 — Restricted classical deductive preservation

**Scope.** A specified typed, classical fragment with explicit predicates, quantification, and entailment semantics. **Prediction.** Translation into and out of the object-centric representation preserves valid entailments and does not admit invalid ones in that fragment. **Measure.** Soundness/completeness of a defined translation relative to a reference logic engine, plus proof trace agreement. **Baseline.** A trusted first-order or fragment-appropriate prover with identical premises. **Protocol.** Define grammar and interpretation; run generated valid/invalid entailment pairs and CASE-001 Socrates fixtures; test identity aliasing, quantifier scope, inconsistent premises, temporal changes and illicit group inference. **Disconfirmation.** A valid entailment lost or an invalid entailment introduced under the stated mapping. **Boundary.** No guarantee for probabilistic, temporal, defeasible, or unrestricted natural-language reasoning. **Dependencies.** SPEC-001/003. **Evidence:** none. **Status:** E0.

### OCSH-002 — Cross-domain ODK invariance

**Scope.** At least three distinct, explicitly typed domains using `Object[metricIndices]`. **Prediction.** The same versioned ODK implementation performs contracted differential operations without edits to kernel code. **Measures.** Kernel binary/hash invariance, passed semantic conformance checks, number of domain adapters, comparative defect rates and overhead. **Baseline.** Separate domain-specific comparator implementations. **Protocol.** Freeze ODK version before domain adapters; compare capacity, schedule, and transaction evidence metrics; reject incompatible units and granularity. **Disconfirmation.** Necessary domain-specific kernel modifications or systematically incorrect comparisons despite valid adapters. **Boundary.** Identical interface does not imply equal meaning across domains. **Dependencies.** SPEC-001/002/004. **Evidence:** none. **Status:** E0.

### OCSH-003 — Contracted plugin adaptation efficiency

**Scope.** Predeclared target tasks with independently specified acceptance criteria. **Prediction.** Contract-based Object Plugins reduce engineering adaptation effort or defects relative to matched bespoke integration. **Measures.** Person-hours, changed lines, integration time, conformance defects, runtime overhead and maintenance cost. **Baseline.** Comparable direct implementations with the same team, task scope and tool budget. **Protocol.** Randomize or counterbalance task order; record semantic adapter work and failed transfers; report total cost, not only successful plugin invocation. **Disconfirmation.** No net savings, or savings purchased by unacceptable regressions. **Dependencies.** SPEC-004, SPEC-001/002. **Evidence:** none. **Status:** E0.

### OCSH-004 — In-situ feedback and traceability

**Scope.** Object-linked feedback streams with revisions, conflicting evidence and provenance. **Prediction.** In-situ learning improves feedback utilization and/or audit reconstruction over a non-object-linked feedback workflow. **Measures.** Time to integrate feedback, attribution accuracy, audit completeness, stale-evidence errors, unjustified fact promotion and task performance. **Baseline.** Static model or conventional log-based update process with matched data. **Protocol.** Inject corrected observations and contradictory reports; test temporal and perspective invalidation; blind reviewers to workflow identity. **Disconfirmation.** No traceability gain or more unauthorized belief/state changes. **Boundary.** Traceability gain alone does not establish better decisions. **Dependencies.** SPEC-001/005. **Evidence:** none. **Status:** E0.

### OCSH-005 — Single and composite WE-native CDE

**Scope.** Explicit State-Containers with typed deltas, invariants, path memory and rollback rules. **Prediction.** Shared CDE contracts support valid single-object changes and coordinated multi-object transitions without silently violating global constraints. **Measures.** Constraint violations, valid-state reachability, rollback correctness, candidate coverage and computation cost. **Baseline.** Conventional constraint programming/search or application-specific state transition code. **Protocol.** Exercise CASE-003 fleet-duty merge/split, CASE-004 competing identity hypotheses, and CASE-006 code changes; include infeasible candidates, repeated deltas, loops, and unauthorized commits. **Disconfirmation.** Validated candidates that violate declared invariants or irrecoverable invalid transitions under contract-compliant inputs. **Boundary.** Feasible candidate is not authorized deployment. **Dependencies.** SPEC-001/006. **Evidence:** none. **Status:** E0.

### OCSH-006 — Granularity contract effectiveness

**Scope.** Individual, group, route, transaction cluster and composite-state levels. **Prediction.** Explicit granularity contracts reduce invalid property inheritance, ecological inference and mismatched aggregation. **Measures.** False inference rate on adversarial fixtures, correct abstention, valid aggregation retention and annotation cost. **Baseline.** Same reasoner without explicit granularity checks. **Protocol.** Inject person-to-group and group-to-person fallacies, conflicting time windows, and incompatible denominators. **Disconfirmation.** No reduction in invalid inferences or excessive rejection of valid ones. **Dependencies.** SPEC-001/003/005. **Evidence:** none. **Status:** E0.

### OCSH-007 — SQL-to-WE semantic and security preservation

**Scope.** Declared SQL dialect, schema, transaction isolation, authorization model and five proposed transformations: Bucketize, Normalize, Combine, Encode, Derive. **Prediction.** Typed SQL-to-WE adapters preserve designated SQL results and access restrictions while enabling reusable object capabilities. **Measures.** Differential query equivalence, row multiplicity preservation, NULL/three-valued-logic correctness, aggregate grain consistency, time-window consistency and unauthorized disclosure rate. **Baseline.** Native SQL query results and database policy enforcement. **Protocol.** Freeze query fixtures; compare transformation outputs under nulls, joins, duplicates, windowing, snapshot changes and row-level security; deny forbidden cross-tenant joins. **Disconfirmation.** Semantic mismatches or security bypass under declared supported inputs. **Boundary.** Not all SQL expressions or dialects are assumed covered. **Dependencies.** SPEC-001/004/005; CASE-002. **Evidence:** none. **Status:** E0.

### OCSH-008 — Validated cross-domain relay

**Scope.** Source capability and target task with predeclared acceptance criteria. **Prediction.** Conformance-governed relay produces a measurable target-domain gain relative to a matched no-relay baseline. **Measures.** Target success, adaptation cost, regression rate, transfer acceptance rate, time to validated deployment. **Baseline.** No reuse and unconstrained copy/paste or informal agent handoff, with equal resources. **Protocol.** CASE-005 Tracks A/B/C; freeze source version and target tests before adaptation; independent target reviewer challenges assumptions. **Disconfirmation.** No net benefit or repeated semantic/security regressions. **Boundary.** Transfer success is not automatically unanticipated spillover. **Dependencies.** SPEC-004/005/006. **Evidence:** none. **Status:** E0.

### OCSH-009 — Untargeted-task spillover

**Scope.** Tasks prospectively held out from source capability design and selection. **Prediction.** Newly developed capabilities produce independently verified, resource-adjusted gains on previously unselected tasks. **Measures.** Held-out task improvement, effect uncertainty, novelty audit, leakage incidence and total adaptation/verification cost. **Baseline.** Frozen pre-capability system and resource-matched alternatives. **Protocol.** Pre-register task pool and chronological capability versions; separate capability creators from evaluators; report all attempted transfers, not just successes. **Disconfirmation.** Gains vanish after contamination checks, budget matching or failed-transfer inclusion. **Boundary.** A single post-hoc attractive example is not evidence. **Dependencies.** SPEC-004/005/006; EXT-005. **Evidence:** none. **Status:** E0.

### OCSH-010 — Sustained validated capability/question growth

**Scope.** Multiple rounds of controlled capability generation, evaluation, relay and retirement. **Prediction.** A governed system can repeatedly add useful, nonredundant capabilities or testable questions with retained net value over a defined observation horizon. **Measures.** Independent validated capability yield per unit resource, question novelty/usefulness, retention, regression burden, safety violations and discovery efficiency across rounds. **Baseline.** Fixed catalog, manual-only extension and resource-matched search. **Protocol.** Longitudinal, preregistered rounds with held-out tasks, versioned registries, retirement rules and external audits. **Disconfirmation.** Plateau, growing maintenance cost that erases gains, repeated rediscovery, unsafe self-authorization or benchmark leakage. **Boundary.** Sustained growth over a finite horizon does **not** establish an asymptotic scaling law, AGI, or unlimited open-endedness. **Dependencies.** SPEC-004/005/006; EXT-003/004/005. **Evidence:** none. **Status:** E0.

### OCSH-011 — Object-centric AI code governance

**Scope.** Multi-project AI-assisted changes with Calling Graph, data/control dependencies, policy and test links. **Prediction.** Object-centric governance improves impact localization, test targeting or traceability versus calling-graph-only and standard CI baselines. **Measures.** Impact recall/precision, missed security dependencies, targeted test effectiveness, reviewer effort, provenance reconstruction, latency and false alarms. **Baseline.** Conventional CI/review and Calling Graph-only analysis. **Protocol.** CASE-006 multi-repository fixtures; include unchanged call graph with changed tenant authorization semantics, dynamic dispatch, configuration, schema and deployment edges. **Disconfirmation.** No improvement, critical missed impacts or unacceptable review overhead. **Boundary.** Passing tests is not authorization; call graph stability does not prove semantic stability. **Dependencies.** SPEC-001/002/005/006; EXT-002. **Evidence:** none. **Status:** E0.

## 5. Dependency and inference discipline

| Upstream research result | Could inform | Must NOT be inferred from it alone |
|---|---|---|
| OCSH-001 restricted preservation | Reliable formal reasoning layer | Universal soundness of natural-language inference |
| OCSH-002 unchanged ODK | OCSH-003, OCSH-008 | Correct semantics of every adapter |
| OCSH-003 lower adaptation cost | OCSH-008 | Net target-task performance gain |
| OCSH-004 feedback traceability | OCSH-010 | Better factual truth or autonomous growth |
| OCSH-005 valid composite transitions | OCSH-008, OCSH-011 | Optimal schedules or authorized deployment |
| OCSH-006 fewer granularity errors | OCSH-001, OCSH-007 | Correctness under unmodeled granularity |
| OCSH-007 SQL preservation | OCSH-008 | Transfer to unrelated domains |
| OCSH-008 cross-domain transfer | OCSH-009 | Untargeted spillover |
| OCSH-009 prospective spillover | OCSH-010 | Persistent scaling law |
| OCSH-010 finite-horizon growth | Future scaling studies | Unlimited growth or proven AGI |
| OCSH-011 governance improvement | Cross-project relay studies | Full program correctness/security |

These are research dependencies and plausible evidence pathways, not logical implications.

## 6. Study portfolio and test allocation

| Study ID | Core hypotheses | Fixture families | Essential controls |
|---|---|---|---|
| STUDY-LOGIC-01 | 001, 006 | CASE-001, EXT-001 | Reference prover, invalid entailments, identity/granularity traps |
| STUDY-ODK-01 | 002, 003 | CASE-002/003/004/005 | Frozen kernel, domain-specific baseline, matched budget |
| STUDY-FEEDBACK-01 | 004 | CASE-004/006 | Conflicting evidence, stale data, provenance audit |
| STUDY-CDE-01 | 005, 006 | CASE-003/004/006 | Global invariants, rollback, loops, unauthorized commit |
| STUDY-SQL-01 | 007 | CASE-002 | Native SQL oracle, NULL, joins, row-level security |
| STUDY-RELAY-01 | 003, 008 | CASE-005 | Target-blind tests, failed-transfer ledger, cost accounting |
| STUDY-SPILLOVER-01 | 009 | EXT-005 | Prospective holdout, chronology, leakage audit |
| STUDY-GROWTH-01 | 010 | EXT-003/004/005 | Longitudinal baselines, retirement, total cost |
| STUDY-CODE-01 | 011 | CASE-006 | Calling Graph-only, standard CI, semantic adversaries |

Each study MUST register both positive and negative fixtures. A negative test is a success when an invalid inference, unsafe transfer, or unauthorized transition is **rejected**; this must not be misreported as a failure of the framework.

## 7. Minimal evidence and experiment record schemas

```yaml
hypothesis_id: OCSH-008
study_id: STUDY-RELAY-01
protocol_version: TBD
preregistration_uri: TBD
source_capability_version: TBD
target_task_manifest: TBD
baseline_manifest: TBD
resource_budget: TBD
acceptance_criteria: TBD
negative_fixture_ids: []
execution_environment: TBD
results_artifact_ids: []
independent_reviewer: TBD
observed_effect: null
uncertainty_interval: null
confounds: []
status: E0
```

```yaml
evidence_id: TBD
hypothesis_id: TBD
study_id: TBD
artifact_uri: TBD
artifact_hash: TBD
fixture_version: TBD
observed_at: TBD
provenance: TBD
independent_verification: false
supports_or_challenges: TBD
limitations: []
review_decision: pending
```

Do not fill these records with synthetic metrics presented as observations. Proposed toy calculations belong in the case text and must be labeled synthetic.

## 8. Governance of revisions, counterexamples and residuals

1. Preserve canonical OCSH identifiers. If a hypothesis changes materially, create a versioned claim and log the change in `DECISION-LOG.md`.
2. Register counterexamples in `COUNTEREXAMPLE-REGISTRY.md`, including unresolved and inconclusive cases. A counterexample may narrow a scope rather than refute all related hypotheses.
3. Register ambiguous terms and changed definitions in `DEFINITION-REGISTRY.md`; never alter a metric definition mid-study without recording the break.
4. Record outstanding validation gaps in `UNRESOLVED-RESIDUALS.md`; duplicate execution and failed attempts can remain valuable relay evidence.
5. Require an independent reviewer for E2+ promotion, including a security reviewer for claims involving authority, SQL permissions or code deployment.
6. Keep claim evidence distinct from authorization. No hypothesis status permits bypassing policy or human review.
7. Report null results, regressions, adverse events and abandoned trials alongside successes.

## 9. Crosswalk to companion hypothesis families

The core OCSH namespace is stable. Companion extensions introduce local, more granular hypotheses: `MAH-*` in EXT-003 (multi-agent coordination), `OMPH-*` in EXT-004 (metric/plugin/policy evolution), and `SSH-*` in EXT-005 (spillover/scaling). Their exact propositions and local numbering are governed by their respective source documents; this registry does not silently rename or merge them. Future versions SHOULD add a verified, line-level local-to-core mapping after review. The formal-logic and SIF localization extensions likewise provide local test obligations without automatically creating new OCSH IDs.

## 10. Explicit leftovers and open research questions

| Residual | Open question / action | Relevant IDs |
|---|---|---|
| HR-001 | Define a fully formal restricted object-logic grammar and translation proof obligations | 001 |
| HR-002 | Select trusted proof engines and exhaustive/representative generators | 001 |
| HR-003 | Publish stable ODK API and hash-frozen test harness | 002 |
| HR-004 | Define cost accounting for semantic adapters and maintenance | 003, 008 |
| HR-005 | Design blinded feedback provenance review | 004 |
| HR-006 | Formalize composite state invariants and delta rollback | 005 |
| HR-007 | Build adversarial multi-granularity datasets | 006 |
| HR-008 | Declare SQL dialect/isolation/security support matrix | 007 |
| HR-009 | Verify NULL, bag semantics, aggregation and row-level security | 007 |
| HR-010 | Freeze target-domain acceptance tests before relay | 008 |
| HR-011 | Preregister untargeted tasks and chronology audit | 009 |
| HR-012 | Specify task novelty and capability nonredundancy measures | 009, 010 |
| HR-013 | Define finite-horizon versus scaling-law statistical criteria | 010 |
| HR-014 | Define capability retirement and negative-transfer policy | 008, 010 |
| HR-015 | Build multi-project calling/data/control/security graph fixtures | 011 |
| HR-016 | Define critical false-negative thresholds for security impact analysis | 011 |
| HR-017 | Determine independent reviewer roles and conflict rules | all |
| HR-018 | Publish reproducibility manifests and archival conventions | all |
| HR-019 | Determine when a failed conformance check is a spec defect vs implementation defect | all |
| HR-020 | Establish external replication and adversarial evaluation partners | all |
| HR-021 | Audit data licensing, privacy and sensitive evidence access | 004, 007, 011 |
| HR-022 | Bound policy evolution and prevent self-authorization | 010, 011 |
| HR-023 | Quantify relay overhead and collective learning retention | 008, 010 |
| HR-024 | Maintain explicit comparison with conventional non-OCSRE methods | all |

## 11. Proposed validation gates and release interpretation

**Gate A — Specification readiness:** canonical claims, typed interfaces, negative tests and baselines documented. **Gate B — Harness readiness:** fixtures and executable or formal oracles available. **Gate C — Evidence readiness:** study execution with complete result ledger, independent review and counterexample triage. **Gate D — Qualified support:** replication and bounded effect claims. At v1.0.0, the repository may publish this registry as a research artifact without passing Gates B–D. Publishing it is not an empirical endorsement of OCSRE.

## 12. Maintenance checklist

- [ ] Canonical IDs OCSH-001–011 remain stable and unique.
- [ ] All claims retain E0 unless supported by linked evidence.
- [ ] Every study names a baseline, outcome, disconfirmation condition and safety boundary.
- [ ] Negative results and semantic mismatches are not omitted.
- [ ] Local extension hypotheses are mapped only after source review.
- [ ] Evidence and authorization decisions remain separate.
- [ ] Changed claims, definitions and unresolved residuals have trace records.
- [ ] Public release notes do not describe proposed experiments as completed validation.

---

**Research posture:** Specifications/Contracts First; Conformance Before Runtime; Explicit Leftover. The purpose of this registry is to make OCSRE's most ambitious claims *testable and revisable*, not to declare them established.
