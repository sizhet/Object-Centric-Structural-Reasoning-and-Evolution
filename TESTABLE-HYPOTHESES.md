# TESTABLE-HYPOTHESES — OCSRE Falsifiable Research Protocols

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Version:** v1.0.0 — Research Framework and Contracts  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**License:** Apache-2.0  
**Canonical location:** `TESTABLE-HYPOTHESES.md`  
**Research status:** Protocol proposals only. All OCSH-001–011 remain **E0 — Proposed**; no execution, formal proof, replication, or scaling law is claimed.

## 1. Purpose and relationship to the research registry

This document translates the eleven canonical hypotheses in [`research-trace/HYPOTHESIS-REGISTRY.md`](research-trace/HYPOTHESIS-REGISTRY.md) into **testable research protocols**. The registry is the source of truth for hypothesis identity, current status, and evidence history; this file defines proposed experiment designs, pre-registration fields, comparison conditions, metrics, negative controls, and decision rules. Neither a worked example nor a manuscript constitutes a result. Future experimental changes must be logged, versioned, and reviewed before execution.

The central research thesis is that a typed WE/Object substrate can coordinate formal reasoning, an Object Differential Kernel (ODK), domain Object Plugins, in-situ learning, WE-native Constrained Delta Evolution (CDE), SIF Localization, and UIERU-style capability relay **without collapsing their distinct semantics**. A study must distinguish logical correctness, semantic conformance, empirical utility, security, authorization, and long-horizon growth.

### 1.1 Canonical study identifiers

| Study | Primary OCSH | Primary research surface | Principal comparator |
|---|---|---|---|
| STUDY-LOGIC-01 | 001, 006 | CASE-001; SPEC-003 | Reference logic engine; no-granularity-contract ablation |
| STUDY-ODK-01 | 002, 003 | CASE-002/003/004/005; SPEC-002/004 | Bespoke comparators and integrations |
| STUDY-FEEDBACK-01 | 004 | OCSRE-007; SPEC-005 | Conventional logs / static feedback pipeline |
| STUDY-CDE-01 | 005, 006 | CASE-003/004/006; SPEC-006 | Domain-specific state transition/search |
| STUDY-SQL-01 | 007 | CASE-002; OCSRE-006 | Native SQL oracle and native security policy |
| STUDY-RELAY-01 | 003, 008 | CASE-005; EXT-003 | No relay; informal handoff |
| STUDY-SPILLOVER-01 | 009 | EXT-005 | Frozen pre-capability system, budget-matched alternatives |
| STUDY-GROWTH-01 | 010 | EXT-003/004/005 | Fixed catalog; manual-only evolution |
| STUDY-CODE-01 | 011 | CASE-006; OCSRE-010 | Standard CI/review; Calling Graph only |

**Terminology:** OCSH identifies a hypothesis; STUDY identifies an experiment family; `THT-###` below identifies a proposed protocol obligation. None are evidence identifiers.

## 2. Evidence hierarchy and claim boundaries

- **E0 — Proposed:** falsifiable claim and suggested design; current state for every OCSH.
- **E1 — Specified:** frozen, independently reviewed protocol, fixtures, metrics, baselines, and acceptance thresholds; not yet a successful test.
- **E2 — Tested:** actual execution, retained artifacts, failures, and reproducible environment.
- **E3 — Replicated:** independent repetition across relevant conditions.
- **E4 — Qualified support:** bounded conclusion supported by multiple rigorous studies with uncertainty and limitations.
- **EX — Refuted/restricted; EH — On hold:** documented contrary evidence, scope narrowing, or blockers.

A valid deductive proof does not demonstrate true premises; passing conformance does not prove improved task utility; improved task utility does not prove safe authorization; successful relay does not establish untargeted spillover; finite-horizon growth does not establish an asymptotic Scaling Law.

## 3. Mandatory pre-registration and reporting contract

Every study MUST specify before accessing test outcomes: hypothesis/version; target population of tasks; inclusion/exclusion rules; source and target domains; frozen code and adapter hashes; test fixture provenance; train/development/held-out partition and chronological cutoff; control conditions; resource budget (compute, human effort, token usage, wall time); primary and secondary metrics; uncertainty calculation; failure/abstention criteria; negative controls; randomization and seed strategy; independent reviewer; security/permission model; stop criteria; and publication of unsuccessful attempts. Mark unknown fields `TBD` rather than filling them with invented measurements.

**Suggested statistical rule (to be pre-registered, not assumed):** for a comparative utility hypothesis, require a positive primary effect with a confidence interval excluding zero **and** a predeclared minimum practical effect, without unacceptable safety regressions. Report exact effect sizes, uncertainty, all tasks, and multiple-comparison treatment. For a safety-critical semantic invariant, a single confirmed contract-compliant counterexample can defeat the scoped invariant even when average performance is high. Do not turn this suggested rule into a post-hoc success criterion.

### 3.1 Common outcome record

```yaml
study_id: STUDY-SQL-01
hypothesis_ids: [OCSH-007]
protocol_version: TBD
preregistration_uri: TBD
fixture_manifest_uri: TBD
code_and_adapter_hashes: TBD
baseline_version: TBD
holdout_manifest: TBD
budget_manifest: TBD
primary_metric: TBD
minimum_practical_effect: TBD
uncertainty_method: TBD
negative_control_ids: []
executed_at: null
result_artifact_ids: []
failed_case_ids: []
security_incidents: []
independent_reviewer: TBD
status: E0
interpretation: not_evaluated
leftovers: []
```

The result record must distinguish `not_executed`, `rejected_as_invalid`, `failed_to_execute`, `executed_and_failed`, `executed_and_passed`, and `inconclusive`. A rejected invalid input is **positive conformance evidence**, not a failed test.

## 4. OCSH-001 — Restricted classical deductive preservation

**Claim.** A specified OCSRE fragment preserves classical deductive validity. **Scope:** explicit first-order or narrower typed fragment, with fixed interpretation of quantifiers, identity, predicates, and entailment. **Independent variable:** object-centric translation versus reference representation. **Primary outcome:** soundness of entailment preservation; completeness only if separately claimed and scoped. **Oracle:** independently implemented reference prover/model checker.

**Protocol.** Freeze a grammar and translation mapping. Generate valid and invalid premise/conclusion pairs; include `∀x(Human(x) → Mortal(x))`, `Human(s)` entails `Mortal(s)` as a positive example, and invalid converse/affirming-consequent cases as negative examples. Compare proof witnesses and countermodels. Include identity aliases, empty classes, quantifier scope, inconsistent-premise policy, changing temporal facts, and unauthorized Person→Group lifting. Run independent implementation checks and preserve all mismatches.

**Disconfirmation:** any counterexample to the claimed translation property inside the declared fragment. **Not established:** natural-language correctness, factual truth of premises, defeasible reasoning, or unrestricted logic. **Sources:** [OCSRE-002](docs/OCSRE-002-From-Classical-Syllogism-to-Object-Centric-Structural-Reasoning.md), [SPEC-003](specs/SPEC-003-Classical-Reasoning-Preservation-and-Granularity-Contract.md), [CASE-001](cases/CASE-001-Person-and-Classical-Reasoning.md), [EXT-001](extensions/EXT-001-Object-Centric-Reasoning-and-the-History-of-Logic.md).

## 5. OCSH-002 — Cross-domain ODK kernel invariance

**Claim.** A common ODK can be reused across domains without modifying the kernel. **Independent variable:** frozen generic ODK plus adapters versus separate domain comparators. **Primary outcomes:** unchanged kernel hash and semantic conformance rate; secondary outcomes: defect rate, latency, adaptation effort. **Domains:** at least three genuinely distinct typed metric settings (e.g., bus capacity, inventory utilization, transaction evidence), chosen before results are known.

**Protocol.** Freeze ODK binary and interface; register metric units, direction, granularity, time, perspective, missingness and normalization in adapters. Apply `Object[metricIndices]` comparisons and differential operators to both compatible and incompatible inputs. Test percentage-point versus absolute-count confusion, invalid cross-perspective comparisons, null inputs, correlated evidence, and invalid aggregations. Independently audit adapters for hidden reimplementation of the kernel.

**Disconfirmation:** required kernel modifications, semantically wrong comparisons despite contract-compliant adapters, or an implementation whose apparent reuse is merely displaced domain logic. **Boundary:** kernel reuse does not prove universal metric equivalence. **Sources:** [OCSRE-004](docs/OCSRE-004-Object-Differential-Kernel-and-Generic-Operators.md), [SPEC-002](specs/SPEC-002-Object-Differential-Kernel-and-Comparator-Contract.md), [CASE-005](cases/CASE-005-Cross-Domain-Object-Plugin-Relay.md).

## 6. OCSH-003 — Contract-based Object Plugins reduce adaptation costs

**Claim.** Contracted Object Plugins reduce net domain adaptation effort or errors. **Conditions:** contract-based integration, bespoke implementation, and optionally informal plugin reuse. **Primary metric:** total person-hours per accepted target task, including adapter creation, validation, debugging and maintenance; **secondary:** changed lines, defect incidence, latency and ongoing upkeep.

**Protocol.** Preselect comparable tasks; randomize or counterbalance team/task order; hold tools, experience, task scope, and validation budget comparable. Count unsuccessful attempts and plugin authoring overhead. Require identical target acceptance criteria and security gates. Measure costs over a defined maintenance interval rather than stopping at first successful demo.

**Disconfirmation:** no practically meaningful net saving, increased defects, or security regressions. **Boundary:** a plugin invocation is not a successful transfer. **Sources:** [OCSRE-005](docs/OCSRE-005-Object-Plugins-and-Composable-Intelligence-Capabilities.md), [SPEC-004](specs/SPEC-004-Object-Plugin-and-Capability-Composition-Contract.md), [CASE-005](cases/CASE-005-Cross-Domain-Object-Plugin-Relay.md).

## 7. OCSH-004 — In-situ learning improves feedback use or traceability

**Claim.** Object-linked learning improves feedback integration and/or provenance reconstruction. **Comparator:** conventional event log or static feedback update using identical data. **Primary metrics:** provenance reconstruction accuracy and stale-evidence error rate; secondary: feedback incorporation latency, downstream task accuracy, and unauthorized belief promotion.

**Protocol.** Create time-versioned observations, corrections, conflicting witnesses, revoked sources, perspective shifts and feedback loops. Assign reviewers blinded to condition to reconstruct why a state or inference changed. Separate the ability to *trace* a decision from its correctness. Record rejected updates, replay integrity and rollback.

**Disconfirmation:** no audit improvement, systematic misattribution, or increased unsafe state changes. **Sources:** [OCSRE-007](docs/OCSRE-007-In-Situ-Object-Learning-Decision-and-Feedback.md), [SPEC-005](specs/SPEC-005-In-Situ-Learning-Feedback-and-Epistemic-Governance-Contract.md), [CASE-004](cases/CASE-004-Transaction-and-Compositional-Identity.md).

## 8. OCSH-005 — WE-native CDE supports single and composite transitions

**Claim.** Shared typed-delta contracts govern both individual and composite WE state changes. **Primary metrics:** global-invariant violations, valid-state reachability, rollback correctness and unauthorized-commit incidence; secondary: search coverage and cost. **Comparator:** conventional application-specific search/constraint solver with matched objectives and feasibility rules.

**Protocol.** Freeze state schema and invariant set. In CASE-003, test trip reassignment, duty merging, time windows, bus capacity, driver rules and rollback; in CASE-004, test candidate identity-hypothesis splits/merges without promoting conjecture to fact; in CASE-006, test code changes under deployment constraints. Exercise repeated Delta prohibition, path memory, NoSubtree, loop-back termination and concurrent composite updates. Validate the *whole* state after every candidate, not only the changed node.

**Disconfirmation:** a contract-compliant transition that passes verification but violates a declared invariant, or rollback that cannot restore the required state. **Boundary:** feasible ≠ optimal; evaluated ≠ authorized; ODK differential ≠ CDE typed delta. **Sources:** [OCSRE-008](docs/OCSRE-008-WE-Native-CDE-and-Composite-State-Evolution.md), [SPEC-006](specs/SPEC-006-WE-Native-CDE-Composite-State-and-Relay-Contract.md), [CASE-003](cases/CASE-003-School-Bus-Scheduling-and-Composite-WE-State.md).

## 9. OCSH-006 — Granularity contracts reduce invalid inference

**Claim.** Explicit granularity contracts reduce invalid property inheritance and aggregation. **Conditions:** identical reasoner with and without granularity checking. **Primary metric:** false-inference rate on predeclared adversarial examples; secondary: true-inference retention, abstention calibration and annotation cost.

**Protocol.** Construct Person↔Group, Student↔Trip↔Fleet, Wallet↔Actor Cluster, and Row↔Aggregate cases. Include ecological fallacies, composition fallacies, incompatible denominators, conflicting time windows, universal versus existential claims and aggregate-only evidence. Score false acceptance and excessive rejection separately.

**Disconfirmation:** no error reduction or a prohibitive drop in legitimate inference coverage. **Sources:** [OCSRE-003](docs/OCSRE-003-Dynamic-Relational-and-Multi-Granular-Reasoning.md), [SPEC-001](specs/SPEC-001-Object-Identity-Perspective-and-State-Contract.md), [SPEC-003](specs/SPEC-003-Classical-Reasoning-Preservation-and-Granularity-Contract.md).

## 10. OCSH-007 — SQL-to-WE semantics and security

**Claim.** Declared SQL-to-WE transformations preserve specified query semantics and access boundaries while enabling object capability reuse. **Oracle:** native SQL engine under the same schema, dialect, snapshot, isolation level and authorization policy. **Primary metrics:** exact semantic mismatch count for supported transformations and unauthorized disclosure count; secondary: performance and reuse cost.

**Protocol.** Freeze SQL fixtures and compare Bucketize, Normalize, Combine, Encode and Derive results against independent SQL queries. Test `NULL` and three-valued logic, join multiplicity, duplicate rows, grouping keys, aggregation grain, timezone and snapshot mismatch, schema evolution, and row-level security. Use negative tests where the correct result is a rejection, not a value. Audit tenant boundaries at source and output.

**Disconfirmation:** any supported, contract-compliant semantic mismatch or unauthorized disclosure. **Boundary:** this does not imply preservation of every SQL dialect or arbitrary query. **Sources:** [OCSRE-006](docs/OCSRE-006-SQL-to-Object-Attribute-Transformation-and-Semantic-Alignment.md), [CASE-002](cases/CASE-002-SQL-Native-Object-Adaptation.md), [SPEC-004](specs/SPEC-004-Object-Plugin-and-Capability-Composition-Contract.md).

## 11. OCSH-008 — Validated cross-domain capability relay

**Claim.** Contract-governed relay yields measurable target-domain benefit. **Conditions:** no relay, informal handoff, and validated relay. **Primary metric:** target-task success net of adaptation/verification cost; secondary: security regressions, acceptance rate and maintenance burden.

**Protocol.** Freeze source capability, target task and acceptance tests before transfer. Use CASE-005 Track A (SQL capacity → inventory), Track B (school-bus scheduling → equipment allocation), and Track C (transaction evidence governance → code impact analysis). Require independent target-domain review and record *every* attempted transfer, including failures. Validate target semantics and authorization rather than treating shared schema as proof of equivalence.

**Disconfirmation:** no net gain, systematic semantic breakage, or prohibitive validation overhead. **Boundary:** successful planned transfer is not untargeted spillover. **Sources:** [OCSRE-011](docs/OCSRE-011-Structural-Capability-Spillover-and-Relay.md), [CASE-005](cases/CASE-005-Cross-Domain-Object-Plugin-Relay.md), [EXT-003](extensions/EXT-003-Multi-Agent-Object-Intelligence-and-Relay.md).

## 12. OCSH-009 — Untargeted-task structural spillover

**Claim.** A new capability yields measurable gains on tasks not selected to motivate its design. **Primary metric:** independently verified, resource-adjusted performance change on prospectively held-out tasks; secondary: novelty audit, leakage rate and adaptation cost.

**Protocol.** Before capability construction, freeze a broad task pool and a concealed holdout; timestamp capability versions and developer access. After construction, independently evaluate held-out tasks under a fixed budget against a pre-capability snapshot and resource-matched alternatives. Report all evaluated tasks, not only striking successes. Test whether gains persist after excluding tasks semantically adjacent to training or design examples.

**Disconfirmation:** gains vanish after leakage controls, failed-transfer inclusion, or resource matching. **Boundary:** a post-hoc anecdote is not prospective spillover. **Sources:** [EXT-005](extensions/EXT-005-Structural-Capability-Spillover-and-Scaling-Hypotheses.md), [OCSRE-012](docs/OCSRE-012-Open-Ended-Object-Centric-Structural-Intelligence.md).

## 13. OCSH-010 — Sustained validated capability and question growth

**Claim.** Governed evolution repeatedly yields useful, nonredundant capabilities or testable questions with retained net value over a specified finite horizon. **Primary metric:** independently validated, retained capability yield per total resource unit per round; secondary: novel testable-question yield, regressions, retirement rate, and security incidents.

**Protocol.** Pre-register the number and duration of rounds, frozen task pools, discovery budgets, independent review and retirement rules. Compare OCSRE Metric/Plugin/Policy evolution against a fixed capability catalog, manual-only extension and budget-matched generic search. Track whether a new capability actually changes held-out outcomes and survives later regression tests. Require human-governed authorization for policy changes; prohibit self-awarded privileges.

**Disconfirmation:** net-value plateau, accumulating maintenance debt, repeated rediscovery, task contamination, or unsafe self-authorization. **Boundary:** finite-horizon sustained gains do not establish an unbounded or asymptotic scaling law. **Sources:** [EXT-004](extensions/EXT-004-Open-Ended-Metric-Plugin-and-Policy-Evolution.md), [EXT-005](extensions/EXT-005-Structural-Capability-Spillover-and-Scaling-Hypotheses.md).

## 14. OCSH-011 — AI-generated code governance

**Claim.** Object-centric, multi-graph code governance improves change-impact localization, validation targeting or traceability. **Conditions:** standard CI/review, Calling Graph-only, and Calling Graph → UTN → OCSRE with data/control/configuration/schema/security/test/deployment relations. **Primary metrics:** recall of safety-critical affected components and missed security dependencies; secondary: precision, test selection efficiency, reviewer effort and latency.

**Protocol.** Freeze multi-project code fixtures and inject changes that affect authorization caches, tenant isolation, dynamic dispatch, configuration and schema dependencies. Include a case with **unchanged Calling Graph but changed program semantics**. Evaluate whether proposed CDE code deltas are rejected when they violate declared invariants, even when tests pass. Keep approval, merge and deployment permissions separate from candidate scoring.

**Disconfirmation:** no material impact recall improvement, missed critical security edges, or unacceptable operational overhead. **Boundary:** improved localization does not prove complete program correctness or permission to deploy. **Sources:** [OCSRE-010](docs/OCSRE-010-AI-Generated-Code-Governance-Through-Calling-Graphs-and-UTN.md), [CASE-006](cases/CASE-006-AI-Generated-Code-Governance-Through-Calling-Graphs-and-CDE.md), [EXT-002](extensions/EXT-002-Object-Centric-SIF-Localization-and-Addressing.md).

## 15. Shared ablation and negative-control matrix

| Ablation / control | Purpose | Relevant hypotheses |
|---|---|---|
| Remove Object identity typing | Detect accidental label-based identity collapse | 001, 006, 007 |
| Remove perspective/time checks | Detect invalid metric comparisons and stale inference | 002, 004, 006 |
| Remove granularity checks | Measure false inheritance versus valid retention | 001, 006 |
| Replace ODK with bespoke comparators | Test kernel reuse versus domain specialization | 002, 003 |
| Remove plugin contracts | Expose hidden semantic adaptation costs | 003, 008 |
| Remove provenance ledger | Quantify audit and attribution dependence | 004, 011 |
| Verify local delta only | Detect global composite-state constraint failures | 005 |
| Bypass SQL NULL/row-security handling | Detect semantic and privacy failures | 007 |
| Allow informal agent handoff | Test relay governance and negative transfer | 008 |
| Select tasks after observing outcomes | Detect selection bias in spillover claims | 009 |
| Count raw plugins without retirement/cost | Detect artificial growth | 010 |
| Use Calling Graph alone | Detect missing semantic/security dependencies | 011 |

Ablations must remain within an approved sandbox and must never be used to bypass real-world access control or deployment safeguards.

## 16. Conformance obligations — proposed protocol checks

The following are **protocol-design obligations**, not executed test results:

| ID | Obligation | Expected disposition |
|---|---|---|
| THT-001 | Every study maps to a stable OCSH identifier | Required |
| THT-002 | Hypothesis wording and scope frozen before test | Required |
| THT-003 | Primary metric declared before outcomes observed | Required |
| THT-004 | Baseline matched for task and resources | Required |
| THT-005 | Negative and adversarial fixtures predeclared | Required |
| THT-006 | Object identity distinguished from labels and keys | Required where relevant |
| THT-007 | Metric unit, direction, time, perspective typed | Required where relevant |
| THT-008 | ODK code hash unchanged in invariance study | Required for OCSH-002 |
| THT-009 | Plugin adaptation costs include validation and failures | Required for OCSH-003/008 |
| THT-010 | Feedback provenance and stale evidence tested | Required for OCSH-004 |
| THT-011 | Composite-state global invariants checked | Required for OCSH-005 |
| THT-012 | Granularity false positives and false negatives measured | Required for OCSH-006 |
| THT-013 | SQL oracle uses matched snapshot/security context | Required for OCSH-007 |
| THT-014 | Relay acceptance independently reviewed | Required for OCSH-008 |
| THT-015 | Untargeted tasks frozen prospectively | Required for OCSH-009 |
| THT-016 | Growth tracks retirement, regression and total costs | Required for OCSH-010 |
| THT-017 | Code governance tests non-call-graph dependencies | Required for OCSH-011 |
| THT-018 | Unauthorized actions cannot be auto-promoted | Required across governed studies |
| THT-019 | All attempted trials and failed transfers recorded | Required |
| THT-020 | Uncertainty, missing data and limitations reported | Required |
| THT-021 | Independent reviewer and artifact hashes retained | Required for evidence upgrade |
| THT-022 | Negative evidence can trigger EX/EH and scope revision | Required |
| THT-023 | Cross-hypothesis inference boundaries enforced | Required |
| THT-024 | Explicit leftovers remain visible after publication | Required |

## 17. Positive reference tests and adversarial tests

### 17.1 Positive reference tests (design only)

| Test ID | Stimulus | Expected outcome |
|---|---|---|
| TH-POS-001 | Valid Socrates-style deduction in declared fragment | Preserved entailment with proof trace |
| TH-POS-002 | Typed same-unit ODK comparison | Correct differential and provenance |
| TH-POS-003 | Valid plugin adapter under frozen kernel | Contract passes without kernel edits |
| TH-POS-004 | Corrected observation with versioned provenance | Traceable supersession without history erasure |
| TH-POS-005 | Feasible bus duty merge under all declared constraints | Candidate eligible for review, not auto-deployed |
| TH-POS-006 | Valid group aggregation with explicit denominator | Correct scoped aggregate inference |
| TH-POS-007 | SQL transformation under fixed snapshot and permissions | Oracle-equivalent authorized result |
| TH-POS-008 | Validated source capability transferred to target | Target conformance and utility evaluated |
| TH-POS-009 | Truly unseen held-out task | Blind, resource-matched measurement |
| TH-POS-010 | New metric/plugin improves retained task utility | Independently verified and regression-tested |
| TH-POS-011 | Security-relevant code dependency captured outside call graph | Impact surfaced and routed to review |
| TH-POS-012 | Failed transfer with documented counterexample | Failure retained in research ledger |

### 17.2 Negative and adversarial tests (design only)

| Test ID | Adversarial condition | Required safe outcome |
|---|---|---|
| TH-NEG-001 | Invalid converse inference | Reject entailment |
| TH-NEG-002 | Object label collision | Do not merge identities |
| TH-NEG-003 | Person→Group inheritance without bridge rule | Reject or qualify |
| TH-NEG-004 | Incompatible metric units | Reject comparison |
| TH-NEG-005 | Incompatible perspectives | Reject or require explicit conversion |
| TH-NEG-006 | Stale evidence applied to new state | Invalidate or qualify |
| TH-NEG-007 | Missing metric coerced to zero | Reject silent coercion |
| TH-NEG-008 | Domain-specific logic hidden in supposedly invariant kernel | Flag protocol violation |
| TH-NEG-009 | Plugin with undeclared permission escalation | Deny integration |
| TH-NEG-010 | Correlated weak evidence double counted | Prevent unsupported confidence promotion |
| TH-NEG-011 | Composite delta passes local check but breaks fleet invariant | Reject candidate |
| TH-NEG-012 | Repeated forbidden delta or uncontrolled loop-back | Enforce path/termination rules |
| TH-NEG-013 | Infeasible candidate assigned highest score | Reject regardless of score |
| TH-NEG-014 | SQL `NULL` interpreted as ordinary false/zero | Flag semantic mismatch |
| TH-NEG-015 | Join duplicates silently removed | Flag multiplicity mismatch |
| TH-NEG-016 | Cross-tenant row disclosure | Block and record security failure |
| TH-NEG-017 | Target plugin with incompatible metric meaning | Reject relay |
| TH-NEG-018 | Agent consensus without independent evidence | No automatic promotion |
| TH-NEG-019 | Post-hoc selected “untargeted” tasks | Exclude from OCSH-009 evidence |
| TH-NEG-020 | Holdout contamination | Invalidate affected spillover estimate |
| TH-NEG-021 | Plugin count grows while net retained utility falls | No scaling claim |
| TH-NEG-022 | Proposed policy relaxes its own authorization gate | Reject self-authorization |
| TH-NEG-023 | Unchanged Calling Graph, altered tenant cache semantics | Flag via semantic/security dependencies |
| TH-NEG-024 | Passing CI but missing deployment approval | Do not deploy |

## 18. Decision rules, contradictions, and negative evidence

A hypothesis must be evaluated against its **own** scope and primary outcome. The following transitions are prohibited without separate evidence: valid ODK comparisons → plugin cost reduction; plugin cost reduction → relay utility; planned relay utility → untargeted spillover; spillover → sustained growth; finite growth → Scaling Law; validated code change → authorized deployment. When a counterexample appears, preserve the original claim and evidence, open an entry in [`research-trace/COUNTEREXAMPLE-REGISTRY.md`](research-trace/COUNTEREXAMPLE-REGISTRY.md), and log any narrowed claim in [`research-trace/DECISION-LOG.md`](research-trace/DECISION-LOG.md).

Independent replication must rerun an identifiable protocol with separate investigators or environments and retain negative outcomes. An inconclusive study must not be described as supporting or refuting the hypothesis. Security-sensitive failures warrant immediate review irrespective of statistical significance.

## 19. Suggested minimal execution order

**Stage A — Semantics:** define reference objects, metric types, identity and granularity rules; complete STUDY-LOGIC-01 and STUDY-SQL-01 specifications. **Stage B — Reusable computation:** freeze an ODK and run STUDY-ODK-01 with explicit adapter costs. **Stage C — Governed state:** add STUDY-FEEDBACK-01 and STUDY-CDE-01 with rollback and global invariants. **Stage D — Relay and governance:** run STUDY-RELAY-01 and STUDY-CODE-01 under independent review. **Stage E — Longitudinal growth:** only after prior stages, preregister STUDY-SPILLOVER-01 and STUDY-GROWTH-01 with genuine holdouts and full cost accounting.

The stages express methodological dependencies, not a committed calendar. Results may require changing or abandoning the architecture.

## 20. Cross-reference map

| Research asset | Role |
|---|---|
| [`research-trace/HYPOTHESIS-REGISTRY.md`](research-trace/HYPOTHESIS-REGISTRY.md) | Canonical OCSH wording, evidence status and study portfolio |
| [`research-trace/DEFINITION-REGISTRY.md`](research-trace/DEFINITION-REGISTRY.md) | Stable semantic definitions and distinctions |
| [`research-trace/COUNTEREXAMPLE-REGISTRY.md`](research-trace/COUNTEREXAMPLE-REGISTRY.md) | Adversarial cases and confirmed/rejected counterexamples |
| [`research-trace/DECISION-LOG.md`](research-trace/DECISION-LOG.md) | Scope and architecture decision history |
| [`research-trace/UNRESOLVED-RESIDUALS.md`](research-trace/UNRESOLVED-RESIDUALS.md) | Operational blockers and closure criteria |
| [`VALIDATION-ROADMAP.md`](VALIDATION-ROADMAP.md) | Execution sequence and evidence promotion gates |
| [`OPEN-QUESTIONS.md`](OPEN-QUESTIONS.md) | Reader-facing open research questions |
| [`FUTURE-DIRECTIONS.md`](FUTURE-DIRECTIONS.md) | Long-term research agenda |

## 21. Explicit leftovers — THT-L001 through THT-L024

These items remain unresolved; they must not be silently treated as satisfied:

1. **THT-L001:** Choose the precise classical logic fragment and reference semantics.
2. **THT-L002:** Formalize translation soundness, and completeness only if claimed.
3. **THT-L003:** Define identity aliasing, splitting and merging rules.
4. **THT-L004:** Finalize typed metric algebra and missingness semantics.
5. **THT-L005:** Select independent domains that genuinely stress ODK invariance.
6. **THT-L006:** Specify how hidden domain-specific adapter work is audited.
7. **THT-L007:** Calibrate plugin development and maintenance cost measurement.
8. **THT-L008:** Select robust audit-trace reconstruction metrics.
9. **THT-L009:** Define conflicting-evidence and stale-evidence adjudication.
10. **THT-L010:** Formalize CDE global invariants and rollback under concurrency.
11. **THT-L011:** Establish path-memory, repeated-delta and loop-back semantics.
12. **THT-L012:** Choose granularity benchmark coverage and valid-inference retention criteria.
13. **THT-L013:** Specify SQL dialects, isolation levels and supported query subset.
14. **THT-L014:** Validate SQL security against real policy implementations in a safe test environment.
15. **THT-L015:** Freeze target-domain task and transfer acceptance manifests.
16. **THT-L016:** Define a leakage-resistant prospective untargeted-task holdout.
17. **THT-L017:** Quantify transfer failures and negative transfer consistently.
18. **THT-L018:** Establish long-horizon capability usefulness and retirement rules.
19. **THT-L019:** Specify operational meaning of novel, testable question yield.
20. **THT-L020:** Define resource normalization across agents, models and human reviewers.
21. **THT-L021:** Build representative code-governance security dependency fixtures.
22. **THT-L022:** Define independent review and replication eligibility.
23. **THT-L023:** Preregister practical effect thresholds and multiplicity handling.
24. **THT-L024:** Build a durable public evidence ledger without disclosing sensitive data.

## 22. Publication and scientific restraint

The initial v1.0.0 contribution is a **testable architecture and research contract portfolio**, not a proven universal reasoning engine, autonomous AGI, validated Scaling Law, or certified code-security system. Future releases should report executed tests, contrary evidence, changed assumptions, and explicit residuals. Scientific value includes discovering where object-centric unification fails, where domain-specific methods outperform it, and which proposed structural interfaces survive independent scrutiny.

**Governing principle:** *Specifications/Contracts First · Conformance Before Runtime · Explicit Leftover · Independent Evidence Before Claim Promotion.*
