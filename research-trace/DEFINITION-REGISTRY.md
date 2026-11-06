# DEFINITION-REGISTRY — OCSRE Research Trace

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Version:** v1.0.0 — Research Framework and Contracts  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**Status:** Proposed terminology registry; normative where explicitly cross-referenced by a SPEC; not an implementation or empirical validation  
**License:** Apache-2.0  
**Canonical location:** `research-trace/DEFINITION-REGISTRY.md`

## 1. Purpose, authority, and scope

This registry supplies a stable vocabulary for the twelve OCSRE research papers, six specifications, six cases, five extensions, and the research-trace assets. It is designed to prevent **definition drift** when a term moves between formal reasoning, SQL adaptation, composite-state optimization, transaction analysis, multi-agent relay, and code governance.

**Authority rule.** This registry is an index and interpretive aid. A specific normative contract in `SPEC-001` through `SPEC-006` takes precedence for its governed interface; a referenced external framework (such as WE-SIO, SIF, UTN, MDT, WE-HDT, CDE, or UIERU) retains authority over its own definitions. When two documents disagree, record the conflict in `DECISION-LOG.md` and `UNRESOLVED-RESIDUALS.md`; do not silently choose a convenient interpretation. This registry does not retroactively certify conformance.

**Notation rule.** Conceptual records and algorithms are *proposed interface sketches*, not claims that a deployed system already implements the fields. Terms such as MUST and MUST NOT are normative only when applied within a named proposed contract. All eleven OCSH hypotheses remain **E0 — Proposed**, with no empirical evidence asserted (`HYPOTHESIS-REGISTRY.md`).

## 2. Definition record schema and change control

Each canonical definition has: **ID**, **term**, **definition**, **boundary / non-equivalence**, **primary sources**, and where useful **example or counterexample**. IDs are stable; renaming a term does not reassign its ID. A change that alters referential, logical, security, temporal, or transition semantics requires a new registry revision, cross-reference audit, counterexample update, and decision record.

| Change class | Treatment | Example |
|---|---|---|
| Editorial | Clarify without changing meaning | Improve an explanation |
| Compatible refinement | Add constraints or fields without changing prior valid cases | Add provenance reference |
| Semantic revision | Version definition and affected contracts | Redefine identity continuity |
| Conflict / ambiguity | Preserve both interpretations pending decision | Different meanings of “state” |
| Deprecated alias | Keep searchability and migration mapping | Legacy label for an ObjectRef |

A consumer MUST NOT assume two similarly named concepts are equivalent merely because both are described as an “object,” “delta,” “score,” “identity,” or “relay.”

## 3. Foundational entities, identities, and views

### DEF-001 — World Entity (WE)
A **World Entity** is an entity represented under the WE ecosystem's identity and structural semantics, potentially exposing typed attributes, relations, temporal states, perspectives, evidence, and permissions. **Boundary:** a WE is not simply a SQL row, an address, a metric vector, or an LLM token. OCSRE uses WE-compatible interfaces; it does not redefine the external WE-SIO authority. **Sources:** OCSRE-001, SPEC-001, OCSRE-006.

### DEF-002 — Object (OCSRE usage)
An **Object** is a typed, contextual computational or reasoning view of a WE or an explicitly modeled composite, accessible through declared contracts. An Object is not necessarily an independently persistent entity and does not guarantee visibility of every WE attribute. **Boundary:** representation/view ≠ underlying entity. **Sources:** OCSRE-001/004, SPEC-001.

### DEF-003 — ObjectRef
A **typed reference** that resolves to an Object view under an identity namespace, type, state, temporal scope, perspective, and access context. Resolution may fail, be ambiguous, or return a provisional identity. **Boundary:** ObjectRef ≠ proof of real-world identity, permission to mutate, or unique physical storage location. **Sources:** SPEC-001, OCSRE-010, EXT-002.

### DEF-004 — IdentityRef
A namespace-qualified reference to an entity identity, with declared type, resolution status, and optional lineage. Its continuity is governed by an identity authority and versioned identity rules. **Boundary:** identity ≠ source key, display label, graph address, metric similarity, or shared ownership. **Sources:** SPEC-001, CASE-001/004.

### DEF-005 — Identity Resolution
A provenance-bearing process for mapping candidate records, aliases, or references to a resolved, provisional, ambiguous, or unresolved entity identity. Merge/split/reidentification events require auditability. **Boundary:** resolution hypothesis ≠ verified actor attribution. **Sources:** SPEC-001, CASE-004.

### DEF-006 — TypeRef
A versioned ontology/schema reference specifying an object's admissible attributes, relations, and operations. Compatibility requires explicit mapping or subtype rules. **Boundary:** same label ≠ compatible type. **Sources:** SPEC-001/004.

### DEF-007 — ObjectView
A permission-scoped computational view that may include `identity`, `type_ref`, `state`, `perspective`, typed attributes, relations, evidence, permissions, and provenance. **Boundary:** a view is not a guarantee that all fields are stored together or disclosed to the caller. **Sources:** SPEC-001.

### DEF-008 — Composite WE / Composite Object
A structured aggregate of multiple typed entities and relations with an explicit membership model and potentially global constraints. Membership and identity-continuity rules are domain-specific. **Boundary:** membership ≠ ownership; aggregate properties do not automatically distribute to members. **Sources:** OCSRE-008, SPEC-006, CASE-003/004.

### DEF-009 — Compositional Identity Hypothesis
A defeasible proposal that multiple observed accounts, addresses, events, or components participate in one controlling or functional actor structure. It carries evidence, competing alternatives, uncertainty, and revision history. **Boundary:** transaction connectivity ≠ proof of common real-world control. **Sources:** CASE-004, OCSRE-009.

## 4. Context, state, time, and granularity

### DEF-010 — Perspective / PerspectiveRef
A versioned interpretive or evaluative standpoint that determines which metrics, goals, evidence rules, or policies apply. **Boundary:** perspective ≠ objective truth, authorization, or identity. **Sources:** OCSRE-003, SPEC-001/002.

### DEF-011 — State / StateSnapshot
A typed representation of an entity or composite at a declared version and temporal scope. A snapshot may be observed, simulated, candidate, or committed; these statuses are not interchangeable. **Boundary:** state ≠ identity; version order ≠ event-time order. **Sources:** SPEC-001/006, OCSRE-008.

### DEF-012 — StateRef
A reference to a versioned state or snapshot, carrying the identity, snapshot/version identifier, and sufficient scope to distinguish historical from candidate or current state. **Boundary:** a StateRef is not a write capability. **Sources:** SPEC-001/006.

### DEF-013 — Temporal Scope
The declared valid-time, event-time, observation-time, processing-time, or transaction snapshot boundaries of a statement or measurement. Alignment across time axes must be explicit. **Boundary:** observations at different times cannot be silently compared as simultaneous facts. **Sources:** OCSRE-003/006, CASE-002.

### DEF-014 — Granularity
The level at which an entity, fact, metric, or decision is defined: individual, event, trip, route, group, fleet, system, etc. **Boundary:** group-to-member inheritance and member-to-group aggregation require explicit rules. **Sources:** OCSRE-003, SPEC-003, CASE-001/003.

### DEF-015 — Cross-Granularity Contract
A rule that declares when a relation, predicate, metric, or constraint may be lifted, projected, aggregated, or inherited between granularities, including loss and exception conditions. **Boundary:** no automatic inference from aggregate averages to each constituent. **Sources:** SPEC-001/003, OCSH-006.

### DEF-016 — Typed Attribute / Typed Relation
An attribute or relation whose domain, range, cardinality, temporal validity, perspective, provenance, and access constraints are declared. **Boundary:** same textual field name ≠ same semantic relation. **Sources:** SPEC-001, OCSRE-003.

## 5. Metrics, computation, and plugins

### DEF-017 — Metric
A typed, versioned measurement or derived evaluation with declared unit, scale, granularity, temporal scope, provenance, perspective, and missingness semantics. **Boundary:** metric ≠ proof, causal explanation, identity, or authorization. **Sources:** OCSRE-004, SPEC-002.

### DEF-018 — Metric Index / `metricIndices`
A typed selector identifying a registered metric or derivation in a metric schema. It is not necessarily a numeric array index. **Boundary:** a selector does not guarantee that every Object supports the metric. **Sources:** OCSRE-004, SPEC-002.

### DEF-019 — `Object[metricIndices]`
A conceptual typed metric projection of an Object under a declared context: `Project(ObjectRef, metricIndices, context)`. The result contains qualified values and their metadata. **Boundary:** projection ≠ bare vector; similarity of projections ≠ identity equivalence. **Sources:** OCSRE-004, SPEC-002.

### DEF-020 — Object Differential Kernel (ODK)
A proposed common computation interface that governs metric selection, compatibility/alignment, comparison or differential operations, qualification, and explanation while delegating domain meaning to explicit plugins. **Boundary:** generic execution discipline ≠ universal semantic equivalence or demonstrated kernel implementation. **Sources:** OCSRE-004, SPEC-002.

### DEF-021 — Differential / Metric Delta
A typed, context-qualified difference between compatible measurements, including direction, units, uncertainty, provenance, and interpretation constraints. **Boundary:** a metric difference is not a CDE state-transition Delta, causal claim, or automatically valid decision. **Sources:** OCSRE-004, SPEC-002/006.

### DEF-022 — Semantic Alignment
A contract-governed operation establishing comparability across types, units, scales, times, perspectives, granularities, missingness, and access contexts. It may refuse comparison. **Boundary:** unit conversion alone is not full semantic alignment. **Sources:** SPEC-002, CASE-002/005.

### DEF-023 — Generic Operator
A typed computation such as select, align, compare, normalize, bucketize, combine, aggregate, rank, or explain, subject to declared preconditions. **Boundary:** shared operator names do not imply shared domain semantics. **Sources:** OCSRE-004/006, SPEC-002.

### DEF-024 — Object Plugin
A versioned, contract-bound extension that supplies domain-specific metric interpretation, transformation, inference, validation, or capability behavior to an Object-Centric workflow. **Boundary:** plugin installation ≠ semantic correctness, runtime safety, or permission to execute actions. **Sources:** OCSRE-005, SPEC-004.

### DEF-025 — Capability / Capability Contract
A declared ability to perform a task or transformation with typed inputs/outputs, preconditions, dependencies, permissions, failure modes, and test evidence. **Boundary:** callable function ≠ verified useful capability; advertised scope ≠ demonstrated scope. **Sources:** SPEC-004, OCSRE-011, CASE-005.

### DEF-026 — SQL-to-WE Adaptation
A governed mapping from SQL records and queries into typed WE/Object representations and operations, preserving declared identity, SQL semantics, provenance, granularity, time, and security. **Boundary:** row-to-object conversion alone is insufficient. **Sources:** OCSRE-006, CASE-002, OCSH-007.

### DEF-027 — Attribute Transformation Pipeline
A sequence of **Bucketize**, **Normalize**, **Combine**, **Encode**, and **Derive** operations, each with an explicit type, lineage, and semantics contract. **Boundary:** transformation must not silently convert NULL to false, duplicate counts after joins, or leak protected rows. **Sources:** OCSRE-006, CASE-002.

## 6. Reasoning, evidence, and epistemic status

### DEF-028 — Classical Deductive Preservation
The proposed property that a precisely restricted object-centric formal fragment preserves the valid entailments and non-entailments of its declared classical reference logic. **Boundary:** does not assert preservation for all natural-language, defeasible, probabilistic, or temporal reasoning. **Sources:** OCSRE-002, SPEC-003, CASE-001, OCSH-001.

### DEF-029 — Entailment / Proof Trace
An entailment is a conclusion that follows under an explicit formal semantics from premises; a proof trace records the inference steps and their dependencies. **Boundary:** logical validity ≠ factual truth of premises or authorization to act. **Sources:** SPEC-003, CASE-001, EXT-001.

### DEF-030 — Evidence Item / EvidenceRef
A source-qualified observation, report, computation, or artifact used to support or challenge a claim, with provenance, time, scope, and reliability qualifiers. **Boundary:** evidence ≠ proof, policy authority, or a committed world-state fact. **Sources:** OCSRE-009, SPEC-005, CASE-004.

### DEF-031 — Claim / Hypothesis
A proposition or explanatory candidate with explicit scope and epistemic status, potentially supported, contradicted, revised, or unresolved. **Boundary:** hypothesis confidence ≠ formal entailment; an OCSH research hypothesis ≠ an individual domain hypothesis. **Sources:** OCSRE-009, HYPOTHESIS-REGISTRY, CASE-004.

### DEF-032 — Directional Weak Evidence
Partial, context-dependent evidence that may shift relative support among competing hypotheses without establishing identity or causality. Correlated observations must not be naively double-counted. **Boundary:** combined weak signals ≠ guaranteed identification. **Sources:** CASE-004, OCSRE-009; conceptual relation to BM-ODWEI.

### DEF-033 — Epistemic Separation
The governance principle that deductive validity, observational support, metric similarity, probability, utility, and authorization are distinct kinds of judgment with distinct evidence and decision rules. **Boundary:** no automatic promotion between categories. **Sources:** OCSRE-009, SPEC-005, EXT-001.

### DEF-034 — In-Situ Object Learning
A proposed feedback-driven learning process tied to identified objects, versions, observations, decisions, and provenance, with controlled revisions. **Boundary:** incorporating feedback ≠ silently changing authoritative state or proving improved task performance. **Sources:** OCSRE-007, SPEC-005, OCSH-004.

### DEF-035 — Feedback Record
A provenance-bearing report about an observation, outcome, correction, or evaluation, associated with relevant object and state references. **Boundary:** a report may be disputed, stale, or unauthorized; it is not automatically ground truth. **Sources:** SPEC-005, OCSRE-007.

### DEF-036 — Explicit Leftover / Residual
A named unresolved requirement, ambiguity, failed case, missing evidence, or deferred design decision that remains visible to future work. **Boundary:** a leftover is not a completed feature; documenting it does not resolve it. **Sources:** all SPECs, `UNRESOLVED-RESIDUALS.md` (planned).

## 7. CDE, state evolution, and governance

### DEF-037 — CDE (Constrained Delta Evolution)
A proposed family of constrained state-evolution/search methods using state containers, typed candidate deltas, validation, path memory, and governed transitions. In SIF, CDE is proposed as a major **evolutionary localization** method. **Boundary:** CDE is not equivalent to a metric differential or a particular conventional search algorithm. **Sources:** OCSRE-008, SPEC-006, EXT-002; companion CDE research.

### DEF-038 — State-Container
A typed container of object/state references, relations, constraints, provenance, and permitted transition semantics, possibly spanning a composite system. **Boundary:** a container is not necessarily a database transaction or a mutable global singleton. **Sources:** OCSRE-008, SPEC-006, CASE-003.

### DEF-039 — Typed Delta (CDE)
A proposed state transition operation with explicit input state, target objects, preconditions, effect semantics, invariant checks, and rollback or rejection behavior. **Boundary:** CDE Delta ≠ ODK metric delta; proposed Delta ≠ authorized commit. **Sources:** SPEC-006, CASE-003/004/006.

### DEF-040 — Candidate State / Committed State
A **candidate state** is a proposed outcome of one or more transitions; a **committed state** is accepted by the relevant authoritative process after validation and authorization. **Boundary:** a high-scoring candidate cannot bypass invariant checks or approval. **Sources:** SPEC-001/006, CASE-003/006.

### DEF-041 — Invariant / Constraint
A condition that must hold for a state or transition to be valid within a specified scope, such as capacity, temporal feasibility, access control, or consistency. **Boundary:** optimization objectives are not automatically hard constraints; feasibility ≠ optimality. **Sources:** SPEC-006, CASE-003.

### DEF-042 — M→N Dynamic Branching
An adaptive candidate-generation/search structure in which a set of current states or branches may produce a variable number of successor candidates, under declared resource and validity constraints. **Boundary:** branch count alone does not imply useful exploration. **Sources:** OCSRE-008, EXT-003, companion CDE.

### DEF-043 — Path Memory / Non-Reuse Constraint
A record of applied or rejected transition signatures along a search path, used to enforce declared no-repeat or no-reuse rules. **Boundary:** identical textual Delta labels may differ in context; path constraints must declare equivalence semantics. **Sources:** SPEC-006, CASE-003.

### DEF-044 — NoSubtree / Loop-Back Control
Governance mechanisms for excluding invalid candidate regions and bounding repeated or cyclic exploration. **Boundary:** pruning must be justified by a sound rule for its declared scope; loop-back may be allowed only with explicit controls. **Sources:** OCSRE-008, SPEC-006.

### DEF-045 — Control Plane / Authorization Boundary
The governing interface that evaluates policies and grants or denies transitions such as promotion, mutation, deployment, or relay acceptance. **Boundary:** evidence, agent consensus, model confidence, and passing tests are not themselves authorization. **Sources:** OCSRE-009/010, SPEC-005/006, CASE-006.

## 8. Localization, multi-agent systems, and relay

### DEF-046 — SIF (Structural Intelligence Framework)
A broader framework organizing problem–capability mapping, localization/addressing, node intelligence, and control/governance. OCSRE is proposed as an interoperable object-centric contribution, not a replacement for SIF. **Sources:** OCSRE-010, EXT-002.

### DEF-047 — Localization / Addressing
A typed process of finding or generating an appropriate reference, capability, evidence source, state, or action path under context and constraints. **Boundary:** locating a representation ≠ proving entity identity or authorizing an action. **Sources:** OCSRE-010, EXT-002.

### DEF-048 — Referential Localization
Locating an already represented entity, state, metric, evidence item, relation, or capability through a declared addressing mechanism. **Boundary:** retrieval does not prove semantic correctness. **Sources:** EXT-002.

### DEF-049 — Evolutionary Localization
Searching for a valid yet not necessarily pre-existing state or transition path, including CDE-based candidate generation and validation. **Boundary:** finding a candidate ≠ demonstrating optimality or authorizing execution. **Sources:** EXT-002, OCSRE-008.

### DEF-050 — UTN / MDT / WE-HDT Interface Relation
UTN, Metric Differential Tree (MDT), and WE-HDT are distinct proposed structural addressing, indexing, or representation mechanisms that may interoperate through ObjectRef and typed contracts. **Boundary:** shared interface ≠ algorithmic equivalence, interchangeable guarantees, or common implementation. **Sources:** OCSRE-010, EXT-002, CASE-006.

### DEF-051 — Agent Role / Independent Validator
An Agent Role declares permitted contributions (generate, challenge, verify, audit, authorize only if separately empowered). An **independent validator** evaluates a candidate under a sufficiently separated process and evidence path. **Boundary:** multiple agreeing agents are not independent validation by default. **Sources:** EXT-003, CASE-005/006.

### DEF-052 — Relay Artifact
A portable, versioned package of capability, contracts, dependency bindings, test evidence, provenance, negative cases, scope limits, and unresolved residuals. **Boundary:** portability ≠ accepted deployment or successful target-domain transfer. **Sources:** OCSRE-011, SPEC-004/006, EXT-003.

### DEF-053 — Capability Relay
A governed process for transferring or adapting a capability between tasks, agents, systems, or domains with target-side conformance and independent evaluation. **Boundary:** copying code or reusing an API does not by itself establish semantic transfer. **Sources:** OCSRE-011, CASE-005, OCSH-008.

### DEF-054 — Collective Structural Learning
Accumulation and revision of validated structural artifacts, including reusable successes, failures, counterexamples, dependencies, and leftovers across participants or runs. **Boundary:** growing artifact count ≠ growing intelligence. **Sources:** OCSRE-011/012, EXT-003/005.

### DEF-055 — Competitive Relay / Strategy Candidate
Multiple alternative, potentially conflicting capability or action proposals evaluated against common constraints and distinct perspectives before promotion. **Boundary:** winning a score contest ≠ policy compliance or empirical superiority. **Sources:** EXT-003; conceptual relation to SSICR.

## 9. Open-ended evolution, spillover, and scaling

### DEF-056 — Metric Evolution
Governed generation, refinement, or retirement of metrics with semantic versioning, independent assessment, and anti-gaming safeguards. **Boundary:** optimizing a self-created metric does not establish external utility. **Sources:** EXT-004.

### DEF-057 — Plugin Evolution
Governed generation, composition, specialization, replacement, or retirement of Object Plugins, preserving dependency and conformance traces. **Boundary:** new plugin ≠ new verified capability. **Sources:** EXT-004, SPEC-004.

### DEF-058 — Policy Evolution
A controlled process for proposing and reviewing policy changes with separate authorization and rollback rules. **Boundary:** an agent may propose a policy change but MUST NOT grant itself permission by changing its own evaluator. **Sources:** EXT-004, SPEC-005/006.

### DEF-059 — Structural Capability Spillover
A hypothesized benefit of a structural capability outside its original target scope, established only through predeclared independent tasks, suitable controls, and resource-accounted evaluation. **Boundary:** planned cross-domain reuse ≠ untargeted spillover. **Sources:** OCSRE-011/012, EXT-005, OCSH-009.

### DEF-060 — Structural Scaling Hypothesis
A falsifiable claim that accumulated, interoperable, validated structural capabilities produce repeatable growth in independently measured useful performance as resources or capability stock vary. **Boundary:** no scaling law is demonstrated by this repository; a rising number of documents, plugins, or agents is insufficient. **Sources:** EXT-005, OCSH-010.

### DEF-061 — Untargeted Task
A task frozen before a capability or evaluation policy is developed, and not used to tune that capability, serving as a test of non-directed generalization. **Boundary:** a retrospectively chosen success is not a clean untargeted-task test. **Sources:** EXT-005.

## 10. Code governance and software objects

### DEF-062 — Calling Graph
A typed directed graph of potential function or procedure invocation relationships within a declared program version and analysis scope. **Boundary:** unchanged calling edges ≠ unchanged behavior, security, data flow, or configuration. **Sources:** CASE-006, OCSRE-010.

### DEF-063 — Multi-Graph Code Dependency View
A composite model integrating calling relationships with data flow, control dependencies, schemas, configuration, permissions, tests, and deployment dependencies where available. **Boundary:** static graph coverage is incomplete unless declared; unknown edges remain explicit. **Sources:** CASE-006.

### DEF-064 — Change Impact Localization
A contract-governed process for identifying potentially affected software objects, tests, invariants, and security boundaries after a proposed code Delta. **Boundary:** impact localization is a hypothesis about affected scope, not a proof of absence of other effects. **Sources:** CASE-006, OCSH-011.

### DEF-065 — Code Change Governance State
The status of a proposed change as generated, analyzed, tested, security-reviewed, authorized, merged, deployed, or rolled back, with distinct gates. **Boundary:** a passing test or AI-generated explanation is not approval to merge or deploy. **Sources:** CASE-006, SPEC-005/006.

## 11. Critical non-equivalences and forbidden inference shortcuts

| Pair | Must remain distinct | Failure if collapsed |
|---|---|---|
| WE vs SQL row | Entity vs source record | Duplicate or mistaken identity |
| ObjectRef vs IdentityRef | Contextual access vs identity reference | False attribution |
| Identity vs metric similarity | Referential vs comparative | Mistaken actor merge |
| Perspective vs truth | Viewpoint vs fact | Biased claim promotion |
| State version vs event time | Revision vs world chronology | Temporal leakage |
| Member vs composite | Local vs global granularity | Invalid inherited property |
| NULL vs false vs redacted | Different missingness/logic | Incorrect SQL semantics or disclosure |
| ODK metric delta vs CDE typed Delta | Measurement vs transition | Unauthorized mutation |
| Candidate vs committed | Proposed vs authoritative | Premature deployment |
| Evidence vs proof | Support vs entailment | Unsupported certainty |
| Proof vs authorization | Logical vs governance | Unsafe action |
| Plugin availability vs capability validation | Callable vs demonstrated | Invalid relay |
| Calling Graph vs full behavior | One dependency surface vs semantics | Missed security regression |
| Relay reuse vs spillover | Directed reuse vs untargeted gain | Inflated generalization claim |
| Capability count vs scaling | Inventory vs performance law | Unsupported Scaling Law |

## 12. Cross-document dependency map

| Topic | Primary contract | Research paper(s) | Case(s) / extension(s) | Hypothesis |
|---|---|---|---|---|
| Identity, state, perspective | SPEC-001 | OCSRE-001/003 | CASE-001/004; EXT-002 | OCSH-006 |
| ODK, metric projection | SPEC-002 | OCSRE-004 | CASE-002/005; EXT-004 | OCSH-002 |
| Classical logic, granularity | SPEC-003 | OCSRE-002/003 | CASE-001; EXT-001 | OCSH-001/006 |
| Plugin, capability transfer | SPEC-004 | OCSRE-005/011 | CASE-005; EXT-003/004 | OCSH-003/008 |
| In-situ evidence, learning | SPEC-005 | OCSRE-007/009 | CASE-004/006 | OCSH-004 |
| CDE and composite states | SPEC-006 | OCSRE-008 | CASE-003/004/006; EXT-002 | OCSH-005 |
| SQL adaptation | SPEC-001/002/004/005 | OCSRE-006 | CASE-002 | OCSH-007 |
| Localization and code governance | SPEC-001/005/006 | OCSRE-010 | CASE-006; EXT-002 | OCSH-011 |
| Spillover and scaling | SPEC-004/006 | OCSRE-011/012 | CASE-005; EXT-005 | OCSH-008/009/010 |

These mappings identify research surfaces; they do not assert all listed contracts already pass or that cross-document semantics have been formally reconciled.

## 13. Illustrative semantic checks

**Check A — identity.** Two wallets share a timestamp and amount distribution. Their metric vectors may be similar; the identity resolver must not merge their owners without independent identity evidence and an authorized rule.

**Check B — SQL.** A LEFT JOIN produces NULL for a missing matching record. A transformer must not silently encode that NULL as `FALSE` or as a numeric zero without an explicit, versioned interpretation contract.

**Check C — composite.** A fleet's average occupancy is 80%. This does not entail that each bus is at 80% occupancy; individual capacity constraints must be checked independently.

**Check D — differential.** The proposed schedule reduces required vehicles from three to two in a synthetic fixture. The metric delta is `-1 vehicle`; a CDE typed Delta is the actual candidate reassignment operation. The metric result does not authorize deployment.

**Check E — code.** A function call graph is unchanged after an AI edit, but a tenant-scoped authorization cache becomes global. The Calling Graph is insufficient to establish safety; data-flow, policy, and negative security tests are necessary.

**Check F — scaling.** Ten new plugins are added and six are reused. Neither count alone demonstrates spillover or scaling; independently held-out task gains and total resource costs must be reported.

## 14. Definition governance and conformance checklist

A new or revised research artifact SHOULD:

1. Identify the canonical DEF IDs for core terms it uses.
2. State whether a reference denotes identity, view, address, state, or hypothesis.
3. Declare type, granularity, perspective, time, provenance, and permission where relevant.
4. Distinguish measured metric deltas from state-transition deltas.
5. Preserve the boundary between proposal, validation, authorization, and commitment.
6. Provide negative examples for any semantic coercion or cross-domain mapping.
7. Record unknowns and failures rather than inventing a default meaning.
8. Link falsifiable claims to `HYPOTHESIS-REGISTRY.md` and supporting evidence IDs.
9. Route material changes through `DECISION-LOG.md` and unresolved issues through `UNRESOLVED-RESIDUALS.md`.
10. Avoid claiming that a written contract, worked example, or agent consensus constitutes empirical validation.

### Proposed registry tests (not executed)

| ID | Test | Expected outcome |
|---|---|---|
| DR-P01 | Distinguish WE, Object, ObjectRef, IdentityRef | Distinct semantics retained |
| DR-P02 | Resolve a versioned metric with unit and time | Qualified metric projection |
| DR-P03 | Compare compatible metrics under one perspective | Typed differential with provenance |
| DR-P04 | Propose CDE transition and validate invariants | Candidate only until authorization |
| DR-P05 | Relay a plugin with full contract and negative tests | Target-side conformance required |
| DR-P06 | Record an E0 hypothesis and proposed experiment | No evidence claim |
| DR-N01 | Equate wallet similarity with actor identity | Reject / unresolved |
| DR-N02 | Treat SQL NULL as FALSE without rule | Reject |
| DR-N03 | Infer every member from group average | Reject |
| DR-N04 | Treat ODK delta as CDE mutation | Reject |
| DR-N05 | Promote agent consensus to formal proof | Reject |
| DR-N06 | Deploy AI code solely on unchanged Calling Graph | Reject |
| DR-N07 | Let an agent self-authorize a policy change | Reject |
| DR-N08 | Claim scaling from artifact count | Reject |

**Status:** all checks are proposed; no executable conformance suite or results are supplied by this registry.

## 15. Explicit leftovers and open decisions

| ID | Unresolved item | Proposed next action |
|---|---|---|
| DLR-001 | Canonical WE-SIO identity schema version | Pin external contract and mapping |
| DLR-002 | ObjectRef wire encoding | Define interoperable serialization |
| DLR-003 | Identity merge/split lineage semantics | Specify audit and revocation cases |
| DLR-004 | Temporal interval model | Test event/valid/observation time axes |
| DLR-005 | Perspective inheritance and conflict | Define precedence and explicit refusal |
| DLR-006 | Metric unit ontology | Choose versioned registry and adapters |
| DLR-007 | Metric missingness vocabulary | Distinguish absent, NULL, redacted, unknown |
| DLR-008 | ODK error/result algebra | Specify typed failure categories |
| DLR-009 | Plugin dependency and capability versioning | Define compatibility and revocation |
| DLR-010 | SQL snapshot/transaction semantics | Add reproducible query fixtures |
| DLR-011 | Cross-granularity proof obligations | Build formal counterexample suite |
| DLR-012 | Evidence confidence calibration | Define independent evaluation |
| DLR-013 | Weak-evidence dependence handling | Prevent correlated evidence inflation |
| DLR-014 | CDE Delta equivalence on paths | Specify context-sensitive signatures |
| DLR-015 | Composite rollback semantics | Test partial-failure recovery |
| DLR-016 | Soundness of NoSubtree pruning | State admissible pruning conditions |
| DLR-017 | Referential vs evolutionary localization API | Define SIF integration contract |
| DLR-018 | UTN/MDT/WE-HDT adapter compatibility | Compare supported guarantees |
| DLR-019 | Independent multi-agent validation criteria | Define reviewer separation |
| DLR-020 | Relay artifact minimum evidence | Define acceptance profile |
| DLR-021 | Policy evolution authority separation | Add adversarial conformance tests |
| DLR-022 | Held-out spillover task design | Preregister task families |
| DLR-023 | Scaling cost accounting and horizon | Specify longitudinal protocol |
| DLR-024 | Calling Graph coverage and unknown edges | Document static/dynamic limits |

These are unresolved research and engineering questions, not hidden implementation commitments. On creation of `UNRESOLVED-RESIDUALS.md`, cross-link these IDs rather than silently marking them complete.

## 16. Maintenance procedure and companion registries

The registry is maintained alongside:

- `HYPOTHESIS-REGISTRY.md` — OCSH-001–011, test status, falsification criteria, evidence IDs.
- `COUNTEREXAMPLE-REGISTRY.md` — cases that challenge definitions, inference shortcuts, and transfer claims.
- `DECISION-LOG.md` — definition choices, rejected alternatives, reasons, and change history.
- `UNRESOLVED-RESIDUALS.md` — explicit leftover ownership, blockers, and closure criteria.
- `GLOSSARY.md` — reader-facing concise terminology; this registry is the more precise, traceable source.

**Proposed change procedure:** submit a definition change with affected DEF IDs and files → evaluate semantic compatibility and security implications → attach positive and negative fixtures → document decision → update references and release notes → assign evidence and review status. In case of conflict with an authoritative SPEC, revise through the specification's own governance process first.

## 17. Closing position

OCSRE's unification claim is **interoperability through explicit, typed, versioned contracts**, not the erasure of distinctions between identities, metrics, logical proofs, evidence, transitions, capabilities, or authorization. A useful definition registry makes those distinctions visible, testable, and revisable. The definitions in this file provide a proposed common language for research and future conformance work; they do not establish that OCSRE has been implemented, validated, or shown to scale.
