# SPEC-006 — WE-Native CDE, Composite State, and Relay Contract

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Release track:** v1.0.0 — Research Framework and Contracts  
**Document type:** Proposed normative interface specification; not a certified implementation  
**Authors:** Sizhe Tan & GPT-Obot  
**License:** Apache-2.0  
**Status:** Research proposal / E0; conformance requirements are specified, not empirically certified.

## Abstract

This specification defines a proposed interoperability contract between World Entity (WE) objects and Constrained Delta Evolution (CDE). A CDE State-Container may hold a single WE or a composite of multiple WEs, typed relations, resources, constraints, and versioned evidence. Evolution proceeds through candidate Typed Deltas, sandbox application, validation, authority review, controlled promotion, and monitoring. A valid local edit does not establish global feasibility. Likewise, an attractive differential score does not establish deductive truth, authorization, or successful real-world execution.

The contract also defines how evolution strategies, candidate generators, validation artifacts, and learned capabilities may be relayed across objects, domains, and agents without silently transferring permissions or assuming semantic equivalence. It integrates the identity and perspective boundaries of SPEC-001, the comparator discipline of SPEC-002, the reasoning/granularity safeguards of SPEC-003, plugin composition of SPEC-004, and the learning/evidence governance of SPEC-005. This is a **specifications-first** research artifact: no production runtime, convergence theorem, or positive scaling result is claimed.

## 1. Purpose, scope, and non-goals

**Purpose.** Specify the minimum common interfaces and obligations for WE-native constrained state evolution, composite-state consistency, and validated capability relay.

**In scope:** object/state references; state ownership; composite membership; typed candidate Deltas; constraints; search-path memory; candidate generation and evaluation; permission boundaries; commit/rollback; provenance; multi-agent proposals; receiver-side relay conformance; negative tests.

**Out of scope:** choosing a universal search algorithm, proving convergence for arbitrary state spaces, defining WE-SIO identity from scratch, implementing a distributed transaction manager, certifying domain-specific safety, or establishing an empirical scaling law.

**Separation of responsibilities:** WE-SIO supplies foundational entity semantics; OCSRE specifies shared interfaces; CDE supplies a general constrained-evolution framework; ODK evaluates typed differences; SIF/UTN/WE-HDT may localize candidates; UIERU and related relay systems may organize transfer. These are interfaces, **not claims of algorithmic equivalence**.

## 2. Normative language and precedence

**MUST / MUST NOT** indicate proposed mandatory obligations for a conforming implementation; **SHOULD** indicates a recommended default with documented exceptions; **MAY** indicates an optional capability. A specification's normative force applies only within its declared conformance profile and implementation scope.

When contracts interact, more restrictive identity, evidence, privacy, permission, safety, and domain invariants take precedence over permissive plugin or search behavior. Conflicts MUST produce an explicit unresolved result rather than an implicit override. All experimental claims remain E0 until separately validated.

## 3. Foundational distinctions

The following are different concepts and MUST remain distinguishable:

| Concept | Meaning | Not equivalent to |
|---|---|---|
| `WEIdentity` | Stable semantic reference to an entity under an identity policy | SQL row key, address, metric similarity |
| `StateSnapshot` | Versioned observation/representation of entity state | Entity identity, ground truth |
| `StateContainer` | Bounded set of state components and invariants for an evolution attempt | An automatically authorized mutable object |
| `TypedDelta` | Proposed, typed transformation with declared effects | Committed state change |
| `ODKResult` | Typed comparison/evaluation with qualifications | Proof of feasibility or authority |
| `Candidate` | Hypothetical state after a proposed Delta | Real-world outcome |
| `Promotion` | Authorized advancement of a validated candidate | External action completion |
| `RelayArtifact` | Portable strategy/capability plus contracts and evidence | Receiver-side validation or permission |

The default rule is: **propose ≠ validate ≠ authorize ≠ commit ≠ observe outcome**.

## 4. Minimal WE-native State-Container contract

A container MUST declare an immutable container reference, its owner or controlling authority, scope, baseline version, included WEs, relevant relation edges, applicable perspectives, constraint set, evidence references, and allowed mutation surface. A composite container is not automatically a new WE identity: it MAY be a bounded working state over multiple existing entities.

```yaml
StateContainer:
  container_id: string
  schema_version: string
  owner_ref: AuthorityRef
  baseline_state_ref: StateRef
  membership:
    we_refs: [WEIdentityRef]
    relation_refs: [TypedRelationRef]
  granularity_contract_ref: ContractRef
  temporal_scope: TemporalScope
  perspectives: [PerspectiveRef]
  constraint_set_ref: ConstraintSetRef
  permission_scope_ref: PermissionRef
  evidence_refs: [EvidenceRef]
  read_set: [TypedPath]
  allowed_write_set: [TypedPath]
  container_version: VersionRef
```

This schema is illustrative, not a required serialization format. A `StateRef` MUST bind to an explicit version or defensible snapshot semantics. Unresolved identity or conflicting versions MUST block promotion until resolved or explicitly waived by an authorized, documented policy.

## 5. Composite-state invariants

Composite state requires constraints that are not reducible to independent per-object checks. An implementation MUST distinguish:

1. **Local invariants:** field types, object-specific capacity, nonnegative inventory.
2. **Relational invariants:** valid assignment, referential integrity, relation cardinality.
3. **Shared-resource invariants:** no double booking, no duplicate student assignment, inventory conservation.
4. **Temporal invariants:** ordered events, scheduling windows, stale-state detection.
5. **Perspective/policy invariants:** optimization goals versus hard feasibility constraints.
6. **Authority invariants:** changes must remain within authorized scope.

For a container state $S$, a proposed Delta $\delta$ is eligible only if its preconditions hold and every applicable hard constraint is satisfied by the candidate $S'=\mathrm{Apply}(S,\delta)$. This is a proposed interface obligation, not a guarantee that every domain's constraints are decidable.

## 6. Typed Delta envelope

A Delta MUST identify its target, declared semantic type, baseline version, preconditions, read/write sets, proposed effects, constraints, validation requirements, provenance, and authority requirements. The engine MUST reject unknown mutation types unless an explicitly versioned extension contract authorizes them.

```yaml
TypedDelta:
  delta_id: string
  delta_type: string
  schema_version: string
  target_container_ref: ContainerRef
  base_version: VersionRef
  proposer_ref: SubjectRef
  precondition_refs: [PredicateRef]
  read_set: [TypedPath]
  write_set: [TypedPath]
  proposed_effects: [TypedEffect]
  invariant_refs: [ConstraintRef]
  perspective_refs: [PerspectiveRef]
  evidence_refs: [EvidenceRef]
  required_validation_refs: [ValidatorRef]
  required_authority_ref: AuthorityRef
  idempotency_key: string
  reversibility: reversible | compensatable | irreversible
```

Representative types include `AttributeDelta`, `RelationDelta`, `AssignmentDelta`, `ResourceDelta`, `PolicyDelta`, `MetricDefinitionDelta`, and `CompositeDelta`. Epistemic or policy updates MUST NOT be silently treated as physical state changes. A composite Delta MUST specify atomicity expectations and partial-failure behavior.

## 7. Delta composition, path memory, and non-reuse

Delta composition is conditional, not automatically associative or commutative. Two Deltas MAY be composed only when preconditions, effect scopes, ordering, and constraints remain compatible. A declared commutativity or inverse relationship MUST be supported by tests or formal conditions, not assumed from naming.

CDE's **same-path Delta non-reuse** rule is represented by a path-scoped ledger. A normalized Delta signature MUST include sufficient state, type, target, and effect context to avoid conflating unrelated edits. The path ledger MUST prevent a prohibited repeat within that path; it MUST NOT ban valid reuse across independent paths merely because their human-readable descriptions match. Distinguish the delta *definition* from a delta *application instance*.

A branch may contain a `Yes` continuation, a `NoSubtree` exclusion, or a documented unresolved branch. `NoSubtree` MUST preserve its scope and reason; it MUST NOT be generalized to all future states without evidence. Loop-back MUST be bounded by a declared policy (e.g., depth, budget, monotone measure, visited-state detection, or an explicit human stop gate). **Termination is not guaranteed in arbitrary open-ended search spaces.**

## 8. Candidate generation and M→N search

A generator MAY propose multiple successors from one or several parent candidates. The number of branches MAY adapt to evidence, remaining budget, residuals, and estimated value. Each generated candidate MUST carry its parent references, delta chain, baseline version, generation policy version, and validation status.

A generator is permitted to be heuristic, symbolic, learned, multi-agent, or hybrid. Its proposed output is not automatically feasible. Search pruning SHOULD record the relevant rule and evidence; rejected branches SHOULD be retained in a compact counterexample/residual registry when useful for collective learning.

## 9. Evaluation: ODK is not the validator

ODK may compare candidate and baseline objects using typed `Object[metricIndices]` projections, explicit unit alignment, perspective-aware scoring, and provenance. It MUST expose incomparability, missing values, metric conflicts, and uncertainty rather than manufacturing a scalar score.

Hard constraints and authorization MUST be checked independently of optimization scores. A high-scoring candidate that violates any applicable hard constraint MUST NOT be promoted. When perspectives conflict, the decision policy MUST identify who is entitled to choose and which trade-offs are allowed. A differential score is neither a proof of a proposition nor a prediction of realized external outcomes.

## 10. Evolution lifecycle and promotion gates

The reference lifecycle is:

```text
Baseline State (versioned)
    -> Generate Typed Delta
    -> Check Preconditions / Read-Write Scope
    -> Sandbox Apply to Candidate
    -> Validate Local + Composite + Temporal Constraints
    -> Evaluate with ODK / Multiple Perspectives
    -> Challenge with Counterexamples / Evidence Review
    -> Obtain Explicit Authority
    -> Atomic or Governed Promotion
    -> Monitor Outcome / Record Residuals
```

Every gate MUST emit a traceable disposition: `pass`, `fail`, or `unresolved` with reason codes. `Unresolved` MUST NOT be silently coerced to `pass`. A candidate MAY remain in a sandbox indefinitely without being promoted. Real-world effects require a distinct execution contract.

## 11. Concurrency, stale state, and transaction boundaries

Promotion MUST verify that the baseline version and relevant read-set assumptions remain valid. Concurrent proposals that write overlapping or invariant-coupled fields MUST be serialized, reconciled, or rejected under an explicit concurrency policy. Implementations MAY use optimistic concurrency, locking, or domain-specific transaction protocols, but MUST disclose guarantees and failure modes.

A composite update spanning external systems MUST NOT claim atomicity unless the underlying execution path actually provides it. Partial commits require an explicit recovery plan and observable status. Audit logs SHOULD be append-only or equivalently tamper-evident for the intended threat model.

## 12. Rollback, compensation, and irreversible actions

A reversible in-memory candidate can be discarded. A committed database change may require a compensating transaction. A physical action—such as dispatching a bus, moving funds, or deploying software—may not be reversible. Each Delta MUST declare one of these categories and the applicable rollback/compensation procedure.

**Rollback of a representation does not undo an external event.** Irreversible effects MUST require an explicit external-action authorization gate, with stronger review where impact is material. The system MUST preserve observed outcome evidence even when a proposed plan is abandoned.

## 13. Multi-agent proposal and collective evolution

Multiple agents MAY generate, critique, compare, or validate candidates, but proposal authority and promotion authority MUST be separately defined. Agreement among agents is not independent evidence if they share the same source, model failure, or derived artifacts. Conflict resolution MUST be explicit and provenance-aware.

An agent MAY contribute a Delta generator or constraint checker as a plugin under SPEC-004. It MUST NOT gain expanded permissions by joining a relay chain. Unresolved disagreements SHOULD be preserved as residuals or alternative candidate branches rather than merged into false consensus.

## 14. Relay artifact and receiver-side contract

A portable relay artifact SHOULD contain:

```yaml
EvolutionRelayArtifact:
  artifact_id: string
  capability_kind: generator | validator | metric | policy | workflow
  source_domain: string
  source_contract_versions: [ContractRef]
  input_output_types: [TypeRef]
  assumptions: [PredicateRef]
  permission_requirements: [PermissionRef]
  validation_evidence_refs: [EvidenceRef]
  known_counterexamples: [CounterexampleRef]
  negative_transfer_records: [EvidenceRef]
  integration_cost_record: CostRef
  provenance_ref: ProvenanceRef
  version: string
```

The receiving domain MUST independently check type compatibility, semantic assumptions, permissions, domain constraints, baseline comparisons, and relevant regression tests. Source-side success MUST NOT be represented as receiver-side certification. A relay MAY transfer a question, counterexample, metric, or validator without transferring the source policy or execution authority.

## 15. Capability spillover and evaluation boundaries

The hypothesis is that reusable typed evolution capabilities may improve previously untargeted tasks. Evidence of spillover requires held-out tasks, a credible baseline, measurement of adaptation and validation costs, and recording of negative transfer. Suggested metrics include feasibility rate, net objective improvement, constraint violations, transfer success, regression burden, cost per validated capability, and marginal reach.

**Capability count is not effective coverage.** A newly installed plugin may provide no validated benefit; a single well-defined comparator may unlock multiple uses. Sustained scaling or open-ended growth is an unproven research hypothesis, not an implication of the interface design.

## 16. Illustrative application contracts

### 16.1 School-bus scheduling — CASE-003

**Container:** buses, students, routes, time windows, assignments, capacities. **Candidate Delta:** reassign a student or merge routes. **Hard checks:** each student assigned according to policy; no capacity overrun; feasible timing and route continuity. **Objectives:** fleet count and student travel burden, under a declared perspective policy. A local reduction in vehicles cannot justify a globally infeasible assignment.

### 16.2 Transaction and compositional identity — CASE-004

**Container:** observed transactions, temporal edges, inventory hypotheses, identity hypotheses, confidence-qualified evidence. **Candidate Delta:** revise a *hypothesized* grouping or evidence interpretation. **Hard checks:** provenance, chronology, conservation assumptions where applicable, privacy and uncertainty boundaries. A plausible identity linkage MUST NOT become an asserted real-world identity merely through search optimization.

### 16.3 AI-generated code governance — CASE-006

**Container:** code entities, calling graph, data/control-flow dependencies, interfaces, security policies, test evidence, deployment context. **Candidate Delta:** modify a function, interface, or dependency. **Checks:** affected contract compatibility, change-impact localization, security and regression evidence. Calling-graph reachability is one perspective; it does not exhaust runtime semantics. UTN may help locate affected objects, but localization does not authorize deployment.

### 16.4 SQL-to-WE adaptation — CASE-002

SQL rows may supply observations for WE states only through identity resolution and typed semantic transformation. A row key MUST NOT be assumed to be WE identity. SQL authorization, NULL semantics, join multiplicity, and source provenance MUST survive transformations. Database writes remain governed external effects.

### 16.5 Cross-domain capability relay — CASE-005

A route-assignment validator might inspire a resource-allocation validator in another domain, but only after the receiving domain checks its own resource semantics, constraints, and performance baseline. The relay record MUST include failed adaptations as well as successes.

## 17. Conformance profiles and required artifacts

| Profile | Required coverage | Evidence artifacts |
|---|---|---|
| **C0 — Container** | Identity, version, membership, constraints, permission scope | Schema validation; identity and stale-state negatives |
| **C1 — Candidate Evolution** | Typed Delta, path ledger, sandbox, hard checks | Candidate traces; rejected-branch tests |
| **C2 — Governed Promotion** | Authorization, concurrency, rollback/compensation, monitoring | Gate logs; conflict and failure-injection tests |
| **C3 — Composite/Relay** | Cross-object invariants, receiver validation, negative transfer | Composite fixtures; cross-domain conformance reports |

Higher profiles inherit lower ones. A profile claim MUST specify its implementation version, domain, test corpus, exclusions, and unresolved failures. This document defines proposed profiles; it does not award certifications.

## 18. Normative conformance requirements

| ID | Requirement |
|---|---|
| **WCR-001** | Every container MUST have stable reference, version, ownership, and declared scope. |
| **WCR-002** | WE identity MUST remain distinct from location, similarity, SQL key, and candidate state. |
| **WCR-003** | Composite membership and cross-object invariants MUST be explicit. |
| **WCR-004** | A Typed Delta MUST declare type, target, baseline, preconditions, read/write sets, and effects. |
| **WCR-005** | Unknown or unauthorized Delta types MUST be rejected. |
| **WCR-006** | Candidate application MUST be isolated from committed state until promotion. |
| **WCR-007** | Local and global hard constraints MUST pass before promotion. |
| **WCR-008** | Evaluation scores MUST NOT override failed feasibility or permission checks. |
| **WCR-009** | Perspective conflicts and incomparable metrics MUST be explicitly qualified. |
| **WCR-010** | Same-path prohibited Delta reuse MUST be detected using a declared signature policy. |
| **WCR-011** | Loop-back MUST have a declared bound, stop policy, or unresolved outcome. |
| **WCR-012** | `NoSubtree` exclusions MUST preserve scope and rationale. |
| **WCR-013** | Stale baselines and conflicting concurrent writes MUST be detected. |
| **WCR-014** | Promotion MUST require an identifiable authority and auditable gate outcome. |
| **WCR-015** | Reversibility, compensation, and irreversible-effect categories MUST be distinguished. |
| **WCR-016** | External actions MUST require separate authorization and outcome recording. |
| **WCR-017** | Evidence, inference, decision, and executed action MUST remain epistemically distinct. |
| **WCR-018** | Multi-agent consensus MUST NOT be treated as independent validation by default. |
| **WCR-019** | Relay artifacts MUST declare assumptions, versions, provenance, and known limitations. |
| **WCR-020** | Receivers MUST revalidate semantics, permissions, constraints, and regressions. |
| **WCR-021** | Negative transfer and rejected candidates MUST be recorded where relevant to claims. |
| **WCR-022** | Every conformance claim MUST include test evidence, exclusions, and explicit unresolved residuals. |

These identifiers are local to SPEC-006; `WECDE-*` in OCSRE-008 denotes earlier paper-level proposed obligations and is not silently renumbered here.

## 19. Counterexample-first test matrix

| Test | Failure mode | Expected result |
|---|---|---|
| **CE-001** | Two distinct WEs share a metric signature | No identity merge |
| **CE-002** | SQL row key mistaken for WE identity | Reject or require resolution |
| **CE-003** | Delta targets stale baseline | Reject/rebase under policy |
| **CE-004** | Local assignment valid; student double-booked globally | Reject composite candidate |
| **CE-005** | Vehicle capacity respected; route timing violated | Reject candidate |
| **CE-006** | Unapproved write outside declared scope | Reject Delta |
| **CE-007** | High ODK score but hard constraint fails | No promotion |
| **CE-008** | Mixed units or perspectives without alignment | Incomparable/unresolved |
| **CE-009** | Repeated prohibited Delta in same path | Reject branch |
| **CE-010** | Loop-back without stop policy | Block profile conformance |
| **CE-011** | `NoSubtree` exclusion applied outside its scope | Reject pruning decision |
| **CE-012** | Concurrent edits violate shared invariant | Conflict/revalidate |
| **CE-013** | Rollback claimed to undo irreversible transfer | Reject rollback claim |
| **CE-014** | Agent majority repeats one correlated source | No independent-evidence claim |
| **CE-015** | Source plugin relayed with expanded privileges | Reject receiver installation |
| **CE-016** | Relay works in source domain but fails receiver constraints | Record negative transfer |
| **CE-017** | Calling graph misses data-flow security impact | Require supplementary analysis |
| **CE-018** | Hypothesized transaction cluster promoted as verified identity | Block epistemic promotion |
| **CE-019** | External action executed before approval | Governance failure; incident record |
| **CE-020** | Composite partial commit falsely reported atomic | Fail conformance |

Tests MUST check both machine-readable outcomes and provenance/authority traces. Test fixtures and runtime results remain future work.

## 20. Validation protocol and hypothesis mapping

**Phase A — Static conformance:** validate container/Delta schemas, identity separation, typed paths, and policy references. **Phase B — Deterministic fixtures:** exercise valid and invalid local/composite transitions. **Phase C — Adversarial tests:** inject stale versions, conflicting writes, permission violations, ambiguous evidence, and unsafe relays. **Phase D — Comparative evaluation:** measure search quality and transfer benefit against domain baselines on held-out tasks. **Phase E — Independent replication:** reproduce claims with different agents, domains, and validation owners.

| Hypothesis | SPEC-006 test target |
|---|---|
| **OCSH-005** | Shared contracts support single-WE and composite transitions |
| **OCSH-002** | ODK evaluates domain candidates without changing the core kernel |
| **OCSH-003** | Contracted plugins reduce integration/adaptation cost |
| **OCSH-004** | In-situ feedback improves traceability or learning outcomes |
| **OCSH-006** | Explicit granularity contracts prevent invalid composite inferences |
| **OCSH-007** | SQL adapters preserve semantics and permissions |
| **OCSH-008** | Receiver-validated relay improves held-out transfer |
| **OCSH-009** | New capabilities yield net gains on untargeted tasks |
| **OCSH-010** | Sustained, validated capability growth occurs over repeated cycles |
| **OCSH-011** | Code governance improves localization and validation targeting |

OCSH-001 remains relevant to reasoning components but is not proven by this evolution contract. **All hypotheses are E0 at project inception.** No observed effect size, convergence rate, or certified safety level is asserted here.

## 21. Explicit leftovers and unresolved research questions

1. Formal semantics for composite WE identity versus transient State-Containers.
2. Domain-independent typing of read/write paths and effect summaries.
3. Constraint decidability and incomplete-validator qualification.
4. Sufficient conditions for safe Delta commutativity and composition.
5. Canonical Delta signatures without false-positive path exclusions.
6. Search completeness under path non-reuse and `NoSubtree` pruning.
7. Loop-back policies for non-monotone and unbounded state spaces.
8. Multi-object transaction semantics across heterogeneous stores.
9. Practical atomicity limits for cross-service operations.
10. Recovery and compensation for partially executed physical actions.
11. Provenance integrity and adversarial audit-log tampering.
12. Formal treatment of inconsistent perspectives and objectives.
13. Objective drift under in-situ policy and metric learning.
14. Epistemic uncertainty propagation across long Delta chains.
15. Agent collusion, correlated errors, and independent validation criteria.
16. Permission attenuation across nested plugin and relay graphs.
17. Receiver-side semantic alignment and negative-transfer thresholds.
18. Robust baselines for measuring integration and validation costs.
19. Open-ended candidate generation without uncontrolled search growth.
20. Version compatibility across WE-SIO, UTN, SIF, ODK, and CDE.
21. Domain-specific privacy controls for transaction identity hypotheses.
22. Sound change-impact coverage beyond calling graphs in code governance.
23. Conditions under which residual-driven exploration is beneficial.
24. Longitudinal tests of capability spillover and proposed scaling behavior.

Each leftover SHOULD be entered in `research-trace/UNRESOLVED-RESIDUALS.md` with ownership, evidence, and a proposed falsification or resolution path. Repetition of unresolved work across iterations is an explicit relay of residual knowledge, not an implicit success.

## 22. Cross-document interfaces and release discipline

**Primary conceptual basis:** `docs/OCSRE-008-WE-Native-CDE-and-Composite-State-Evolution.md`; `docs/OCSRE-007-In-Situ-Object-Learning-Decision-and-Feedback.md`; `docs/OCSRE-009-Epistemic-Separation-and-Object-Centric-Evidence-Governance.md`; `docs/OCSRE-011-Object-Capability-Spillover-Relay-and-Collective-Structural-Learning.md`.

**Normative neighbors:** `specs/SPEC-001-Object-Identity-Perspective-and-State-Contract.md`; `specs/SPEC-002-Object-Differential-Kernel-and-Comparator-Contract.md`; `specs/SPEC-003-Classical-Reasoning-Preservation-and-Granularity-Contract.md`; `specs/SPEC-004-Object-Plugin-and-Capability-Composition-Contract.md`; `specs/SPEC-005-In-Situ-Learning-Feedback-and-Epistemic-Governance-Contract.md`.

**Planned validation artifacts:** `cases/CASE-003-School-Bus-Scheduling-and-Composite-WE-State.md`; `cases/CASE-004-Transaction-and-Compositional-Identity.md`; `cases/CASE-005-Cross-Domain-Object-Plugin-Relay.md`; `cases/CASE-006-AI-Generated-Code-Governance-Through-Calling-Graphs-and-CDE.md`; `research-trace/HYPOTHESIS-REGISTRY.md`; `research-trace/COUNTEREXAMPLE-REGISTRY.md`; `TESTABLE-HYPOTHESES.md`; `VALIDATION-ROADMAP.md`.

**Planned illustration:** `figures/Fig-007-WE-Native-CDE-and-Composite-State-Evolution.png` (do not mark as available until generated).

A v1.0.0 release may describe this specification as a proposed contract framework. It MUST NOT imply that the proposed profiles have passed conformance, that a production implementation exists, or that structural spillover/scaling has been demonstrated.

## Conclusion

WE-native CDE is a proposed disciplined bridge from object-centric representation, comparison, reasoning, and learning to constrained evolution. Its central invariant is that **candidate generation, semantic validity, global feasibility, authorization, commitment, and observed outcome remain separate, traceable stages**. Composite State-Containers extend this discipline across interacting WEs, while receiver-side relay contracts permit capabilities to travel without transporting unjustified authority or unsupported claims. The next research step is not to declare success, but to implement falsifiable conformance fixtures, adversarial counterexamples, and independent cross-domain validation.
