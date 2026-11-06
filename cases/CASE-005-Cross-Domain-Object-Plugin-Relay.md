# CASE-005 — Cross-Domain Object Plugin Relay

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Release target:** v1.0.0 — Research Framework and Contracts  
**Document type:** Research case and proposed conformance protocol  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**Status:** Proposed / E0; synthetic examples and test designs, not completed empirical validation  
**License:** Apache-2.0

## Abstract

This case examines a central claim of Object-Centric Structural Reasoning and Evolution (OCSRE): a capability developed around one World Entity (WE) domain can be transferred to a different domain through a stable Object Differential Kernel (ODK), typed Object Plugins, explicit semantic adapters, and receiving-domain conformance gates. The target is not superficial reuse of source code. It is **validated structural capability relay**, in which semantics, authority, provenance, evidence qualification, and measured utility survive transfer. We construct three synthetic relay tracks: SQL-based school-transport capacity analysis to inventory utilization analysis; composite-state school-bus scheduling to a constrained resource-assignment problem; and transaction-graph hypothesis analysis to software dependency-impact triage. Each track distinguishes genuinely reusable mechanisms from domain-specific assumptions that must be replaced. We specify transfer envelopes, positive and adversarial tests, baselines, measurement criteria, and promotion gates. The cases are proposals for reproducible experiments, not evidence that cross-domain transfer has already succeeded. The principal hypotheses are OCSH-002, OCSH-003, and OCSH-008; untargeted spillover and sustained scaling (OCSH-009 and OCSH-010) require separate experiments.

## 1. Research question and claim boundary

**Question:** Under what explicit contracts can an Object Plugin or composed capability move from a source domain to a receiving domain without silently changing meaning, widening authority, or weakening validation?

The proposed thesis is conditional: **shared object interfaces may reduce the work required to transfer certain structural operations, provided that the receiving domain supplies its own valid identity, metric, relation, constraint, and policy bindings.** Neither shared syntax nor passing source-domain tests establishes receiving-domain validity.

This case does **not** assert that (a) every domain admits a common metric, (b) a graph in one domain has the same causal meaning as a graph in another, (c) a successful plugin invocation proves useful intelligence, or (d) capability accumulation follows a demonstrated scaling law.

## 2. Research lineage and normative dependencies

This case operationalizes:

- `docs/OCSRE-004-Object-Differential-Kernel-and-Generic-Operators.md`: Resolve → Project → Align → Evaluate → Qualify → Trace.
- `docs/OCSRE-005-Object-Plugins-and-Composable-Intelligence-Capabilities.md`: typed plugin interfaces and capability composition.
- `docs/OCSRE-006-SQL-to-Object-Attribute-Transformation-and-Semantic-Alignment.md`: SQL-to-WE semantic transformations.
- `docs/OCSRE-008-WE-Native-CDE-and-Composite-State-Evolution.md`: candidate-state evolution and composite constraints.
- `docs/OCSRE-009-Epistemic-Separation-and-Object-Centric-Evidence-Governance.md`: evidence versus inference versus authorization.
- `docs/OCSRE-010-UTN-WE-HDT-and-SIF-Localization-Through-Shared-Object-Interfaces.md`: localization is not identity or authority.
- `docs/OCSRE-011-Object-Capability-Spillover-Relay-and-Collective-Structural-Learning.md`: capability relay, transfer measurement, and independent target validation.
- `specs/SPEC-001-Object-Identity-Perspective-and-State-Contract.md` through `specs/SPEC-006-WE-Native-CDE-Composite-State-and-Relay-Contract.md`: identity, comparator, inference, plugin, learning, and evolution contracts.

Relevant case fixtures are `cases/CASE-002-SQL-Native-Object-Adaptation.md`, `cases/CASE-003-School-Bus-Scheduling-and-Composite-WE-State.md`, and `cases/CASE-004-Transaction-and-Compositional-Identity.md`. `cases/CASE-006-AI-Generated-Code-Governance-Through-Calling-Graphs-and-CDE.md` is the intended deeper code-governance follow-up. These links describe repository paths, not completed implementation dependencies.

## 3. Terms and separation of concerns

**Object / WE:** a domain-grounded entity with explicit identity, type, state, temporal scope, and applicable perspectives. A source database row, network address, or graph node is not automatically a WE identity.

**Object Plugin:** a versioned capability implementation or specification with typed inputs and outputs, preconditions, postconditions, effects, provenance requirements, and authority limits.

**Relay candidate:** a capability and its transfer package proposed for another context, before receiving-domain validation.

**Validated relay:** a transfer for which receiving-domain conformance, target-specific performance, negative tests, and costs have been recorded and passed against declared acceptance criteria.

**Spillover:** a measurable benefit on an additional task or domain beyond the original design target. It is not synonymous with successful invocation or code reuse.

**Explicit leftover:** an unresolved semantic, empirical, engineering, or governance issue recorded without being treated as resolved.

The ODK is a reusable execution discipline, not a universal ontology. Object Plugins carry domain-specific interpretation. SIF localization, UTN/MDT/WE-HDT addressing, UIERU relay, MLIU learning, and ISGFTR spillover hypotheses may consume the interface without being declared algorithmically equivalent.

## 4. Reference relay package

A proposed minimal relay envelope is:

```yaml
relay_id: RELAY-CASE005-EXAMPLE-001
source:
  domain: school_transport
  capability_id: typed-utilization-bucket
  capability_version: 0.1.0
  artifact_digest: REQUIRED_AT_EXECUTION
receiving:
  domain: inventory
  adapter_id: inventory-utilization-adapter
  adapter_version: 0.1.0
object_contract:
  identity_binding: receiving_domain_resolver
  state_version: REQUIRED
  perspective: operational_capacity
  temporal_scope: declared_snapshot
  metric_schema: ratio_dimensionless
semantic_contract:
  source_meaning: assigned_load / available_capacity
  target_meaning: reserved_units / usable_capacity
  null_policy: reject_or_qualify
  zero_denominator_policy: reject
  aggregation_grain: per_resource_per_snapshot
  bucket_policy_version: v1
  evidence_class: derived_measurement
permissions:
  effective_scope: intersection_of_source_target_and_invoker
  side_effect_class: pure
validation:
  target_conformance: required
  target_negative_tests: required
  held_out_evaluation: required_for_transfer_claim
  source_success_is_insufficient: true
promotion:
  status: proposed
  independent_review: required
```

This YAML is an **illustrative schema sketch**, not a registered wire format or an executable conformance certificate. A real implementation must bind hashes, identities, authority, and versions to actual artifacts. A relay package also needs source tests, receiving-domain reference answers, a trial ledger, and a rollback or revocation plan for deployed capabilities.

## 5. Relay lifecycle and decision gates

A proposed lifecycle is:

1. **Discover:** identify a source capability and the exact semantic operation it performs.
2. **Decompose:** separate reusable operator, source-domain assumptions, and hidden dependencies.
3. **Bind:** attach receiving-domain WE identities, types, metric semantics, perspective, time, and authority.
4. **Adapt:** implement only explicit, versioned semantic adapters; do not silently alter the kernel.
5. **Conform:** run SPEC-001–SPEC-006 checks relevant to the transfer.
6. **Challenge:** run negative, adversarial, and cross-granularity tests, including permission failures.
7. **Evaluate:** compare against a receiving-domain baseline on held-out fixtures; include integration and validation cost.
8. **Review:** independently inspect the evidence, conflicts, and residuals.
9. **Promote or reject:** record an explicit decision. Promotion of a plugin is not authorization for its external actions.
10. **Monitor and relay:** track drift, regression, negative transfer, and possible future reuse.

Any P0 semantic, security, epistemic, or evolution-safety failure blocks promotion. An indeterminate result remains indeterminate; it is not counted as success.

## 6. Track A — SQL capacity analysis to inventory utilization

### 6.1 Source and target objects

Source objects are school-bus trip assignments with `planned_passengers` and `rated_seats` at a defined assignment snapshot. Target objects are inventory storage bins with `reserved_units` and `usable_capacity_units` at a defined inventory snapshot. Their identities, data owners, and operational meanings differ. A row key or assignment identifier must not be copied into the receiving WE identity namespace.

A potentially reusable **pure operator** is:

\[
U(o,t,p)=\frac{\operatorname{Load}(o,t,p)}{\operatorname{Capacity}(o,t,p)},\quad \operatorname{Capacity}>0.
\]

The ratio is dimensionless only after source and target quantities have been verified as compatible within their own domain. The operation does not imply that passenger capacity and warehouse capacity are interchangeable real-world concepts.

### 6.2 Synthetic reference fixture

| Domain | Object | Load | Capacity | Expected utilization | Expected bucket |
|---|---|---:|---:|---:|---|
| School transport | Assignment A1 | 30 | 40 | 0.75 | Moderate |
| School transport | Assignment A2 | 36 | 40 | 0.90 | High |
| Inventory | Bin I1 | 60 | 80 | 0.75 | Moderate |
| Inventory | Bin I2 | 90 | 100 | 0.90 | High |

For this case only, define `Low` for 0 ≤ U < 0.60, `Moderate` for 0.60 ≤ U < 0.85, and `High` for U ≥ 0.85. These are **synthetic illustrative thresholds**, not transport safety standards or warehouse operating policies. A target plugin may reuse the bucket operator only after adopting or replacing this threshold policy explicitly.

Expected calculations: A1 and I1 both yield 0.75; A2 and I2 both yield 0.90. Equal numeric outputs establish a shared arithmetic pattern, **not** equal operational risk or interchangeable intervention policy.

### 6.3 Transfer tests

Positive tests: verify typed division, explicit denominator checks, exact threshold behavior at 0.60 and 0.85, snapshot binding, stable ODK version, and provenance from input records to derived metric.

Negative tests: reject capacity 0, incompatible measurement units, missing numerator, duplicated SQL join rows, stale snapshots, and a caller without permission to read the target records. Distinguish SQL `NULL` from zero and preserve row-level security. Reject averaging per-bin utilization without an explicit weighting policy when total utilization is required.

**Proposed transfer claim:** the generic ratio/bucket capability can be reused with a new domain adapter. **Not claimed:** that the warehouse policy, business value, or source SQL query can be copied unchanged.

## 7. Track B — school-bus scheduling to constrained resource assignment

### 7.1 Source mechanism

`CASE-003` uses a composite WE state for students, trips, vehicles, duties, and constraints. A candidate CDE Delta may reassign or resequence a trip; the resulting composite state must satisfy capacity, timing, resource exclusivity, and other declared constraints before promotion.

### 7.2 Receiving problem

Consider a synthetic equipment-assignment system with three fixed jobs and two machines. A job requires one compatible machine for its entire interval. Unlike a school bus, a machine may have setup-time or tool-compatibility restrictions; those are **receiving-domain** constraints, not transferable facts.

| Job | Interval | Compatible machines |
|---|---|---|
| J1 | 09:00–09:40 | M1, M2 |
| J2 | 09:20–10:00 | M1, M2 |
| J3 | 10:05–10:45 | M1, M2 |

If setup time is assumed zero and there are no additional constraints, J1 and J3 may share one machine while J2 uses the other. The minimum machine count is at least two because J1 and J2 overlap, and the exhibited schedule uses two. This is a **synthetic combinatorial result**, not an industrial performance finding.

### 7.3 Reusable and non-reusable pieces

Potentially reusable: state-container composition, interval-overlap predicate (after time semantics are bound), candidate reassignment Delta schema, global exclusivity validator, version checks, no-reuse-on-path search bookkeeping, and promotion gates.

Must be re-specified: equipment compatibility, setup and teardown, labor rules, maintenance, cost model, objective priority, and any irreversible actuation. Bus passenger capacity and student ride-time limits are not valid machine constraints.

### 7.4 Required rejection example

Suppose a candidate moves J2 to M1 while J1 remains on M1 from 09:00 to 09:40. The move is locally well-typed, but it violates composite machine exclusivity between 09:20 and 09:40. The CDE validator must reject it even if the ODK score improves. A locally legal Delta does not establish a globally legal state.

## 8. Track C — transaction graph analysis to code-impact triage

### 8.1 Source reasoning pattern

`CASE-004` studies transaction evidence, graph relations, and defeasible compositional-identity hypotheses. Its transferable **method** may include typed graph traversal, evidence-dependence tracking, competing hypotheses, and uncertainty-qualified explanation. It does not provide a verified mapping from transaction flows to program semantics.

### 8.2 Receiving context

In software governance, nodes may represent functions, modules, data resources, tests, or deployment artifacts. Edges may represent calls, data dependence, control dependence, imports, or declared contracts. A calling graph alone is only one perspective: dynamic dispatch, reflection, configuration, generated code, and external effects can escape static call-edge coverage.

The proposed path is **Calling Graph → UTN localization → OCSRE typed object/evidence interfaces → impact hypothesis → targeted validation**. Localization narrows candidates; it does not prove impact completeness or authorize a code change.

### 8.3 Synthetic example

Assume a change to function `parseOrder` and a static call edge `submitOrder → parseOrder`. The graph suggests `submitOrder` may be affected, but it does not establish that all runtime paths execute the changed code or that no data-flow or configuration-dependent consumers exist. The receiving-domain adapter must supply code-specific semantics, tests, and security policy.

Positive checks: record the changed artifact version, preserve edge provenance, produce an impact candidate set, and link proposed regression tests to changed contracts. Negative checks: a missing dynamic call edge, an indirect data consumer, a stale graph snapshot, a passing unit test with a failing integration invariant, and a caller lacking deployment authority.

**Transfer boundary:** reuse the evidence-governed graph-analysis discipline; do not transfer transaction-identity probabilities, wallet-control assumptions, or the interpretation of graph connectivity.

## 9. Kernel invariance and adapter accounting

For each track, pin the ODK artifact and comparator/registry versions. A claimed **kernel-invariant relay** requires zero source-code changes to the pinned ODK. Adapter changes are allowed but must be counted and inspected; a hidden domain branch inside the kernel invalidates the invariance claim. Changes to plugins, adapters, schemas, thresholds, validators, and test suites must be reported separately.

A proposed transfer ledger includes: source capability/version, target adapter/version, kernel digest, target object type, semantic assumptions, test suite, conformance result, rejected trials, integration effort, validation effort, maintenance burden, and target outcome. A capability that requires rewriting the core may still be useful engineering, but it does not support OCSH-002 as formulated.

## 10. Authority and epistemic boundaries

The relay package must not broaden the intersection of invoker, source, receiving-domain, and organizational permissions. Read-only derived metrics cannot acquire mutation authority merely by being composed with an effectful plugin. Every derived claim retains its epistemic class: observation, measurement, deductive result, statistical inference, hypothesis, recommendation, authorization, or verified outcome.

A successful comparator score is not a proof; a graph path is not causal identity; a candidate CDE Delta is not a committed state; and a committed internal state does not undo or authorize irreversible external actions. Independent receiving-domain review is required before a claim is promoted from proposed transfer to validated transfer.

## 11. Proposed conformance profiles

| Profile | Required evidence | Permitted claim |
|---|---|---|
| R0 — Interface | Typed manifest, identity/perspective/state binding, dependency versions | Interface compatibility only |
| R1 — Semantic | R0 + receiving-domain fixtures, alignment, negative tests, permission checks | Semantic conformance on tested scope |
| R2 — Transfer | R1 + held-out target baseline, complete cost ledger, independent review | Validated transfer on declared target scope |
| R3 — Relay portfolio | R2 + multi-target monitoring, regression, negative-transfer records, drift controls | Governed portfolio reuse on evaluated targets |

Profiles are **proposed CASE-005 evaluation labels**, not externally ratified certification levels. None is claimed to have been achieved by the synthetic examples.

## 12. Positive reference tests (proposed)

| ID | Test | Expected result |
|---|---|---|
| CDR-P01 | Equal ratio arithmetic across bus and bin fixtures | Numeric equality with distinct semantics |
| CDR-P02 | Threshold at 0.60 | Moderate under declared synthetic policy |
| CDR-P03 | Threshold at 0.85 | High under declared synthetic policy |
| CDR-P04 | Valid machine assignment J1/J3 share machine | Composite feasibility under stated assumptions |
| CDR-P05 | J1/J2 overlapping jobs | Lower bound of two machines |
| CDR-P06 | Source and target WE resolvers differ | Distinct identity namespaces preserved |
| CDR-P07 | Pinned ODK with new target adapter | Kernel digest unchanged |
| CDR-P08 | Pure plugin composition | No state mutation or external effects |
| CDR-P09 | Target evidence provenance reconstruction | Full trace to source records and transforms |
| CDR-P10 | Code graph impact hypothesis | Candidate impact, not proof or deployment authorization |
| CDR-P11 | Receiving-domain held-out validation | Result recorded separately from source tests |
| CDR-P12 | Failed transfer trial | Negative outcome retained in relay ledger |

These are expected outcomes under stated fixtures, not test execution reports.

## 13. Negative and adversarial tests (proposed)

| ID | Failure injection | Required behavior |
|---|---|---|
| CDR-N01 | Zero capacity | Reject division |
| CDR-N02 | SQL NULL treated as zero | Reject or qualify; preserve NULL semantics |
| CDR-N03 | Join duplicates assignment rows | Detect changed cardinality and block invalid metric |
| CDR-N04 | Unauthorized inventory record | Deny access without leaking derived value |
| CDR-N05 | Stale target snapshot | Reject or revalidate temporal binding |
| CDR-N06 | Incompatible metric units | Reject absent validated conversion |
| CDR-N07 | Same ratio, different operational policy | Do not inherit source policy |
| CDR-N08 | Aggregate ratios across mismatched grains | Reject absent declared aggregation contract |
| CDR-N09 | Overlapping machine duties | Reject composite Delta |
| CDR-N10 | Missing machine setup time | Mark incomplete; no production promotion |
| CDR-N11 | Local Delta valid, global resource conflict | Reject candidate promotion |
| CDR-N12 | Reused path Delta or unbounded loop | Enforce CDE path/termination controls |
| CDR-N13 | Source plugin changes without version bump | Fail integrity/version conformance |
| CDR-N14 | Hidden ODK domain patch | Fail kernel-invariance claim |
| CDR-N15 | Plugin widens permissions | Deny invocation or promotion |
| CDR-N16 | Correlated evidence counted as independent | Flag dependence; revise confidence |
| CDR-N17 | Transaction graph edge interpreted as common ownership | Reject unsupported identity conclusion |
| CDR-N18 | Missing dynamic code call | Report impact-recall limitation; require supplemental evidence |
| CDR-N19 | Graph reachability treated as proof of runtime impact | Reject epistemic promotion |
| CDR-N20 | Passing unit test used as deployment approval | Deny unauthorized action |
| CDR-N21 | Source-domain success replaces target testing | Fail relay promotion gate |
| CDR-N22 | Only successful transfers logged | Fail completeness/audit check |
| CDR-N23 | Negative transfer concealed in average benefit | Require per-target distribution and failures |
| CDR-N24 | External irreversible action followed by internal rollback | Preserve external-action residual and escalation |

## 14. Case-specific conformance obligations

The following **CDR-001–CDR-022** are case-level obligations. They complement, rather than renumber or replace, `SPEC-004` OPC-001–OPC-020 and `OCSRE-011` CSR-001–CSR-018.

| ID | Priority | Requirement |
|---|---|---|
| CDR-001 | P0 | Every relay candidate MUST identify a versioned source capability and target adapter. |
| CDR-002 | P0 | Receiving WE identity MUST be resolved independently of source keys and addresses. |
| CDR-003 | P0 | Metric meaning, unit, grain, time, and perspective MUST be declared. |
| CDR-004 | P0 | Unknown or incompatible semantics MUST block promotion. |
| CDR-005 | P0 | SQL NULL, joins, and row-level permissions MUST survive adaptation. |
| CDR-006 | P0 | Source policy thresholds MUST NOT silently become target policy. |
| CDR-007 | P0 | Target permissions MUST NOT be expanded by relay or composition. |
| CDR-008 | P0 | Evidence lineage and epistemic classes MUST be preserved. |
| CDR-009 | P0 | Pure computation MUST be distinguished from candidate and effectful operations. |
| CDR-010 | P0 | Composite-state constraints MUST be validated before CDE promotion. |
| CDR-011 | P0 | Source-domain validation MUST NOT substitute for target validation. |
| CDR-012 | P0 | Code-impact localization MUST NOT be treated as complete program semantics. |
| CDR-013 | P0 | Authorization and irreversible external-action boundaries MUST be explicit. |
| CDR-014 | P1 | The pinned ODK digest and all adapter changes SHOULD be reported. |
| CDR-015 | P1 | Held-out receiving-domain baselines MUST be specified for transfer claims. |
| CDR-016 | P1 | Integration, validation, and maintenance costs MUST be counted in net benefit. |
| CDR-017 | P1 | Rejected, failed, and indeterminate trials MUST remain visible. |
| CDR-018 | P1 | Transfer claims MUST specify target scope and uncertainty. |
| CDR-019 | P1 | Regression and drift monitoring SHOULD follow promotion. |
| CDR-020 | P1 | Independent receiving-domain review SHOULD challenge semantic equivalence. |
| CDR-021 | P2 | Multi-agent relay MAY propose adapters but MUST respect the same gates. |
| CDR-022 | P2 | Open-ended plugin generation MAY be explored only with bounded budgets and validation. |

## 15. Measurement and falsification plan

For each target domain, compare at least: **B0** a native, hand-built solution; **B1** an ad hoc copy-and-adapt solution; and **R** the contract-based relay solution. Hold target tasks and correctness criteria constant. Record implementation effort, integration effort, validation effort, regression burden, runtime cost, failure rate, and maintenance effort. Report both gross reuse and net benefit.

A proposed net benefit definition is:

\[
B_{net}=V_{target}-C_{integration}-C_{validation}-C_{maintenance}-C_{risk},
\]

where each term must be defined in a common, declared unit or reported as a multidimensional vector rather than arbitrarily added. `V_target` is the target-specific value relative to a baseline, not an intrinsic score assigned by the relay system.

**OCSH-002:** falsified on the tested scope if a claimed generic ODK requires domain-specific core modifications. **OCSH-003:** not supported if contract-based plugins do not lower total adaptation cost against matched baselines. **OCSH-008:** not supported if target tests show no net transfer advantage or unacceptable safety failures. **OCSH-009:** requires pre-registered, untargeted task suites beyond these three designed tracks. **OCSH-010:** requires independent longitudinal experiments; three synthetic tracks cannot establish sustained scaling.

Report confidence intervals or uncertainty ranges when repeated trials exist, and all failures even if the mean result is positive. A successful synthetic example only demonstrates internal consistency under its assumptions.

## 16. Collective learning and relay governance

A multi-agent implementation could separate source-capability discovery, semantic-adapter design, target test generation, independent counterexample search, and governance review. Agreement among agents is not independent evidence if they share the same model, training data, prompts, or fixtures. The receiving domain retains the right to reject a relay candidate even when the source domain approves it.

Relay should preserve the full history: original hypothesis, counterexamples, revised adapter, rejected alternatives, accepted scope, and monitored outcomes. Repeated execution may contribute useful learning data, but repetition alone is not proof of generalization. Negative transfer is a first-class collective-learning artifact.

## 17. SIF, UIERU, MLIU, and ISGFTR positioning

OCSRE offers a common object/capability interface. SIF can use it for problem-to-capability localization and control-plane decisions; UTN and differential addressing can locate candidates; UIERU can organize relay portfolios and feedback; MLIU can consume validated learning units; and ISGFTR motivates empirical spillover and generalization studies. These are **proposed interoperability relationships**, not mandatory runtime dependencies, proven equivalences, or claims that a common protocol already exists among the projects.

## 18. Reproducibility package and evidence ledger

A future executable validation package should contain: immutable synthetic input fixtures; schemas and unit/perspective dictionaries; source and target adapters; pinned ODK/plugin versions and digests; positive/negative test manifests; baseline implementations; held-out test sets; cost accounting templates; and a complete relay-trial ledger. Any real data must undergo domain-specific privacy, access-control, and security review. The present Markdown case contains only illustrative fixtures and expected results.

A recommended ledger row is:

`trial_id | source_version | target_version | kernel_digest | adapter_digest | target_scope | conformance | held_out_result | baseline | costs | negative_transfer | decision | reviewer | residuals`

## 19. Cross-document traceability

| Research hypothesis | Case evidence proposed | Primary contract |
|---|---|---|
| OCSH-002 | ODK digest unchanged across Track A/B/C | SPEC-002, SPEC-004 |
| OCSH-003 | Total adapter cost vs B0/B1 | SPEC-004 |
| OCSH-005 | Composite Delta acceptance/rejection in Track B | SPEC-006 |
| OCSH-006 | Grain, time, and relation checks in all tracks | SPEC-003 |
| OCSH-007 | SQL-to-WE transformation and permission preservation in Track A | SPEC-001, SPEC-002, SPEC-004 |
| OCSH-008 | Held-out target transfer and negative-transfer ledger | SPEC-004, SPEC-005 |
| OCSH-009 | Separate untargeted task-suite experiment | SPEC-004, SPEC-005 |
| OCSH-010 | Separate longitudinal capability-growth experiment | SPEC-005, SPEC-006 |
| OCSH-011 | Code-impact localization and validation targeting in Track C | SPEC-004, SPEC-005, SPEC-006 |

All listed hypotheses remain **proposed / E0** in this document.

## 20. Counterexample interpretation and stop conditions

A failed case is not necessarily a failure of the whole OCSRE research program. It may indicate a defective adapter, a domain-specific incompatibility, a flawed genericity claim, a missing contract, or an ineffective target task. The trial ledger must classify the failure without retroactively changing success criteria. P0 safety failures terminate the attempted promotion. P1 performance failures block claims of demonstrated benefit. Unsupported claims about untargeted spillover or scaling must remain unpromoted regardless of source-domain success.

## 21. Explicit leftovers and open questions

1. What is the smallest interoperable capability manifest sufficient for independent implementations?
2. How should semantic equivalence be represented when target metrics have only partial analogies?
3. Which unit and granularity transformations can be statically verified?
4. How should SQL query provenance survive complex joins, views, and aggregation?
5. Can target identity binding be checked without exposing sensitive identifiers?
6. How should missing, uncertain, and contradictory measurements propagate through ODK?
7. Which composite constraints admit incremental rather than full revalidation?
8. What formal termination guarantees are possible for relay-generated CDE search policies?
9. How should concurrent target-state updates invalidate previously accepted candidates?
10. How can setup-time and other hidden scheduling constraints be discovered reliably?
11. How should dynamic calls and runtime configuration supplement static calling graphs?
12. What constitutes adequate code-impact recall for high-risk deployment decisions?
13. How can correlated agent judgments be identified and discounted?
14. Which evidence types are portable and which must be regenerated in the target domain?
15. What is the right denominator for failed versus attempted relay trials?
16. How should adapter-maintenance cost be amortized across multiple receiving domains?
17. How can risk cost be measured without hiding incomparable dimensions in one score?
18. What thresholds should qualify a transfer as economically or operationally meaningful?
19. How can semantic drift be detected after a target plugin is promoted?
20. When should a relay capability be revoked, quarantined, or rolled back?
21. What privacy-preserving mechanisms support collective relay evidence?
22. Which untargeted benchmarks would genuinely test OCSH-009 rather than reproduce design intent?
23. What longitudinal design could distinguish sustained growth from saturation for OCSH-010?
24. How should newly discovered counterexamples update SPEC contracts without invalidating historical trial records?

## 22. Conclusion

Cross-domain Object Plugin Relay is best understood as a **governed transfer experiment**, not a declaration of universal semantic equivalence. The candidate reusable substrate is the disciplined separation of WE identity, metric projection, typed comparison, reasoning, candidate evolution, evidence, and authorization. A transfer succeeds only when a receiving domain independently validates the capability on its own objects, constraints, and objectives, and when its benefit survives full cost and failure accounting. This case provides reproducible synthetic starting points and explicit falsification conditions for OCSH-002, OCSH-003, and OCSH-008. It deliberately leaves untargeted spillover and long-run scaling open.

---

**Repository placement:** `cases/CASE-005-Cross-Domain-Object-Plugin-Relay.md`  
**Related next case:** `cases/CASE-006-AI-Generated-Code-Governance-Through-Calling-Graphs-and-CDE.md`  
**Research status:** Proposed / E0. No runtime, benchmark result, or externally validated transfer is claimed.
