# VALIDATION-ROADMAP — OCSRE Staged Conformance and Evidence Program

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Version:** v1.0.0 — Research Framework and Contracts  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**License:** Apache-2.0  
**Canonical location:** `VALIDATION-ROADMAP.md`  
**Research status:** Proposed validation plan. **All OCSH-001–OCSH-011 remain E0 — Proposed.** No implementation, completed test, independent replication, demonstrated performance advantage, or Scaling Law is asserted here.

## 1. Mission and boundaries

This roadmap operationalizes [`TESTABLE-HYPOTHESES.md`](TESTABLE-HYPOTHESES.md) and the canonical [`research-trace/HYPOTHESIS-REGISTRY.md`](research-trace/HYPOTHESIS-REGISTRY.md). It is a **sequence of proposed research gates**, not a report of completed work. The central aim is to determine whether a typed World Entity (WE)/Object substrate can preserve well-defined semantics while coordinating classical reasoning, the Object Differential Kernel (ODK), Object Plugins, SQL adaptation, in-situ learning, WE-native Constrained Delta Evolution (CDE), SIF Localization, capability relay, and AI-generated code governance.

The program must not collapse these distinct claims:

1. **Formal or semantic conformance:** behavior respects a stated contract in a stated domain.
2. **Empirical utility:** a method outperforms a fair baseline on a predeclared task distribution.
3. **Security and authority:** information access and actions satisfy independently defined policy.
4. **Transfer:** a reusable capability performs successfully in a different context.
5. **Spillover:** a validated gain appears on tasks not targeted by the original development.
6. **Growth or scaling:** repeated, independently evaluated capability expansion is sustained after accounting for costs and selection effects.

A result at one level is not automatic evidence for another. This roadmap preserves **Specifications/Contracts First; Conformance Before Runtime; Explicit Leftover**.

## 2. Canonical sources and authority

| Asset | Governing role |
|---|---|
| [`research-trace/HYPOTHESIS-REGISTRY.md`](research-trace/HYPOTHESIS-REGISTRY.md) | Canonical hypothesis identity, wording, status and evidence record |
| [`TESTABLE-HYPOTHESES.md`](TESTABLE-HYPOTHESES.md) | Experimental families, controls, metrics, adversarial cases and protocol obligations |
| [`research-trace/DEFINITION-REGISTRY.md`](research-trace/DEFINITION-REGISTRY.md) | Semantic terminology and non-equivalence boundaries |
| [`research-trace/COUNTEREXAMPLE-REGISTRY.md`](research-trace/COUNTEREXAMPLE-REGISTRY.md) | Counterexamples, dispositions and falsification evidence |
| [`research-trace/DECISION-LOG.md`](research-trace/DECISION-LOG.md) | Versioned architectural and protocol decisions |
| [`research-trace/UNRESOLVED-RESIDUALS.md`](research-trace/UNRESOLVED-RESIDUALS.md) | Outstanding blockers, owners and closure criteria |
| [`OPEN-QUESTIONS.md`](OPEN-QUESTIONS.md) | Research-facing unresolved questions |
| [`FUTURE-DIRECTIONS.md`](FUTURE-DIRECTIONS.md) | Long-horizon agenda, not evidence of feasibility |

The six contracts in `specs/` are normative **only within their explicitly declared scopes**. A manuscript, diagram, sample trace, or roadmap milestone is not a conformance certificate. If this roadmap and a canonical registry disagree, the discrepancy must be recorded in the Decision Log; do not silently rewrite history.

## 3. Evidence ladder and promotion controls

| State | Meaning | Minimum evidence required | What it does **not** mean |
|---|---|---|---|
| **E0 — Proposed** | Falsifiable claim is articulated | Named hypothesis and intended scope | A test has been run |
| **E1 — Specified** | Protocol is frozen and independently reviewed | Versioned preregistration, fixtures, baselines, thresholds, controls, reviewer sign-off | Positive outcome |
| **E2 — Tested** | Experiment was executed and auditable | Immutable run artifacts, failures, resource accounting, raw results, reproducible environment | Independent replication |
| **E3 — Replicated** | Independent execution corroborates a bounded result | Separate operator/environment, agreed scope, comparable protocol, disclosed deviations | Universal validity |
| **E4 — Qualified support** | Multiple rigorous studies support a restricted claim | Synthesis with uncertainty, limitations, negative findings and domain boundaries | An unrestricted law |
| **EX / EH** | Refuted or restricted / on hold | Counterevidence or documented blocker and rationale | Silent removal of the hypothesis |

**Promotion is evidence-specific, not automatic or collective.** A successful SQL conformance test does not promote an ODK cross-domain utility hypothesis. A refuted invariant must be recorded even if average task accuracy is favorable. A security failure can block deployment regardless of an otherwise positive utility score.

## 4. Roadmap architecture: six gated phases

The phases are dependency-oriented; they are **not calendar commitments**. Each phase may iterate, branch, or stop. The phase names align with [`FUTURE-DIRECTIONS.md`](FUTURE-DIRECTIONS.md).

| Phase | Focus | Principal studies | Exit condition |
|---|---|---|---|
| **P0 — Semantic Foundations** | Identity, perspective, types, logic, reference oracle | STUDY-LOGIC-01 preparation | Reviewed, versioned contracts and negative fixtures |
| **P1 — Minimal Conformance Prototypes** | ODK, Object Plugin, SQL adapter | STUDY-LOGIC-01; STUDY-ODK-01; STUDY-SQL-01 | Reproducible contract tests and documented deviations |
| **P2 — Governed State and Feedback** | In-situ learning, CDE, composite states, SIF addressing | STUDY-FEEDBACK-01; STUDY-CDE-01 | Traceable state transitions and governance checks |
| **P3 — Domain and Governance Stress Tests** | Multi-agent challenges, weak identity, code impact | STUDY-CDE-01; STUDY-CODE-01 | Cross-domain adversarial evaluation without unauthorized effects |
| **P4 — Evolution and Relay Experiments** | Plugin/capability transfer, competitive validation | STUDY-RELAY-01 | Bounded, independently assessed transfer evidence |
| **P5 — Spillover and Scaling Validation** | Untargeted tasks and longitudinal capability growth | STUDY-SPILLOVER-01; STUDY-GROWTH-01 | Preregistered held-out results with cost and selection accounting |

A phase may be entered for **protocol design** before earlier phases finish; it may not claim **validated downstream performance** while its prerequisite semantics are unresolved.

## 5. P0 — Semantic foundations and test oracles

### P0.1 Deliverables

- A machine-readable Object/WE reference schema with stable identity, state, perspective, time, granularity, provenance, and authorization fields.
- A typed MetricIndex vocabulary with units, admissible operations, missingness, and uncertainty rules.
- A restricted classical-logic fragment with a reference deduction oracle; clear separation of deductive entailment from empirical support.
- A reference model for cross-granularity transitions, including prohibited inheritance and aggregation.
- A trace schema binding an input, versioned contract, decision, evidence reference, and output to a reproducible run.
- A canonical fixture registry: valid cases, minimal counterexamples, expected abstentions, and security-denial cases.

### P0.2 Acceptance gate

The team must be able to distinguish **identity equality, metric similarity, evidential association, and authorization** in tests. The schema must distinguish ODK **comparison/differential** outputs from CDE **typed state-changing deltas**. At least one negative fixture for each critical semantic boundary must have an expected, independently reviewed outcome. Unspecified fields remain `TBD`, not invented defaults.

**Primary contracts:** [`SPEC-001`](specs/SPEC-001-Object-Identity-Perspective-and-State-Contract.md), [`SPEC-003`](specs/SPEC-003-Classical-Reasoning-Preservation-and-Granularity-Contract.md).  
**Reference case:** [`CASE-001`](cases/CASE-001-Person-and-Classical-Reasoning.md).

## 6. P1 — Minimal conformance prototypes

### P1.1 Minimal Auditable Conformance Slice (MACS)

Implement only the smallest slice needed to reveal structural errors:

1. **One ObjectRef/StateRef schema**, with explicit identity, perspective, granularity and access scope.
2. **One typed ODK comparator**, deterministic on frozen inputs, with declared metric semantics.
3. **One contract-checked Object Plugin**, whose adapter declares preconditions, outputs, version, dependencies and permitted side effects.
4. **One SQL-to-WE adapter**, with a native SQL oracle for NULL, joins, aggregation, row-level authorization and provenance.
5. **One CDE typed-delta validator**, initially as a contract checker rather than a search optimizer.
6. **One shared conformance runner**, retaining fixtures, input hashes, expected/observed outputs, failure traces and execution budget.

The slice is intentionally narrow. It should not be presented as a general-purpose AGI runtime, production query engine, or completed CDE implementation.

### P1.2 Proposed experiments

- **STUDY-LOGIC-01 (OCSH-001/006):** compare the restricted OCSRE reasoner with a reference logic engine; measure entailment preservation, invalid inheritance and abstention.
- **STUDY-ODK-01 (OCSH-002/003):** test whether the **same kernel implementation** can operate across declared domain adapters without hidden domain-specific branches; separately measure adapter effort and correctness.
- **STUDY-SQL-01 (OCSH-007):** compare SQL-native query results and permissions with transformed WE outputs under a frozen semantic mapping.

### P1.3 Stop conditions

Stop promotion when an identity collision, unsupported granularity lift, SQL three-valued logic mismatch, unauthorized row exposure, or unversioned adapter behavior is confirmed. Record the smallest reproducing case and revise the affected contract or scope before repeating. Do not conceal an invalid invariant behind aggregate accuracy.

**Primary contracts:** [`SPEC-002`](specs/SPEC-002-Object-Differential-Kernel-and-Comparator-Contract.md), [`SPEC-004`](specs/SPEC-004-Object-Plugin-and-Capability-Composition-Contract.md).  
**Reference cases:** [`CASE-002`](cases/CASE-002-SQL-Native-Object-Adaptation.md), [`CASE-005`](cases/CASE-005-Cross-Domain-Object-Plugin-Relay.md).

## 7. P2 — Governed state, feedback and evolutionary localization

### P2.1 In-situ learning

For **STUDY-FEEDBACK-01 (OCSH-004)**, preregister the meaning of a learning event: what was observed, who/what supplied feedback, which Object state and metric changed, which policy authorized the update, and how a prior version can be inspected or restored. Compare against static feedback or conventional logging. Evaluate trace completeness, error correction, calibration, latency, resource cost, contamination and regression—not simply the number of recorded events.

### P2.2 WE-native CDE

For **STUDY-CDE-01 (OCSH-005/006)**, validate typed deltas against state-container invariants before optimization. Required tests include single-object transitions, composite constraints, path-memory/no-reuse rules, NoSubtree pruning, Loop-Back termination, admissible rollback and the distinction between a proposed transition and an authorized action.

School-bus scheduling provides a bounded domain with explicit vehicle, route, time and student constraints; transaction/compositional-identity reasoning provides a different evidence and uncertainty regime. Neither case should be represented as a validated solution in advance.

### P2.3 SIF localization contract

Evaluate **referential localization** (finding an existing object, state, capability or evidence address) separately from **evolutionary localization** (searching for a valid, not-yet-instantiated state through constrained deltas). CDE can serve as a proposed evolutionary localization pillar in SIF without implying that addressing and optimization are the same algorithm.

**Primary contracts:** [`SPEC-005`](specs/SPEC-005-In-Situ-Learning-Feedback-and-Epistemic-Governance-Contract.md), [`SPEC-006`](specs/SPEC-006-WE-Native-CDE-Composite-State-and-Relay-Contract.md).  
**Reference cases:** [`CASE-003`](cases/CASE-003-School-Bus-Scheduling-and-Composite-WE-State.md), [`CASE-004`](cases/CASE-004-Transaction-and-Compositional-Identity.md).

## 8. P3 — Domain stress, adversarial evaluation and code governance

Use held-out scenarios, alternative domain schemas, injected ambiguity, missing evidence, contradictory agent reports, stale references, access-control boundaries, and distribution shifts. The purpose is to discover where a purportedly general structural method breaks.

For **STUDY-CODE-01 (OCSH-011)**, compare at least three approaches: standard CI/review; Calling Graph-only impact analysis; and a governed multi-graph approach combining calls, data/control dependencies, object contracts, UTN localization and proposed CDE change paths. Score impact recall/precision, missed security dependencies, false positives, reviewer effort and unauthorized deployment attempts. An unchanged Calling Graph must not be treated as proof that data semantics, tenant isolation, or permissions are unchanged.

Use **read-only, sandboxed** test repositories and simulated deployments unless a separate human authority explicitly permits actions. The structural system can recommend or reject a change; it cannot infer deployment authorization from test success.

**Reference case:** [`CASE-006`](cases/CASE-006-AI-Generated-Code-Governance-Through-Calling-Graphs-and-CDE.md).

## 9. P4 — Capability relay and independent challenge

For **STUDY-RELAY-01 (OCSH-003/008)**, define a transferable capability as a versioned artifact with inputs, outputs, preconditions, domain assumptions, metric semantics, policy requirements, provenance, known failures and conformance tests. Freeze source-domain development before evaluating the target domain.

Compare **no relay**, **informal handoff**, and **contract-governed relay**, using matched resources. Measure successful adaptation, integration time, negative transfer, revalidation effort, runtime cost and policy failures. Require independent challenge of the transferred artifact: multiple agents that share training context or source code do not automatically provide independent confirmation.

UIERU-style relay and collective learning should retain both successful and unsuccessful transfers. A failed transfer is useful evidence about the capability boundary, not a reason to discard the record.

## 10. P5 — Untargeted spillover and longitudinal growth

### P5.1 Untargeted spillover

For **STUDY-SPILLOVER-01 (OCSH-009)**, preregister a held-out task set that was not used to design, select or tune the new capability. Use frozen baseline snapshots and matched compute/human-effort budgets. Audit direct and indirect data leakage, overlapping task families, benchmark reuse and post-hoc selection. Report failures and null effects alongside successes.

A new capability that helps only its intended target may be valuable, but it is not evidence of **untargeted spillover**.

### P5.2 Sustained growth

For **STUDY-GROWTH-01 (OCSH-010)**, track over multiple preregistered cycles: validated capabilities added, genuinely new questions generated, independent verification rate, failed proposals, revalidation burden, cumulative cost, maintenance burden and performance on frozen and refreshed held-out tasks.

Compare with fixed-catalog and manual-only evolution baselines. Measure survivorship bias and the cost of maintaining older capabilities. A rising count of proposed plugins, metrics or questions is not evidence of sustained intelligence improvement. Finite positive growth does not by itself establish an asymptotic Scaling Law.

## 11. Cross-study protocol requirements

Every experiment must publish or securely retain the following **before results are inspected**:

| Required field | Purpose |
|---|---|
| Hypothesis ID and frozen protocol version | Prevent post-hoc claim substitution |
| Inclusion/exclusion criteria and domain scope | Define the population to which results apply |
| Baseline, ablations and negative controls | Separate structural benefit from added resources |
| Data provenance, splits and temporal cutoff | Prevent contamination and leakage |
| Metric definitions and practical thresholds | Make success and failure interpretable |
| Seeds, compute, human effort and wall time | Support fair comparisons |
| Security policy and action authority | Separate recommendation from permission |
| Expected failure and abstention behavior | Prevent unsafe forced answers |
| Independent reviewer and deviation process | Reduce experimenter discretion |
| Artifact hashes and environment manifest | Support reproduction and auditing |
| Uncertainty, missing results and multiple comparisons | Avoid selective reporting |
| Counterexample disposition and residuals | Keep negative knowledge in the research record |

Thresholds and sample sizes are **TBD until preregistered**. They must not be invented in this roadmap or chosen after observing results. For an invariant, one verified in-scope counterexample may be decisive; for utility, use appropriate uncertainty and a minimum practically meaningful effect.

## 12. Shared conformance harness and artifact layout

The following is a **suggested future experiment workspace**, not a claim that these files already exist in the v1.0.0 repository:

```text
validation/                          # proposed; not part of current release inventory
  protocols/                        # immutable preregistrations
  fixtures/
    positive/
    negative/
    adversarial/
  reference-oracles/
  adapters/
  harness/
  runs/<study-id>/<run-id>/
    manifest.yaml
    inputs-and-hashes.json
    observed-results.json
    metrics.json
    failures-and-abstentions.json
    environment.lock
  independent-replications/
  synthesis/
```

Example **proposed** run manifest (all values are placeholders):

```yaml
study_id: STUDY-CDE-01
hypothesis_ids: [OCSH-005, OCSH-006]
protocol_version: TBD
preregistration_uri: TBD
contract_versions: TBD
fixture_manifest_hash: TBD
baseline_id: TBD
code_commit: TBD
container_digest: TBD
random_seeds: TBD
execution_date: TBD
reviewer_id: TBD
security_policy_version: TBD
primary_metric: TBD
predeclared_threshold: TBD
result_artifact_uri: TBD
counterexample_ids: []
residual_ids: []
evidence_status: E0
```

Do not use this sample as evidence of a run. Retain immutable raw results and publish redacted summaries where privacy, security or licensing limits prevent raw release.

## 13. Proposed conformance gate checklist

A study cannot be promoted from protocol to claimed validation unless each applicable item is documented:

- [ ] Canonical hypothesis and scope matched to the registry.
- [ ] Contract versions, data schemas and oracles reviewed.
- [ ] Positive, negative and adversarial fixtures frozen.
- [ ] Baselines and ablations budget-matched.
- [ ] Security and action-authorization boundaries explicit.
- [ ] Statistical or logical decision rule preregistered.
- [ ] Reproducible execution environment and immutable logs available.
- [ ] Failures, abstentions and contradictory observations reported.
- [ ] Counterexamples and unresolved residuals linked.
- [ ] Independent review performed before any E1 promotion.
- [ ] Independent replication performed before any E3 promotion.
- [ ] E4 claim bounded by domains, tasks, uncertainty and costs.

The checklist is a **process requirement**, not a claim of completion.

## 14. Cross-domain validation matrix

| Domain | Principal stressor | Suggested studies | Failure to detect |
|---|---|---|---|
| Person/classical syllogism | Type, quantification, premise truth and granularity | LOGIC | Invalid entailment or ungrounded truth assertion |
| SQL-native objects | NULL, joins, grouping, row policy and provenance | SQL, ODK | Changed query meaning or unauthorized disclosure |
| School-bus scheduling | Composite resource/time constraints | CDE | Locally valid but globally infeasible transition |
| Transaction/compositional identity | Weak evidence and uncertain attribution | CDE, ODK | Similarity incorrectly promoted to identity |
| Cross-domain Object Plugins | Contract compatibility and negative transfer | ODK, RELAY | Hidden domain branches or silent adapter mismatch |
| AI-generated code | Call/data/control dependencies and deployment policy | CODE | Missed semantic impact or unauthorized action |
| Novel held-out task families | Leakage, transfer and long-run drift | SPILLOVER, GROWTH | Targeted tuning mistaken for spontaneous gain |

A domain appearing in the matrix is a **candidate testbed**, not a claim that a benchmark, dataset or executable implementation already exists.

## 15. Independent replication and adversarial red-team protocol

Independent replicators should receive the frozen protocol, input fixtures, acceptance criteria and artifact hashes, but should not be required to accept the original team's interpretations. Record their implementation differences and whether they independently re-created or merely reran an existing artifact. Challenge the strongest claims first: semantic preservation, authorization boundaries, cross-domain reuse, untargeted spillover and sustained growth.

When a counterexample appears: preserve the original observation; determine if it is in scope; attempt minimal reproduction; document the oracle and alternative explanations; assign a counterexample ID; then choose **refute, restrict, repair, or hold** with a versioned Decision Log entry. A repaired implementation does not erase the original failure.

## 16. Decision rights and change control

**Proposed roles** (may be combined in small exploratory work, but conflicts must be disclosed): protocol owner, contract reviewer, benchmark custodian, security reviewer, independent replicator and evidence registrar. The evidence registrar updates the canonical Hypothesis Registry only after required review. Protocol changes after preregistration require a new version and must distinguish exploratory from confirmatory outcomes.

The human/organizational owner of a real system retains authority for deployment, financial transactions, sensitive data access and policy changes. Neither an Object Plugin, a relay agent, nor a CDE-generated path inherits that authority by implication.

## 17. Risks, mitigations and explicit stopping rules

| Risk | Mitigation | Stop / restrict trigger |
|---|---|---|
| Semantic drift across adapters | Typed schemas, oracle comparison, versioning | Confirmed in-scope semantic mismatch |
| Identity conflation | Distinct IdentityRef, similarity and evidence fields | False identity merge |
| Metric gaming or benchmark leakage | Frozen holdouts and independent custodians | Demonstrated contamination |
| Unsafe CDE transitions | Precondition/invariant checks and rollback | Constraint or authorization violation |
| SQL policy bypass | Native policy oracle and denial fixtures | Unauthorized row or field exposure |
| Correlated multi-agent errors | Independent adversarial review | False claim of independent consensus |
| Capability proliferation without value | Cost-normalized evaluation and pruning | No reproducible gain or excessive maintenance |
| Misleading scaling claims | Longitudinal preregistration and uncertainty | Selective cycles or insufficient horizon |
| Code change blind spots | Multi-graph semantic impact tests | Missed security-relevant dependency |

A stop trigger blocks the affected claim or execution path; it does not require abandoning unrelated research.

## 18. Milestones and proposed release evidence packages

| Milestone | Deliverable | Required qualification |
|---|---|---|
| **M0** | Reviewed semantic contracts, negative fixtures, oracles | Protocol-ready only |
| **M1** | MACS conformance runner and immutable run format | Engineering prototype, not general solution |
| **M2** | Logic, ODK and SQL comparison reports | Domain-bounded test evidence |
| **M3** | Feedback and CDE transition/constraint reports | Governance and feasibility evidence |
| **M4** | Code-impact and adversarial domain reports | Bounded safety/impact assessment |
| **M5** | Relay comparisons and independent replication | Conditional cross-domain transfer support |
| **M6** | Held-out spillover and longitudinal growth reports | Qualified evidence; scaling only if separately warranted |

For each milestone, publish: a short claim statement, scope, protocol version, baseline, negative controls, results, uncertainty, failures, counterexamples, residuals, reproducibility instructions and a machine-readable manifest. If no execution occurred, label the package **design-only**.

## 19. Traceability matrix: hypotheses to phases

| Hypothesis | Primary phase | Study | Required prerequisite |
|---|---|---|---|
| OCSH-001 | P0–P1 | STUDY-LOGIC-01 | Restricted logic fragment and oracle |
| OCSH-002 | P1 | STUDY-ODK-01 | Typed ODK and multiple adapters |
| OCSH-003 | P1/P4 | STUDY-ODK-01; STUDY-RELAY-01 | Plugin contracts and cost accounting |
| OCSH-004 | P2 | STUDY-FEEDBACK-01 | Feedback provenance and baseline |
| OCSH-005 | P2–P3 | STUDY-CDE-01 | Typed delta and composite invariants |
| OCSH-006 | P0–P2 | STUDY-LOGIC-01; STUDY-CDE-01 | Granularity contracts and denial tests |
| OCSH-007 | P1 | STUDY-SQL-01 | Native SQL/policy oracle |
| OCSH-008 | P4 | STUDY-RELAY-01 | Frozen source capability and target domain |
| OCSH-009 | P5 | STUDY-SPILLOVER-01 | Untargeted held-out tasks |
| OCSH-010 | P5 | STUDY-GROWTH-01 | Multiple cycles and cost-normalized baselines |
| OCSH-011 | P3 | STUDY-CODE-01 | Call/data/control graph and policy fixtures |

## 20. Explicit leftovers — VR-L001 through VR-L020

These items are deliberately **open**. Their presence does not imply that a solution or artifact exists.

| ID | Open decision or missing asset | Proposed closure evidence |
|---|---|---|
| VR-L001 | Canonical executable ObjectRef schema | Reviewed schema and compatibility fixtures |
| VR-L002 | Stable identity versus temporal alias policy | Adversarial identity tests and decision record |
| VR-L003 | MetricIndex type/unit algebra | Reference oracle and invalid-operation fixtures |
| VR-L004 | Restricted deductive fragment | Formal specification and reference proofs/tests |
| VR-L005 | Granularity coercion rules | Explicit allowed/denied mappings |
| VR-L006 | ODK kernel boundary | Source-level invariance audit across domains |
| VR-L007 | Object Plugin compatibility semantics | Conformance matrix and revocation tests |
| VR-L008 | SQL mapping for NULL/joins/aggregation | Native SQL differential test suite |
| VR-L009 | Security-policy equivalence | Row/column denial oracle and threat review |
| VR-L010 | In-situ feedback attribution | Versioned feedback provenance test |
| VR-L011 | CDE path-memory and rollback model | State transition property tests |
| VR-L012 | Composite-state feasibility oracle | Domain constraint model and negative cases |
| VR-L013 | Evolutionary localization measurement | Separate addressing/search benchmarks |
| VR-L014 | Weak-evidence identity calibration | Uncertainty-aware labeled test protocol |
| VR-L015 | Independent multi-agent challenge | Reviewer separation and disagreement protocol |
| VR-L016 | Code governance dependency completeness | Multi-graph security regression fixtures |
| VR-L017 | Transfer budget normalization | Matched-resource relay benchmark |
| VR-L018 | Untargeted task isolation | Preregistered sealed holdout and leakage audit |
| VR-L019 | Growth horizon and maintenance cost | Longitudinal protocol with survival accounting |
| VR-L020 | External replication infrastructure | Independent rerun and reproducibility package |

Transfer material unresolved items to [`research-trace/UNRESOLVED-RESIDUALS.md`](research-trace/UNRESOLVED-RESIDUALS.md) using that registry's canonical identifiers and governance rules. Do not assume `VR-L###` identifiers are already entries there.

## 21. First recommended execution sequence

The immediate, bounded next step is **not** a full OCSRE runtime. It is a versioned **MACS protocol package**:

1. Freeze the minimal identity/perspective/granularity schema and negative cases.
2. Specify one ODK comparator and one domain adapter with a reproducible oracle.
3. Add a SQL mapping fixture that tests NULL and authorization denial.
4. Add a CDE typed-delta checker with one valid and one globally invalid composite transition.
5. Implement a read-only harness that emits an immutable manifest and preserves failures.
6. Obtain an independent protocol review, then consider E0 → E1 **only for the corresponding hypotheses and scopes**.
7. Run tests only after preregistration; publish E2 evidence only if real artifacts exist.

This sequence gives early evidence about the most important structural interfaces while minimizing implementation cost and avoiding premature claims about intelligence growth.

## 22. Publication, interpretation and closing principle

The v1.0.0 DOI release may legitimately publish a coherent architecture, formal contracts, research hypotheses, adversarial examples and this roadmap **as a research proposal**. It must not describe the roadmap as completed validation. Future release notes should state precisely which studies ran, which failed, which were independently replicated and which claims remain open.

**The measure of progress is not the number of diagrams, plugins, deltas, agents or proposed capabilities. It is the number of precisely scoped claims that survive reproducible tests, meaningful counterexamples and independent challenge—at an honestly reported cost.**

---

### Companion reading

- [`README.md`](README.md) — project orientation.
- [`START-HERE.md`](START-HERE.md) — reading paths and claim boundaries.
- [`CONTENTS.md`](CONTENTS.md) — canonical repository inventory.
- [`TESTABLE-HYPOTHESES.md`](TESTABLE-HYPOTHESES.md) — experimental protocols and proposed negative controls.
- [`FUTURE-DIRECTIONS.md`](FUTURE-DIRECTIONS.md) — longer-term research agenda.
- [`OPEN-QUESTIONS.md`](OPEN-QUESTIONS.md) — research questions and opportunities for external challenge.
