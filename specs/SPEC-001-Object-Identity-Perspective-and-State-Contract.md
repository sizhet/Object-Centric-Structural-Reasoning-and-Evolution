# SPEC-001 — Object Identity, Perspective, and State Contract

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Artifact:** `specs/SPEC-001-Object-Identity-Perspective-and-State-Contract.md`  
**Version:** 1.0.0 (proposed research contract)  
**Status:** Normative proposal; conformance tests specified, implementation and empirical validation pending  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**License:** Apache-2.0

## Abstract

This specification establishes the minimum interoperable contract for representing, resolving, observing, comparing, and evolving World Entities (WEs) through OCSRE object interfaces. It separates durable object identity from source identifiers, addresses, representations, versions, states, perspectives, metrics, evidence, and authorization. It also defines guarded state snapshots, typed relations, temporal semantics, composite membership, and failure behavior. Its purpose is not to replace the WE-SIO identity and representation model: it specifies the obligations an OCSRE adapter must satisfy when exposing that model to Object Differential Kernel (ODK), reasoning, in-situ learning, localization, WE-native CDE, and relay. All examples are illustrative and do not constitute validation.

## 1. Purpose and scope

OCSRE's core progression—Representation → Computation → Reasoning → In-Situ Learning → Constrained Evolution—requires an object reference that remains meaningful across stages. Without a common contract, a database row can be mistaken for an entity, a temporary structural address for permanent identity, a perspective-bound estimate for an objective fact, or a candidate state for a committed state.

This document defines **P0 semantic and ownership safety** at that interface. It covers:

- WE identity and identity-resolution outcomes;
- object type, state snapshots, versioning, and temporal scope;
- perspective ownership and context;
- typed metric projections and relations;
- provenance and epistemic qualification;
- composite state membership and authority boundaries;
- contract failures, conformance fixtures, and explicit residuals.

It does **not** specify a global identity authority, universal ontology, database storage engine, comparator mathematics, classical proof calculus, learning algorithm, CDE search policy, or production authorization mechanism. Those concerns belong to WE-SIO or companion specifications and implementations.

## 2. Normative language and status

**MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** denote obligations within this *proposed* specification. They do not imply that any software already conforms. A **conforming adapter** is one that passes the declared fixtures and documents supported capabilities, limitations, and exceptions. A **claim of empirical benefit** additionally requires an independently specified evaluation.

All examples use conceptual JSON-like records. Field names are proposed interoperability fields, not assertions about an existing WE-SIO implementation. Domain-specific adapters MAY map them to different physical representations if observable semantics are preserved.

## 3. Fundamental non-equivalences

The following distinctions are normative:

1. **Entity identity ≠ source row key.** A key identifies a record within a source, not necessarily a world entity.
2. **Entity identity ≠ address.** A UTN, MDT, WE-HDT, graph path, or index can locate a representation without proving entity identity.
3. **Identity ≠ state.** The same entity can persist through multiple versions and temporal states, subject to declared identity-continuity rules.
4. **State version ≠ event time.** Version order records revisions; valid-time and observation-time are separate axes.
5. **Perspective ≠ truth.** An actor's evaluation, objective, or observation is qualified by perspective and evidence.
6. **Metric equality ≠ identity equality.** Similar objects need not be the same object.
7. **Membership ≠ ownership.** Inclusion in a composite does not automatically authorize mutation.
8. **Candidate ≠ committed state.** Inference, learning, or CDE proposal cannot silently update the authoritative snapshot.
9. **Evidence ≠ authority.** Supporting a claim does not grant permission to act on it.

Any downstream operation that relies on a collapsed distinction MUST fail closed or return a qualified unresolved result.

## 4. Canonical interface model

A conceptual object view is:

```text
ObjectView = {
  identity: IdentityRef,
  type_ref: TypeRef,
  state: StateRef,
  perspective: PerspectiveRef,
  attributes: TypedAttributeSet,
  relations: TypedRelationSet,
  evidence: EvidenceRefs,
  permissions: AccessContext,
  provenance: ProvenanceRefs
}
```

The `ObjectView` is a **read or computation context**, not a claim that these fields are all stored inside the WE or that the viewer can access every field. Access control MAY redact fields; the adapter MUST make redaction distinguishable from absence when disclosure policy permits. Unauthorized callers MUST NOT infer protected identity, membership, or attribute values from error details.

### 4.1 IdentityRef

```text
IdentityRef = {
  namespace: string,
  entity_id: opaque_string,
  entity_type: TypeRef,
  resolution_status: resolved | ambiguous | provisional | unresolved,
  identity_rule_ref: optional versioned reference,
  lineage_refs: optional list
}
```

- `namespace + entity_id` MUST be unique within the declared identity authority and namespace scope.
- An identifier MUST NOT be reused for a different entity within the same declared identity scope.
- A provisional identity MUST remain distinguishable from a verified or resolved identity.
- A merge, split, alias, or reidentification MUST create an auditable identity-resolution event; silent replacement is forbidden.
- The system MUST preserve enough lineage to interpret older references, or explicitly report that lineage is unavailable.
- Composite identity MUST NOT be inferred solely from shared members, a matching label, or a matching metric vector.

### 4.2 TypeRef

```text
TypeRef = { ontology: string, type_id: string, schema_version: string }
```

Types MUST be versioned. Type compatibility MUST be established by an explicit declared mapping, subtype rule, or adapter contract. Similar labels are insufficient. An incompatible or unknown type MUST NOT be silently coerced.

### 4.3 StateRef and StateSnapshot

```text
StateRef = {
  identity: IdentityRef,
  version: opaque_monotonic_revision_token,
  valid_interval: optional interval,
  observed_at: optional timestamp,
  recorded_at: timestamp,
  status: observed | inferred | candidate | committed | superseded,
  snapshot_ref: opaque reference
}
```

The version token MUST support unambiguous equality and stale-write detection within the state authority; it need not be a globally ordered integer. A `StateSnapshot` MUST be immutable as a historical record or preserve an equivalent append-only audit trail. A candidate snapshot MUST be distinguished from a committed one. Event-time corrections MUST NOT rewrite historical provenance without trace.

### 4.4 PerspectiveRef

```text
PerspectiveRef = {
  perspective_id: opaque reference,
  owner_ref: actor or policy authority,
  purpose: string,
  objective_ref: optional versioned reference,
  metric_policy_ref: optional versioned reference,
  effective_interval: optional interval,
  visibility_scope: optional access label
}
```

Perspective is a first-class context for scores, preferences, interpretations, and decisions. A perspective MAY be shared, but its owner and policy MUST remain identifiable. Cross-perspective comparisons MUST declare alignment or return `not_comparable`. A perspective-dependent evaluation MUST NOT be promoted to perspective-independent fact by dropping its context.

### 4.5 Evidence and provenance references

A consequential assertion MUST be linked to its epistemic class (`source_record`, `observation`, `derived_metric`, `deductive_conclusion`, `statistical_inference`, `hypothesis`, `evaluation`, `decision_proposal`, `authorized_action`, or `validated_outcome`), provenance, and temporal scope. Confidence or score fields MUST NOT substitute for a proof or validation record. The detailed promotion and feedback rules are assigned to SPEC-005.

## 5. State and identity invariants

**INV-001 — Identity stability.** An update to attributes, metrics, or state MUST NOT change `IdentityRef` absent an explicit identity transition event.

**INV-002 — State version integrity.** Every consequential read and proposed write MUST declare the state version it uses; stale writes MUST be rejected or explicitly rebased and revalidated.

**INV-003 — Temporal qualification.** A claim with bounded validity MUST NOT be applied outside that interval without an explicit extension rule and evidence.

**INV-004 — Perspective qualification.** A subjective metric or preference MUST retain its perspective identifier through transformations and relay.

**INV-005 — Typed attributes.** Attributes and metric projections MUST include or resolve type, unit/dimension where applicable, missingness semantics, and schema version.

**INV-006 — Typed relations.** Relation endpoints, direction, cardinality, temporal scope, and permitted inference laws MUST be declared; transitivity and inversion MUST NOT be assumed.

**INV-007 — Epistemic integrity.** Derived or inferred claims MUST retain lineage to inputs and transformations, including limitations and uncertainty.

**INV-008 — Authority separation.** Read, evaluate, propose, validate, approve, and commit are distinct capabilities; one MUST NOT imply another.

**INV-009 — Composite boundaries.** Composite membership and authority MUST be explicit, versioned, and validated across affected members.

**INV-010 — Explicit unresolved outcomes.** Missing, ambiguous, stale, redacted, contradictory, or unaligned references MUST yield distinct qualified results where safely disclosable, never invented defaults.

## 6. Object[metricIndices] and typed projection

`Object[metricIndices]` denotes a **projection request**, not a new entity or a universal array index. A projection request MUST resolve:

```text
MetricProjectionRequest = {
  identity_ref, state_ref, perspective_ref,
  metric_selectors: [versioned selector],
  time_window, access_context
}
```

Its response MUST distinguish `value`, `missing`, `redacted`, `not_applicable`, `stale`, `ambiguous`, and `error` as appropriate. Returned values MUST carry metric definition, unit, transformation provenance, temporal coverage, and perspective binding. Where a SQL source is used, transformations such as `bucketize`, `normalize`, `combine`, `encode`, and `derive` MUST be declared and versioned. A normalized value MUST NOT be compared across different baselines without an alignment contract.

The ODK owns typed alignment, comparison, and differential evaluation under SPEC-002. This specification owns the correctness of the object context supplied to that kernel.

## 7. Identity resolution and addressing

A resolution request MUST include a namespace, reference type, caller access context, and requested temporal scope where applicable. Its result MUST use a tagged outcome:

```text
ResolutionResult =
  Resolved(identity_ref, evidence_refs)
  | Ambiguous(qualified_candidates_or_count)
  | Provisional(identity_ref, qualification)
  | Unresolved(reason_code)
  | Denied(non_disclosing_reason)
```

An address resolver MAY use UTN, MDT, WE-HDT, SIF localization, SQL keys, or graph paths. The adapter MUST NOT claim that different addressing systems are mathematically equivalent. Address-to-identity mappings MUST carry provenance, version, and ambiguity. `Resolved` MUST reflect the adapter's declared resolution rule and assurance level; it MUST NOT imply absolute real-world certainty.

## 8. Relations, granularity, and composite identity

A relation assertion MUST declare endpoint types, predicate type, direction, valid time, provenance, and epistemic class. An inferred relation MUST identify the applied inference rule. For group and composite views:

- Membership MUST be distinguished from containment, representation, control, and ownership.
- Aggregate attributes MUST declare aggregation operator, denominator, missingness policy, time alignment, and overlap handling.
- A property of a group MUST NOT automatically be inherited by each member, nor vice versa.
- Composite identities MUST have explicit identity-continuity and membership-version rules.
- Multi-object operations MUST identify the full read/write set and cross-object invariants before any promotion.

Example: a fleet's mean occupancy does not prove each bus is under capacity; a transaction cluster does not establish a verified human identity; a calling-graph node does not fully represent program behavior.

## 9. State transitions and WE-native CDE boundary

A typed delta proposal MUST reference a base state, proposed changes, affected identities, expected versions, constraints, and proposer. The minimum guarded sequence is:

```text
Resolve identities and versions
  → Check permissions and temporal context
  → Construct candidate delta
  → Evaluate typed invariants and cross-object constraints
  → Record evidence, counterexamples, and residuals
  → Obtain required approval
  → Commit with version check, or reject
  → Record post-commit verification and outcome
```

This sequence is an **interface obligation**, not a specified CDE search algorithm. Candidate generation, M→N branching, path memory, no-reuse semantics, loop-back control, and rollback strategies are elaborated in SPEC-006 and OCSRE-008. Irreversible external effects MUST require explicit authorization and a declared recovery/compensation boundary; a database rollback MUST NOT be described as undoing an irreversible real-world action.

## 10. Perspective and policy changes

A change in perspective, objective, or scoring policy MUST produce a new versioned policy context. Recomputing a score under a new perspective MUST NOT rewrite historical scores as if they were generated under that perspective. Where two actors disagree, the system SHOULD preserve both qualified assessments, source evidence, and the adjudication rule if one exists. An unresolved disagreement MUST remain visible to downstream reasoning and relay.

## 11. Security and information-flow obligations

Identity and state contracts MUST enforce the caller's authorized view. In particular:

- Source SQL row-level and column-level permissions MUST remain effective after WE adaptation, aggregation, and caching.
- A metric or derived feature MUST NOT disclose restricted source attributes by inference when forbidden by the governing policy.
- Unauthorized graph traversal, identity resolution, and composite membership inspection MUST be denied or safely redacted.
- Audit events SHOULD record actor, requested operation, policy version, object reference, decision, and outcome, subject to privacy requirements.
- Relay MUST NOT widen the source capability's authority, data visibility, or action rights without explicit reauthorization.

The specification does not assert that a particular security model is sufficient; deployment-specific threat modeling and tests are required.

## 12. Proposed operation signatures

| Operation | Minimum inputs | Result / failure behavior |
|---|---|---|
| `resolve_identity` | source/address ref, namespace, temporal scope, caller | tagged resolution outcome; never silent merge |
| `read_state` | identity, requested version/time, caller | qualified snapshot or denied/unresolved |
| `project_metrics` | identity, version, perspective, selectors, caller | typed, provenance-bearing projections or qualified missingness |
| `read_relations` | identity, relation schema, time, caller | typed relation set with qualification |
| `construct_composite` | member refs, membership rules, owner, version | candidate composite with explicit unresolved members |
| `propose_state_delta` | base version, typed changes, proposer | candidate only; no committed mutation |
| `validate_candidate` | candidate, constraint set, policy version | pass/fail/indeterminate with evidence and residuals |
| `commit_candidate` | validated candidate, expected versions, authority | committed state reference or explicit rejection |

`indeterminate` MUST NOT be treated as `pass` by default. No operation in this table may infer additional permissions from the presence of an identity or address.

## 13. Conformance requirements

The following requirements are proposed as the testable acceptance criteria for SPEC-001.

| ID | Priority | Requirement | Mandatory negative fixture |
|---|---|---|---|
| OIS-001 | P0 | Separate entity identity from source keys | Two source rows referring to one WE must not force two identities |
| OIS-002 | P0 | Namespace and non-reuse of identifiers | Same local ID in different namespaces must not collide |
| OIS-003 | P0 | Preserve identity across state changes | Attribute edit must not silently mint a new WE |
| OIS-004 | P0 | Require versioned state reads and writes | Stale write must not overwrite current state |
| OIS-005 | P0 | Distinguish valid, observed, and recorded time | Late-arriving observation must not rewrite event chronology |
| OIS-006 | P0 | Preserve perspective ownership and policy | Stakeholder score must not become objective fact |
| OIS-007 | P0 | Enforce metric type, units, and schema versions | Meters vs seconds must not be directly compared |
| OIS-008 | P0 | Keep address resolution separate from identity proof | Same graph path must not imply same real-world entity |
| OIS-009 | P0 | Return qualified ambiguous/provisional outcomes | Ambiguous candidate set must not silently choose one |
| OIS-010 | P0 | Enforce typed relation signatures and inference laws | Parent-of must not be assumed symmetric |
| OIS-011 | P0 | Enforce explicit granularity conversions | Fleet mean must not become every bus's occupancy |
| OIS-012 | P0 | Preserve epistemic class and provenance | Statistical inference must not be relabeled deductive proof |
| OIS-013 | P0 | Separate composite membership from mutation authority | Non-owned member must not be edited |
| OIS-014 | P0 | Separate candidate from committed state | Proposed route change must not alter live schedule |
| OIS-015 | P0 | Preserve source and derived-data permissions | Restricted SQL column must not leak through metric projection |
| OIS-016 | P0 | Handle missing/redacted/stale/indeterminate distinctly | NULL must not be coerced into a confirmed zero |
| OIS-017 | P1 | Preserve lineage across merge/split/alias transitions | Historical evidence must not silently rebind |
| OIS-018 | P1 | Support safe cross-system object references | UTN and WE-HDT paths must not be asserted equivalent |
| OIS-019 | P1 | Preserve historical perspective/policy versions | Rescoring must not overwrite old evaluation context |
| OIS-020 | P1 | Record residuals and rejected operations | Failed alignment must not disappear from audit trail |

### 13.1 Conformance report schema

A report SHOULD include: adapter/version; declared scope; fixture ID; expected and observed result; pass/fail/indeterminate; input provenance; authorization context; evidence artifact reference; unresolved residuals; and known exceptions. A P0 failure prevents a claim of full SPEC-001 conformance. P1 support MAY be partial if clearly disclosed; the claimed conformance profile MUST list unsupported P1 requirements.

### 13.2 Suggested execution order

1. Static schema and type validation.
2. Identity, namespace, ambiguity, and state-version tests.
3. Temporal, perspective, and epistemic separation tests.
4. Relations, granularity, composite membership, and ownership tests.
5. Security and non-disclosure tests.
6. Cross-adapter regression, relay, and historical-lineage tests.

No runtime benchmark substitutes for these semantic conformance checks.

## 14. Counterexample-first test scenarios

**CE-001 — Duplicate source records.** Two SQL rows describe one bus at different times. Expected: source records remain distinct; WE identity may resolve to one entity only with an explicit rule and provenance.

**CE-002 — Same key, different entity.** Two databases both use `id=42`. Expected: namespace separation; no automatic merge.

**CE-003 — Changed attribute, same entity.** A bus changes assigned route. Expected: new state version, stable identity unless identity rules say otherwise.

**CE-004 — Unverified person cluster.** Transaction features suggest a shared controller. Expected: provisional compositional hypothesis, not verified person identity.

**CE-005 — Temporal mismatch.** Morning capacity is used for an evening route. Expected: stale/unaligned result unless an explicit temporal model supports transfer.

**CE-006 — Perspective collision.** Operator minimizes fleet count; parents minimize ride duration. Expected: distinct perspectives and objectives, no silent scalarization.

**CE-007 — Invalid group inheritance.** Average bus load is 70%. Expected: no conclusion that every bus is under capacity.

**CE-008 — Graph address reuse.** A function is moved to another module while a path is reused. Expected: address resolution is revalidated against identity and version.

**CE-009 — Unauthorized metric.** A restricted salary column is normalized into a derived score. Expected: authorization still applies; no derived-data leak.

**CE-010 — Stale candidate.** A route-change delta targets state version 5 while version 6 is committed. Expected: reject or explicitly rebase and revalidate.

**CE-011 — Composite external member.** A fleet candidate includes a contractor's bus without mutation rights. Expected: read-only or denied; no unauthorized state change.

**CE-012 — Evidence promotion.** A high similarity score is treated as identity proof. Expected: rejection of unsupported epistemic promotion.

**CE-013 — NULL coercion.** A missing capacity becomes zero in SQL adaptation. Expected: missingness retained or an explicit imputation policy recorded.

**CE-014 — Alias and split.** An entity cluster later splits into two. Expected: lineage and historical evidence remain interpretable; no silent reassignment.

**CE-015 — Irreversible action.** A candidate code deployment passes static checks but lacks deployment approval. Expected: no execution or release; validation is not authorization.

**CE-016 — Hidden membership inference.** A caller probes composite membership via error messages. Expected: non-disclosing denial consistent with access policy.

## 15. Worked cross-domain contract examples

### 15.1 Classical person reasoning

An assertion `Human(x)` and a rule `∀x (Human(x) → Mortal(x))` can be attached to a resolved object reference only under an explicit logical interpretation. An identity resolution failure blocks substitution of a specific person into a proof. The contract does not certify the premise as true merely because a proof step is valid. Formal validity belongs to SPEC-003 and OCSRE-002.

### 15.2 SQL-native school-bus objects

`school_bus.bus_id` is a source identifier; a verified `IdentityRef` requires mapping rules. Route assignments are versioned state attributes; `seats` and `riders` are typed metrics. A fleet aggregate is a composite view with explicit membership and time. A CDE proposal that reduces fleet count must validate every affected assignment and capacity constraint before promotion. This scenario is developed in CASE-002 and CASE-003.

### 15.3 Transaction/compositional identity

Wallet addresses, transactions, IP observations, and public keys can serve as evidence-bearing identifiers or features. They MUST NOT automatically establish that two records correspond to one human actor. Candidate clusters remain provisional and privacy/authorization rules apply. See CASE-004.

### 15.4 AI-generated code governance

A calling graph can locate affected functions but is not complete program semantics. The object interface separates function/module identity, source path, revision, call-edge evidence, ownership, and security context. UTN may aid localization; data flow, control flow, contracts, and regression evidence are still required before a code change is promoted. See CASE-006 and OCSRE-010.

## 16. Dependencies and responsibility boundaries

| Companion artifact | Responsibility relative to SPEC-001 |
|---|---|
| OCSRE-001, OCSRE-003 | Thesis, dynamic relations, temporal and granularity semantics |
| OCSRE-004 / SPEC-002 | Differential Kernel, comparator compatibility and output qualification |
| OCSRE-002 / SPEC-003 | Classical validity and cross-granularity inference preservation |
| OCSRE-005 / SPEC-004 | Plugin packaging, capability composition, dependency and permission boundaries |
| OCSRE-007, OCSRE-009 / SPEC-005 | Feedback, epistemic promotion, learning updates and evidence governance |
| OCSRE-008 / SPEC-006 | Composite State-Container, typed Delta, constraints, relay and promotion |
| OCSRE-010 / EXT-002 | UTN, MDT, WE-HDT and SIF localization interfaces |
| OCSRE-011, OCSRE-012 / EXT-005 | Validated capability transfer and open-ended growth hypotheses |
| CASE-001 through CASE-006 | Domain fixtures and negative-case validation |

**Ownership rule:** WE-SIO remains the canonical source for WE identity/representation concepts; SPEC-001 defines the *OCSRE interoperability obligations* and must be reconciled with any subsequently published WE-SIO normative schema. No undocumented equivalence is presumed.

## 17. Hypothesis traceability and evaluation

This contract is a prerequisite for testing **OCSH-001** (restricted classical preservation), **OCSH-002** (reusable ODK), **OCSH-004** (traceable in-situ learning), **OCSH-005** (single/composite CDE), **OCSH-006** (safe granularity contracts), **OCSH-007** (SQL adaptation), **OCSH-008** (validated relay), and **OCSH-011** (code governance). It is not itself evidence for any of these hypotheses.

Proposed evaluation metrics include: identity collision rate; ambiguous-resolution abstention rate; stale-write rejection rate; invalid granularity inference rate; provenance completeness; permission leakage rate; cross-adapter conformance coverage; and cost of identity/metric mapping. Each metric requires a declared test population, denominator, and baseline. Passing curated tests is not proof of general correctness.

## 18. Explicit leftovers and open questions

1. Which WE-SIO identity rules should be normative across organizations, and which remain domain-specific?
2. How should identity merge, split, and rollback preserve historical referential integrity?
3. What assurance levels are appropriate for provisional or probabilistic entity resolution?
4. How can privacy-preserving cross-system identity linkage be tested without revealing protected identifiers?
5. Which temporal model should be used for interval uncertainty, bitemporal corrections, and distributed clocks?
6. How should mutable ontologies and schema migrations preserve type compatibility?
7. What is the minimum safe representation for conflicting perspectives and multi-owner objectives?
8. How should partially observed composites and overlapping memberships be represented?
9. Which aggregate operators can be lifted across granularities, and under what proof obligations?
10. How should inaccessible provenance be represented without leaking restricted information?
11. Can identity and permission checks be made efficient at very large WE graph scale?
12. What are acceptable consistency and transaction guarantees for distributed composite state?
13. How should ODK caching respond to perspective, metric-definition, or authorization changes?
14. How should UTN/MDT/WE-HDT address drift be detected and repaired?
15. What formal proof techniques can establish selected invariants rather than merely testing them?
16. How should a relay recipient verify external identity claims without trusting source assertions blindly?
17. What governance process resolves disputes about authoritative identity mappings?
18. How should irreversible real-world actions be associated with a state history and compensating actions?
19. How should negative evidence, abstention, and contradictory identity claims affect downstream CDE?
20. What benchmark suite best tests domain transfer without rewarding overfitted mappings?

These items remain **open**, not implicitly solved by the interface proposal. Record new findings in `research-trace/UNRESOLVED-RESIDUALS.md`, `DEFINITION-REGISTRY.md`, and `COUNTEREXAMPLE-REGISTRY.md` when those files are authored.

## 19. Release and implementation discipline

The v1.0.0 research release MAY publish this contract without a runtime implementation. It MUST label the contract as proposed, distinguish authored specifications from verified results, and avoid claiming WE-SIO compatibility until tested. A future implementation SHOULD publish a machine-readable schema, fixture runner, negative-test corpus, security review, compatibility matrix, and versioned conformance report. Changes that weaken P0 safety obligations SHOULD require explicit versioning and documented rationale.

## 20. Conclusion

Object-centric structural intelligence requires a stable semantic interface before it can safely reuse differential computation, reasoning, learning, constrained evolution, and relay. SPEC-001 establishes that interface through explicit identity, state, perspective, evidence, granularity, and authority boundaries. The design intentionally favors **typed contracts, qualified uncertainty, and explicit leftovers** over unverified universal unification. It supplies a testable foundation for SPEC-002 through SPEC-006, while leaving implementation and empirical validation as separate obligations.
