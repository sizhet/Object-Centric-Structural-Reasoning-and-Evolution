# SPEC-002 — Object Differential Kernel and Comparator Contract

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Artifact:** `specs/SPEC-002-Object-Differential-Kernel-and-Comparator-Contract.md`  
**Version:** 1.0.0 (proposed research contract)  
**Status:** Normative proposal; conformance fixtures defined, no runtime or empirical validation claimed  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**License:** Apache-2.0

## Abstract

This specification defines a contract-first, domain-independent execution discipline for the Object Differential Kernel (ODK) and its typed comparator interfaces. The kernel consumes governed World Entity (WE) object views and `Object[metricIndices]` projections, performs resolution, projection, semantic alignment, evaluation, qualification, and trace production, and returns explicitly typed results. The contract separates comparison from identity resolution, logical entailment, causal inference, decision authority, and WE-native CDE state mutation. Domain adapters and Object Plugins supply metric semantics and comparator implementations; the kernel enforces their declared contracts without claiming a universal metric or mathematical equivalence across domains. It specifies P0 failure behavior, P1 portability expectations, testable conformance obligations, adversarial fixtures, and unresolved research residuals. No performance or transfer result is asserted.

## 1. Purpose, applicability, and boundaries

OCSRE progresses from Representation to Computation, Reasoning, In-Situ Learning, and Constrained Evolution. SPEC-001 defines identity, perspective, and state interfaces; this specification governs the **Computation** boundary. Its immediate targets are OCSRE-003 and OCSRE-004, with extensions into OCSRE-005/006/007/008/009/010/011.

The ODK MUST be reusable as an execution discipline across domain-specific adapters. Reuse does **not** mean that distance, similarity, utility, uncertainty, or comparator outputs have interchangeable semantics. The kernel MUST NOT silently invent domain units, identity mappings, missing-value imputations, permission grants, aggregation rules, or evidence strength.

Out of scope: universal metric discovery, a complete WE-SIO ontology, a universal theorem prover, a production security engine, causal identification, a guaranteed optimizer, and proof of structural scaling. Those remain separate research or implementation concerns.

## 2. Normative terminology and dependency

**MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** are obligations of this proposed contract, not claims of implementation. A *conformance report* identifies supported clauses, test evidence, deviations, and explicit leftovers.

This document inherits the following from `SPEC-001-Object-Identity-Perspective-and-State-Contract.md`: `IdentityRef`, `TypeRef`, `StateRef`/`StateSnapshot`, `PerspectiveRef`, provenance/evidence references, access context, and the separation of identity, state, address, perspective, and authority. Implementations MUST use SPEC-001-compatible references rather than redefining them.

A **metric index** is a typed projection selector, not an unqualified numeric array index. A **comparator** is a versioned, declared operation over compatible projections. A **differential** is a qualified comparison result; it is not by itself a CDE Typed Delta. A **qualified result** retains status, evidence, and unresolved semantics.

## 3. Non-equivalences and kernel invariants

1. `same_metric_value` MUST NOT imply `same_identity`.
2. `high_similarity` MUST NOT imply logical entailment, causal influence, or authorized action.
3. `metric_distance` MUST NOT be interpreted as directional advantage without a declared direction and perspective.
4. `Object[metricIndices]` MUST NOT discard object identity, snapshot version, temporal scope, perspective, or access context.
5. `comparator_output` MUST NOT silently mutate an object, plugin, policy, or authoritative state.
6. `normalize(x)` MUST NOT imply that source units, baseline, distribution, or uncertainty have been preserved unless its contract explicitly says so.
7. `aggregate(children)` MUST NOT imply a valid parent-level claim absent a granularity/aggregation contract.
8. `score` MUST NOT be treated as a probability or confidence without calibration and an explicit interpretation contract.
9. `candidate_delta` MUST NOT be treated as a committed WE-native CDE state transition.
10. `traceability` MUST NOT be confused with validity: an auditable computation can still be semantically wrong.

## 4. Canonical kernel pipeline

```text
Request + AccessContext
   -> Resolve     (identity, snapshot, perspective, capability)
   -> Project     (typed Object[metricIndices] views)
   -> Align       (units, types, time, granularity, missingness)
   -> Evaluate    (versioned comparator/operator)
   -> Qualify     (evidence, uncertainty, policy, limitations)
   -> Trace       (replayable provenance and residuals)
   -> DifferentialResult | TypedFailure | Unresolved
```

Each stage MUST return a structured status and MUST preserve earlier qualifications. Implementations MAY fuse physical operations for efficiency only if observable stage semantics and trace reconstruction remain equivalent. Short-circuiting on P0 failures is required.

## 5. Proposed interoperable records

The following schemas are conceptual and intentionally independent of a programming language or storage engine.

```yaml
MetricIndex:
  metric_id: string
  metric_version: string
  object_type_scope: TypeRef
  value_type: scalar | vector | categorical | set | graph | structured
  unit: string | null
  temporal_semantics: instant | interval | window | timeless
  granularity: object | relation | composite | population
  perspective_scope: PerspectiveRef | neutral-with-justification
  null_policy: reject | propagate | explicit-imputation
  access_label: AccessLabel
  provenance_requirement: EvidencePolicy

ProjectionRef:
  identity: IdentityRef
  state: StateRef
  perspective: PerspectiveRef
  metric_indices: [MetricIndex]
  values: TypedValues
  valid_time: TemporalScope
  evidence_refs: [EvidenceRef]
  access_context: AccessContext
  projection_version: string

ComparatorDescriptor:
  comparator_id: string
  version: string
  accepted_types: [TypeRef]
  metric_requirements: [MetricIndex]
  output_semantics: distance | similarity | ordering | difference | predicate | structured
  symmetry: symmetric | asymmetric | conditional | unspecified
  direction: higher-better | lower-better | contextual | none
  normalization_contract: NormalizationPolicy | null
  granularity_contract: GranularityPolicy
  uncertainty_contract: UncertaintyPolicy
  determinism: deterministic | seeded | stochastic
  evidence_policy: EvidencePolicy
  permissions_required: [Permission]
  side_effects: none

DifferentialResult:
  status: valid | qualified | unresolved | rejected
  lhs: ProjectionRef
  rhs: ProjectionRef
  comparator: ComparatorDescriptor
  output: TypedComparatorValue | null
  interpretation: string
  uncertainty: UncertaintyRecord
  evidence_refs: [EvidenceRef]
  trace_ref: TraceRef
  residuals: [Residual]
  policy_decision: PolicyDecision
```

`neutral-with-justification` is a declared claim requiring evidence; it MUST NOT be assumed merely because the caller omits a perspective. An implementation MUST publish exact serializations, schemas, and supported versions before claiming interoperability.

## 6. `Object[metricIndices]` projection contract

Projection MUST resolve the requested WE snapshot and perspective first. Each metric index MUST identify its version, domain, unit, temporal semantics, granularity, missingness policy, and access classification. A projected value MUST retain a link to the underlying object/snapshot and evidence lineage. Derived values MUST carry transformation provenance and may not inherit the epistemic status of raw measurements automatically.

For an illustrative object `Bus#17`, `Object[capacity, occupied_seats]` is meaningful only with a declared snapshot and unit semantics. A separate derived metric `remaining_seats = capacity - occupied_seats` requires a derivation rule, compatible units, and a validity check; a negative result may indicate overbooking or bad data, not automatically a valid operational state.

## 7. Semantic alignment contract

Alignment is a typed, inspectable operation. It MUST test:

- object-type compatibility and any permitted cross-type mapping;
- metric identity/version and intended interpretation;
- dimensional and unit compatibility, including conversion provenance;
- valid-time overlap, observation lag, and snapshot freshness;
- granularity correspondence and aggregation/disaggregation authorization;
- perspective, direction, objective, and baseline consistency;
- nulls, absent values, censoring, and imputation disclosures;
- permissions and permitted information flow;
- evidence quality and provenance availability.

An alignment plan MUST record every non-identity transformation. When no authorized alignment exists, the kernel MUST return `unresolved` or `rejected`; it MUST NOT quietly coerce. Approximate alignment MUST be marked `qualified`, with its error/uncertainty model and applicability limits.

## 8. Comparator contract and mathematical properties

Comparator implementations MUST declare input/output types, domain, version, parameterization, directionality, symmetry, normalization, granularity behavior, uncertainty interpretation, deterministic/stochastic behavior, and any assumptions. Properties MUST be tested, not inferred from names. For example, a comparator called `distance` is not necessarily a metric: non-negativity, identity of indiscernibles, symmetry, and triangle inequality each require separate evidence.

A directional score `D(A,B|p,t)` MAY differ from `D(B,A|p,t)`. A similarity score MAY be non-transitive. Thresholded comparators MUST declare threshold ownership, calibration data, tie handling, and abstention behavior. Comparators that learn parameters MUST identify their training data and model version; comparison-time parameter updates are prohibited unless explicitly modeled as a separate governed learning action.

## 9. Generic operator registry

| Operator | Required contract | Common failure |
|---|---|---|
| `Select` | typed selection, access, snapshot | unauthorized projection |
| `Align` | semantic conversion and trace | unit or time mismatch |
| `Compare` | versioned comparator semantics | false identity inference |
| `Differential` | directional typed output | conflating score with state delta |
| `Normalize` | baseline, units, scope | untraceable scaling |
| `Bucketize` | boundaries, inclusivity, ordering | boundary drift |
| `Combine` | input types, weights, missingness | incompatible score addition |
| `Aggregate` | grain, membership, measure | invalid parent inference |
| `Rank` | perspective, ties, abstention | hidden policy choice |
| `Explain` | provenance, limitations | unsupported causal narrative |

`Encode` and `Derive` MAY be exposed by SQL/attribute plugins under the same typing, provenance, and permission requirements. Operator composition MUST be type-checked at every edge; successful composition is not evidence of downstream utility.

## 10. Typed result, uncertainty, and failure semantics

Results MUST distinguish: `valid` (all declared conditions met), `qualified` (explicit approximations/limitations), `unresolved` (insufficient or incompatible information), and `rejected` (contract or permission violation). `valid` means *valid under the declared computational contract*, not true in every real-world interpretation.

Required failure classes include `IDENTITY_UNRESOLVED`, `SNAPSHOT_MISMATCH`, `TYPE_MISMATCH`, `UNIT_MISMATCH`, `TEMPORAL_MISALIGNMENT`, `GRANULARITY_UNSUPPORTED`, `PERSPECTIVE_CONFLICT`, `MISSING_VALUE_UNHANDLED`, `EVIDENCE_INSUFFICIENT`, `PERMISSION_DENIED`, `COMPARATOR_CONTRACT_VIOLATION`, and `NONDETERMINISM_UNDISCLOSED`. Failures MUST be traceable without disclosing protected inputs.

## 11. Security, privacy, and epistemic governance

The kernel MUST preserve source access restrictions through projections, transformations, caches, traces, and relay outputs. Derived metrics MUST NOT be used to reconstruct forbidden inputs in violation of access policy. A trace MAY be redacted but MUST disclose that redaction and preserve a reviewable protected audit path when policy permits.

The kernel MUST distinguish observed values, transformed values, estimated values, inferred comparisons, and decision recommendations. Confidence, uncertainty, and evidential support MUST retain their own typed fields; no conversion between them is implicit. A comparison MUST NOT grant authority to change a WE state, deploy code, or execute a physical action.

## 12. Object Plugin boundary and portability

Plugins MAY supply metrics, transformations, comparators, and explanations. They MUST declare dependency versions, input/output contracts, resource limits, permission requirements, provenance, and side-effect policy. The ODK MUST remain unchanged when substituting a conforming domain plugin; otherwise the implementation MUST disclose the kernel modification and cannot count that case as unchanged-core reuse under OCSH-002.

Relay to another domain requires new conformance evidence. Compatibility at the type-signature level alone does not establish semantic transfer. Negative transfer and failed adapters MUST be recorded.

## 13. ODK integration with reasoning, learning, localization, and CDE

**Reasoning:** Comparator outputs are premises or evidence candidates, not automatically valid logical conclusions. SPEC-003 controls classical preservation and cross-granularity inference.

**In-situ learning:** Feedback MAY recalibrate metric definitions, comparators, or policies through a separately authorized versioned learning update. Existing results MUST retain their original version references.

**Localization:** UTN, MDT, WE-HDT, and SIF MAY consume differential results to propose candidate structural locations. Localization does not establish identity or authorization.

**WE-native CDE:** Differential results MAY score candidate Typed Deltas or state containers. Candidate generation, constraint checks, promotion, rollback, and irreversible external actions remain under SPEC-006 and appropriate authorities.

**Code governance:** Calling-graph differences MAY help localize impacted functions; sound change-impact analysis also requires relevant data/control flows, contracts, permissions, security assumptions, and regression evidence. A graph similarity score is not proof that a patch is safe.

## 14. Proposed operation signatures and pseudocode

```text
project(object_ref, metric_indices, perspective, snapshot, access)
  -> ProjectionRef | TypedFailure

align(lhs, rhs, alignment_policy, access)
  -> AlignmentPlan | TypedFailure | Unresolved

compare(aligned_lhs, aligned_rhs, comparator_ref, parameters, access)
  -> DifferentialResult | TypedFailure

run_odk(request):
  resolved = resolve(request.refs, request.snapshot, request.perspective)
  require_authorized(resolved, request.access)
  projected = project_all(resolved, request.metric_indices)
  plan = align(projected.left, projected.right, request.alignment_policy)
  if plan.status != valid_or_explicitly_qualified: return plan.failure
  raw = compare(plan.inputs, request.comparator)
  qualified = qualify(raw, plan, request.evidence_policy)
  return attach_trace_and_residuals(qualified)
```

These signatures specify observable obligations, not a runnable reference implementation. All stage boundaries MUST preserve P0 semantics even if optimized into a single execution plan.

## 15. Conformance requirements

| ID | Priority | Requirement | Minimum evidence |
|---|---|---|---|
| ODK-001 | P0 | Preserve SPEC-001 identity/state/perspective references | round-trip fixture |
| ODK-002 | P0 | Validate metric type, version, unit, and temporal scope | incompatible-input fixtures |
| ODK-003 | P0 | Enforce access policy before projection and trace output | deny-and-redact fixture |
| ODK-004 | P0 | Reject unauthorized implicit alignment | unit/grain/time mismatch |
| ODK-005 | P0 | Record all explicit alignment transformations | reproducible alignment trace |
| ODK-006 | P0 | Validate comparator declared domain and semantics | invalid-domain fixture |
| ODK-007 | P0 | Preserve directionality and perspective | A/B reversal test |
| ODK-008 | P0 | Distinguish missing, unknown, and imputed values | null-policy fixture |
| ODK-009 | P0 | Separate differential results from identity, proof, and authority | misuse rejection tests |
| ODK-010 | P0 | Return typed valid/qualified/unresolved/rejected statuses | status matrix |
| ODK-011 | P0 | Preserve provenance and epistemic qualification | lineage replay |
| ODK-012 | P0 | Never mutate authoritative WE state during comparison | read-only invariant |
| ODK-013 | P0 | Enforce declared cross-granularity contracts | aggregation counterexample |
| ODK-014 | P0 | Version comparators and normalization parameters | version-drift fixture |
| ODK-015 | P1 | Permit unchanged-kernel domain plugin substitution | cross-domain conformance |
| ODK-016 | P1 | Trace operator composition and failure propagation | composed pipeline fixture |
| ODK-017 | P1 | Disclose nondeterminism, seeds, and reproducibility bounds | repeated-run report |
| ODK-018 | P1 | Measure positive and negative cross-domain transfer | held-out transfer protocol |
| ODK-019 | P1 | Support residual and uncertainty reporting | explicit leftover fixture |
| ODK-020 | P2 | Benchmark execution cost without weakening P0 guarantees | performance/security report |

### 15.1 Required conformance report

Each report SHOULD contain: implementation identifier and version; kernel version; adapter/plugin versions; supported metric/comparator descriptors; fixture identifiers; expected and observed outputs; pass/fail/qualified/untested outcomes; permission context; trace references; unresolved residuals; known deviations; and reviewer/date. Passing an implementation's own tests is not equivalent to independent verification.

### 15.2 Suggested execution order

**P0 first:** identity and permissions → metric typing → alignment → comparator semantics → epistemic qualification → no mutation. **P1 second:** plugin substitution → composition → repeatability → transfer. **P2 last:** performance optimization and multi-agent execution.

## 16. Counterexample-first test catalog

| ID | Counterexample | Expected response |
|---|---|---|
| CE-001 | Two different WEs share identical metric values | do not merge identities |
| CE-002 | `meters` compared with `seconds` | reject |
| CE-003 | Celsius/Fahrenheit compared without conversion contract | unresolved/reject |
| CE-004 | Measurements refer to disjoint time windows | qualified or reject per policy |
| CE-005 | Bus and fleet occupancy compared at different grains | reject without aggregation contract |
| CE-006 | Comparator marked symmetric returns asymmetric results | contract violation |
| CE-007 | Score direction inverted under a new perspective | preserve explicit direction |
| CE-008 | NULL silently replaced with zero | reject |
| CE-009 | Normalization baseline changes without version update | reject/flag drift |
| CE-010 | High similarity asserted as proof of identity | reject inference |
| CE-011 | High ranking treated as action permission | deny action |
| CE-012 | SQL-derived metric exposes protected source column | deny/redact |
| CE-013 | Cached result reused after state/version change | invalidate or qualify |
| CE-014 | Comparator changes parameters during evaluation | reject undisclosed mutation |
| CE-015 | Plugin produces valid type but wrong domain semantics | fail semantic fixture |
| CE-016 | Local delta score used to commit globally invalid CDE state | reject promotion |
| CE-017 | Calling graph omits data-flow impact | report incomplete impact evidence |
| CE-018 | Relay produces degraded held-out outcomes | record negative transfer |

All tests are **proposed fixtures**, not executed results. An implementation MUST record any untested P0 fixture as unverified, not passed.

## 17. Worked illustrative contracts

### 17.1 School-bus scheduling

Compare two candidate composite schedules under declared metrics: fleet size, student travel time, route duration, capacity violations, and fairness constraints. A comparator may rank a candidate with fewer buses higher under a particular policy, but an overloaded bus MUST still fail CDE feasibility checks. ODK scoring is advisory; SPEC-006 controls state promotion.

### 17.2 SQL-native object adaptation

A database column `trip_minutes` is transformed into a typed metric with time unit, source query, row-to-WE mapping, and authorization. `Bucketize(trip_minutes)` requires explicit interval boundaries and NULL handling. `Normalize(trip_minutes)` requires a baseline and version. Neither transformation establishes WE identity or permission to expose the result.

### 17.3 Transaction and compositional identity

Similarity among transaction behavior patterns MAY produce candidate associations, not verified common ownership. Directional weak evidence, missing observations, and alternative hypotheses MUST remain explicit; no high score automatically resolves a compositional identity.

### 17.4 AI-generated code governance

A changed function's calling-graph neighborhood is projected as a structured metric view. A comparator identifies candidate impacted nodes and routes them to UTN/SIF localization. Subsequent contract checks, data/control-flow analysis, security review, and regression testing determine whether any change is safe; ODK output alone cannot authorize deployment.

## 18. Hypothesis traceability and measurement

| Hypothesis | SPEC-002 contribution | Validation dependency |
|---|---|---|
| OCSH-002 | unchanged-core kernel across domain adapters | identical kernel hash, cross-domain fixtures |
| OCSH-003 | versioned plugin comparator contracts | adaptation effort and regression cost |
| OCSH-006 | explicit grain alignment and aggregation | invalid-inference rate |
| OCSH-007 | typed SQL transformations | SQL semantic/security preservation |
| OCSH-008 | relay of validated comparators | held-out transfer, negative transfer |
| OCSH-009 | unanticipated downstream utility | preregistered untargeted tasks |
| OCSH-011 | graph differential for code impact | impact recall, false positives, review cost |

All hypotheses retain **proposed / E0** status until supported by appropriate experiments. The contract's existence is not empirical evidence for the hypotheses.

## 19. Dependencies and responsibility boundaries

- `SPEC-001`: authoritative OCSRE identity, state, perspective, and object-view boundary.
- `SPEC-003`: preservation of classical reasoning and guarded granularity inference.
- `SPEC-004`: plugin composition, dependencies, and capability governance.
- `SPEC-005`: feedback, evidence status, learning and epistemic governance.
- `SPEC-006`: composite WE state, Typed Delta, CDE constraints, and relay.
- `OCSRE-004`: conceptual ODK/operator rationale; this document defines its proposed interoperability obligations.
- `OCSRE-006`: SQL transformation semantics.
- `OCSRE-009`: evidence governance and promotion gates.
- `OCSRE-010`: localization through UTN/WE-HDT/SIF shared interfaces.
- `CASE-002`, `CASE-003`, `CASE-004`, `CASE-005`, `CASE-006`: prospective conformance/validation cases.

WE-SIO supplies WE representation foundations. MDT, UTN, and WE-HDT supply distinct localization/differential methods, not assumed equivalent. UIERU and ISGFTR motivate relay/spillover hypotheses without implying validated scaling.

## 20. Explicit leftovers and open research questions

1. A machine-checkable cross-language schema for every conceptual record.
2. Formal equivalence criteria for optimized/fused kernel pipelines.
3. A general ontology for metric compatibility across domains.
4. A policy for conflicting metric versions and ontology migrations.
5. Uncertainty propagation through heterogeneous operator chains.
6. Robust handling of censored, delayed, and selectively missing data.
7. Quantification of information loss during granularity transformation.
8. Formal characterization of comparator symmetry and metric axioms.
9. Calibration of ranking thresholds across perspectives.
10. Auditable privacy-preserving differential traces.
11. Cache invalidation under temporal and permission changes.
12. Adversarial plugin behavior and isolation guarantees.
13. Comparator drift detection and rollback of learned parameters.
14. Compositional semantics for nested and recursive Object Plugins.
15. Soundness/completeness tradeoffs in graph-based code impact analysis.
16. Cross-domain negative-transfer prediction before deployment.
17. Resource-bounded conformance testing for large composite WEs.
18. Independent benchmark datasets and preregistration protocols.
19. Multi-agent comparator disagreement and conflict adjudication.
20. Separation of comparator scoring from real-world action governance under latency pressure.
21. Evidence standards for OCSH-009 untargeted spillover.
22. Whether common contracts produce sustained net capability growth (OCSH-010), not yet established.

Every unresolved item MUST remain visible in research-trace documentation or future validation plans; implementation convenience MUST NOT silently convert it into an assumption of correctness.

## 21. Release and implementation discipline

This artifact is a **research contract**, not a production certification. An OCSRE v1.0.0 release MAY publish the specification before a reference runtime. Claims of conformance require reproducible test records; claims of benefit require baseline-controlled experiments. Future revisions SHOULD retain a change log for comparator semantics and include migration guidance for breaking metric contracts.

## 22. Conclusion

A shared Object Differential Kernel is useful only if its generic execution path preserves the semantics of the objects and metrics it compares. SPEC-002 therefore makes semantic alignment, typed comparator declarations, provenance, permissions, uncertainty, and non-mutation first-class obligations. It enables testable domain portability without assuming that heterogeneous comparisons are equivalent, that a score proves a claim, or that a comparison authorizes state evolution. The next step is conformance testing, followed by controlled cross-domain evaluation—not an unsupported assertion of general intelligence or scaling.
