# GLOSSARY — Object-Centric Structural Reasoning and Evolution (OCSRE)

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Version:** v1.0.0 — Research Framework and Contracts  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**License:** Apache-2.0  
**Canonical location:** `GLOSSARY.md`  
**Status:** Reader-facing terminology guide; proposed research framework, not an implementation certification

## Purpose and reading rules

This glossary provides a concise, accessible entry point to OCSRE's terminology. It follows the 65 stable identifiers in [`research-trace/DEFINITION-REGISTRY.md`](research-trace/DEFINITION-REGISTRY.md), but **is not a replacement for the full definitions or the normative interface contracts**. For exact semantics, exceptions, and revision history, follow the definition registry and the governing document in `specs/`. Terms from WE-SIO, SIF, UTN, MDT, WE-HDT, CDE, UIERU and related projects retain their original framework authority.

A definition describes a proposed concept or interface; it does not claim that an operational implementation exists. All OCSH-001–011 research hypotheses remain **E0 — Proposed** pending validation. In particular, do not treat a metric as proof, a candidate as an authorized action, or a transferred component as validated cross-domain intelligence.

**Notation.** `Object[metricIndices]` denotes a metric-indexed view of an object, not a universal executable data type. `Δ` denotes a difference or transition *only as qualified by its type*: ODK differential and CDE Typed Delta have distinct meanings. `WE` means World Entity; `OCSRE` means Object-Centric Structural Reasoning and Evolution.


## Foundations: entities, identity, and object views

### DEF-001 — World Entity (WE)

A **World Entity** is an entity represented under the WE ecosystem's identity and structural semantics, potentially exposing typed attributes, relations, temporal states, perspectives, evidence, and permissions. **Boundary:** a WE is not simply a SQL row, an address, a metric vector, or an LLM token. OCSRE uses WE-compatible interfaces; it does not redefine the external WE-SIO…

**Read more:** [`DEF-001` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-001--world-entity-we).

### DEF-002 — Object (OCSRE usage)

An **Object** is a typed, contextual computational or reasoning view of a WE or an explicitly modeled composite, accessible through declared contracts. An Object is not necessarily an independently persistent entity and does not guarantee visibility of every WE attribute. **Boundary:** representation/view ≠ underlying entity. **Sources:** OCSRE-001/004, SPEC-001.

**Read more:** [`DEF-002` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-002--object-ocsre-usage).

### DEF-003 — ObjectRef

A **typed reference** that resolves to an Object view under an identity namespace, type, state, temporal scope, perspective, and access context. Resolution may fail, be ambiguous, or return a provisional identity. **Boundary:** ObjectRef ≠ proof of real-world identity, permission to mutate, or unique physical storage location. **Sources:** SPEC-001, OCSRE-010, EXT-002.

**Read more:** [`DEF-003` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-003--objectref).

### DEF-004 — IdentityRef

A namespace-qualified reference to an entity identity, with declared type, resolution status, and optional lineage. Its continuity is governed by an identity authority and versioned identity rules. **Boundary:** identity ≠ source key, display label, graph address, metric similarity, or shared ownership. **Sources:** SPEC-001, CASE-001/004.

**Read more:** [`DEF-004` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-004--identityref).

### DEF-005 — Identity Resolution

A provenance-bearing process for mapping candidate records, aliases, or references to a resolved, provisional, ambiguous, or unresolved entity identity. Merge/split/reidentification events require auditability. **Boundary:** resolution hypothesis ≠ verified actor attribution. **Sources:** SPEC-001, CASE-004.

**Read more:** [`DEF-005` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-005--identity-resolution).

### DEF-006 — TypeRef

A versioned ontology/schema reference specifying an object's admissible attributes, relations, and operations. Compatibility requires explicit mapping or subtype rules. **Boundary:** same label ≠ compatible type. **Sources:** SPEC-001/004.

**Read more:** [`DEF-006` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-006--typeref).

### DEF-007 — ObjectView

A permission-scoped computational view that may include `identity`, `type_ref`, `state`, `perspective`, typed attributes, relations, evidence, permissions, and provenance. **Boundary:** a view is not a guarantee that all fields are stored together or disclosed to the caller. **Sources:** SPEC-001.

**Read more:** [`DEF-007` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-007--objectview).

### DEF-008 — Composite WE / Composite Object

A structured aggregate of multiple typed entities and relations with an explicit membership model and potentially global constraints. Membership and identity-continuity rules are domain-specific. **Boundary:** membership ≠ ownership; aggregate properties do not automatically distribute to members. **Sources:** OCSRE-008, SPEC-006, CASE-003/004.

**Read more:** [`DEF-008` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-008--composite-we--composite-object).

### DEF-009 — Compositional Identity Hypothesis

A defeasible proposal that multiple observed accounts, addresses, events, or components participate in one controlling or functional actor structure. It carries evidence, competing alternatives, uncertainty, and revision history. **Boundary:** transaction connectivity ≠ proof of common real-world control. **Sources:** CASE-004, OCSRE-009.

**Read more:** [`DEF-009` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-009--compositional-identity-hypothesis).


## Perspective, state, time, and granularity

### DEF-010 — Perspective / PerspectiveRef

A versioned interpretive or evaluative standpoint that determines which metrics, goals, evidence rules, or policies apply. **Boundary:** perspective ≠ objective truth, authorization, or identity. **Sources:** OCSRE-003, SPEC-001/002.

**Read more:** [`DEF-010` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-010--perspective--perspectiveref).

### DEF-011 — State / StateSnapshot

A typed representation of an entity or composite at a declared version and temporal scope. A snapshot may be observed, simulated, candidate, or committed; these statuses are not interchangeable. **Boundary:** state ≠ identity; version order ≠ event-time order. **Sources:** SPEC-001/006, OCSRE-008.

**Read more:** [`DEF-011` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-011--state--statesnapshot).

### DEF-012 — StateRef

A reference to a versioned state or snapshot, carrying the identity, snapshot/version identifier, and sufficient scope to distinguish historical from candidate or current state. **Boundary:** a StateRef is not a write capability. **Sources:** SPEC-001/006.

**Read more:** [`DEF-012` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-012--stateref).

### DEF-013 — Temporal Scope

The declared valid-time, event-time, observation-time, processing-time, or transaction snapshot boundaries of a statement or measurement. Alignment across time axes must be explicit. **Boundary:** observations at different times cannot be silently compared as simultaneous facts. **Sources:** OCSRE-003/006, CASE-002.

**Read more:** [`DEF-013` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-013--temporal-scope).

### DEF-014 — Granularity

The level at which an entity, fact, metric, or decision is defined: individual, event, trip, route, group, fleet, system, etc. **Boundary:** group-to-member inheritance and member-to-group aggregation require explicit rules. **Sources:** OCSRE-003, SPEC-003, CASE-001/003.

**Read more:** [`DEF-014` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-014--granularity).

### DEF-015 — Cross-Granularity Contract

A rule that declares when a relation, predicate, metric, or constraint may be lifted, projected, aggregated, or inherited between granularities, including loss and exception conditions. **Boundary:** no automatic inference from aggregate averages to each constituent. **Sources:** SPEC-001/003, OCSH-006.

**Read more:** [`DEF-015` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-015--cross-granularity-contract).

### DEF-016 — Typed Attribute / Typed Relation

An attribute or relation whose domain, range, cardinality, temporal validity, perspective, provenance, and access constraints are declared. **Boundary:** same textual field name ≠ same semantic relation. **Sources:** SPEC-001, OCSRE-003.

**Read more:** [`DEF-016` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-016--typed-attribute--typed-relation).


## Metrics, ODK, plugins, and SQL adaptation

### DEF-017 — Metric

A typed, versioned measurement or derived evaluation with declared unit, scale, granularity, temporal scope, provenance, perspective, and missingness semantics. **Boundary:** metric ≠ proof, causal explanation, identity, or authorization. **Sources:** OCSRE-004, SPEC-002.

**Read more:** [`DEF-017` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-017--metric).

### DEF-018 — Metric Index / `metricIndices`

A typed selector identifying a registered metric or derivation in a metric schema. It is not necessarily a numeric array index. **Boundary:** a selector does not guarantee that every Object supports the metric. **Sources:** OCSRE-004, SPEC-002.

**Read more:** [`DEF-018` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-018--metric-index--metricindices).

### DEF-019 — `Object[metricIndices]`

A conceptual typed metric projection of an Object under a declared context: `Project(ObjectRef, metricIndices, context)`. The result contains qualified values and their metadata. **Boundary:** projection ≠ bare vector; similarity of projections ≠ identity equivalence. **Sources:** OCSRE-004, SPEC-002.

**Read more:** [`DEF-019` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-019--objectmetricindices).

### DEF-020 — Object Differential Kernel (ODK)

A proposed common computation interface that governs metric selection, compatibility/alignment, comparison or differential operations, qualification, and explanation while delegating domain meaning to explicit plugins. **Boundary:** generic execution discipline ≠ universal semantic equivalence or demonstrated kernel implementation. **Sources:** OCSRE-004, SPEC-002.

**Read more:** [`DEF-020` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-020--object-differential-kernel-odk).

### DEF-021 — Differential / Metric Delta

A typed, context-qualified difference between compatible measurements, including direction, units, uncertainty, provenance, and interpretation constraints. **Boundary:** a metric difference is not a CDE state-transition Delta, causal claim, or automatically valid decision. **Sources:** OCSRE-004, SPEC-002/006.

**Read more:** [`DEF-021` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-021--differential--metric-delta).

### DEF-022 — Semantic Alignment

A contract-governed operation establishing comparability across types, units, scales, times, perspectives, granularities, missingness, and access contexts. It may refuse comparison. **Boundary:** unit conversion alone is not full semantic alignment. **Sources:** SPEC-002, CASE-002/005.

**Read more:** [`DEF-022` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-022--semantic-alignment).

### DEF-023 — Generic Operator

A typed computation such as select, align, compare, normalize, bucketize, combine, aggregate, rank, or explain, subject to declared preconditions. **Boundary:** shared operator names do not imply shared domain semantics. **Sources:** OCSRE-004/006, SPEC-002.

**Read more:** [`DEF-023` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-023--generic-operator).

### DEF-024 — Object Plugin

A versioned, contract-bound extension that supplies domain-specific metric interpretation, transformation, inference, validation, or capability behavior to an Object-Centric workflow. **Boundary:** plugin installation ≠ semantic correctness, runtime safety, or permission to execute actions. **Sources:** OCSRE-005, SPEC-004.

**Read more:** [`DEF-024` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-024--object-plugin).

### DEF-025 — Capability / Capability Contract

A declared ability to perform a task or transformation with typed inputs/outputs, preconditions, dependencies, permissions, failure modes, and test evidence. **Boundary:** callable function ≠ verified useful capability; advertised scope ≠ demonstrated scope. **Sources:** SPEC-004, OCSRE-011, CASE-005.

**Read more:** [`DEF-025` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-025--capability--capability-contract).

### DEF-026 — SQL-to-WE Adaptation

A governed mapping from SQL records and queries into typed WE/Object representations and operations, preserving declared identity, SQL semantics, provenance, granularity, time, and security. **Boundary:** row-to-object conversion alone is insufficient. **Sources:** OCSRE-006, CASE-002, OCSH-007.

**Read more:** [`DEF-026` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-026--sql-to-we-adaptation).

### DEF-027 — Attribute Transformation Pipeline

A sequence of **Bucketize**, **Normalize**, **Combine**, **Encode**, and **Derive** operations, each with an explicit type, lineage, and semantics contract. **Boundary:** transformation must not silently convert NULL to false, duplicate counts after joins, or leak protected rows. **Sources:** OCSRE-006, CASE-002.

**Read more:** [`DEF-027` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-027--attribute-transformation-pipeline).


## Reasoning, evidence, and in-situ learning

### DEF-028 — Classical Deductive Preservation

The proposed property that a precisely restricted object-centric formal fragment preserves the valid entailments and non-entailments of its declared classical reference logic. **Boundary:** does not assert preservation for all natural-language, defeasible, probabilistic, or temporal reasoning. **Sources:** OCSRE-002, SPEC-003, CASE-001, OCSH-001.

**Read more:** [`DEF-028` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-028--classical-deductive-preservation).

### DEF-029 — Entailment / Proof Trace

An entailment is a conclusion that follows under an explicit formal semantics from premises; a proof trace records the inference steps and their dependencies. **Boundary:** logical validity ≠ factual truth of premises or authorization to act. **Sources:** SPEC-003, CASE-001, EXT-001.

**Read more:** [`DEF-029` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-029--entailment--proof-trace).

### DEF-030 — Evidence Item / EvidenceRef

A source-qualified observation, report, computation, or artifact used to support or challenge a claim, with provenance, time, scope, and reliability qualifiers. **Boundary:** evidence ≠ proof, policy authority, or a committed world-state fact. **Sources:** OCSRE-009, SPEC-005, CASE-004.

**Read more:** [`DEF-030` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-030--evidence-item--evidenceref).

### DEF-031 — Claim / Hypothesis

A proposition or explanatory candidate with explicit scope and epistemic status, potentially supported, contradicted, revised, or unresolved. **Boundary:** hypothesis confidence ≠ formal entailment; an OCSH research hypothesis ≠ an individual domain hypothesis. **Sources:** OCSRE-009, HYPOTHESIS-REGISTRY, CASE-004.

**Read more:** [`DEF-031` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-031--claim--hypothesis).

### DEF-032 — Directional Weak Evidence

Partial, context-dependent evidence that may shift relative support among competing hypotheses without establishing identity or causality. Correlated observations must not be naively double-counted. **Boundary:** combined weak signals ≠ guaranteed identification. **Sources:** CASE-004, OCSRE-009; conceptual relation to BM-ODWEI.

**Read more:** [`DEF-032` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-032--directional-weak-evidence).

### DEF-033 — Epistemic Separation

The governance principle that deductive validity, observational support, metric similarity, probability, utility, and authorization are distinct kinds of judgment with distinct evidence and decision rules. **Boundary:** no automatic promotion between categories. **Sources:** OCSRE-009, SPEC-005, EXT-001.

**Read more:** [`DEF-033` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-033--epistemic-separation).

### DEF-034 — In-Situ Object Learning

A proposed feedback-driven learning process tied to identified objects, versions, observations, decisions, and provenance, with controlled revisions. **Boundary:** incorporating feedback ≠ silently changing authoritative state or proving improved task performance. **Sources:** OCSRE-007, SPEC-005, OCSH-004.

**Read more:** [`DEF-034` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-034--in-situ-object-learning).

### DEF-035 — Feedback Record

A provenance-bearing report about an observation, outcome, correction, or evaluation, associated with relevant object and state references. **Boundary:** a report may be disputed, stale, or unauthorized; it is not automatically ground truth. **Sources:** SPEC-005, OCSRE-007.

**Read more:** [`DEF-035` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-035--feedback-record).

### DEF-036 — Explicit Leftover / Residual

A named unresolved requirement, ambiguity, failed case, missing evidence, or deferred design decision that remains visible to future work. **Boundary:** a leftover is not a completed feature; documenting it does not resolve it. **Sources:** all SPECs, `UNRESOLVED-RESIDUALS.md`.

**Read more:** [`DEF-036` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-036--explicit-leftover--residual).


## CDE, composite state, and governance

### DEF-037 — CDE (Constrained Delta Evolution)

A proposed family of constrained state-evolution/search methods using state containers, typed candidate deltas, validation, path memory, and governed transitions. In SIF, CDE is proposed as a major **evolutionary localization** method. **Boundary:** CDE is not equivalent to a metric differential or a particular conventional search algorithm. **Sources:** OCSRE-008, SPEC-006,…

**Read more:** [`DEF-037` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-037--cde-constrained-delta-evolution).

### DEF-038 — State-Container

A typed container of object/state references, relations, constraints, provenance, and permitted transition semantics, possibly spanning a composite system. **Boundary:** a container is not necessarily a database transaction or a mutable global singleton. **Sources:** OCSRE-008, SPEC-006, CASE-003.

**Read more:** [`DEF-038` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-038--state-container).

### DEF-039 — Typed Delta (CDE)

A proposed state transition operation with explicit input state, target objects, preconditions, effect semantics, invariant checks, and rollback or rejection behavior. **Boundary:** CDE Delta ≠ ODK metric delta; proposed Delta ≠ authorized commit. **Sources:** SPEC-006, CASE-003/004/006.

**Read more:** [`DEF-039` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-039--typed-delta-cde).

### DEF-040 — Candidate State / Committed State

A **candidate state** is a proposed outcome of one or more transitions; a **committed state** is accepted by the relevant authoritative process after validation and authorization. **Boundary:** a high-scoring candidate cannot bypass invariant checks or approval. **Sources:** SPEC-001/006, CASE-003/006.

**Read more:** [`DEF-040` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-040--candidate-state--committed-state).

### DEF-041 — Invariant / Constraint

A condition that must hold for a state or transition to be valid within a specified scope, such as capacity, temporal feasibility, access control, or consistency. **Boundary:** optimization objectives are not automatically hard constraints; feasibility ≠ optimality. **Sources:** SPEC-006, CASE-003.

**Read more:** [`DEF-041` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-041--invariant--constraint).

### DEF-042 — M→N Dynamic Branching

An adaptive candidate-generation/search structure in which a set of current states or branches may produce a variable number of successor candidates, under declared resource and validity constraints. **Boundary:** branch count alone does not imply useful exploration. **Sources:** OCSRE-008, EXT-003, companion CDE.

**Read more:** [`DEF-042` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-042--mn-dynamic-branching).

### DEF-043 — Path Memory / Non-Reuse Constraint

A record of applied or rejected transition signatures along a search path, used to enforce declared no-repeat or no-reuse rules. **Boundary:** identical textual Delta labels may differ in context; path constraints must declare equivalence semantics. **Sources:** SPEC-006, CASE-003.

**Read more:** [`DEF-043` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-043--path-memory--non-reuse-constraint).

### DEF-044 — NoSubtree / Loop-Back Control

Governance mechanisms for excluding invalid candidate regions and bounding repeated or cyclic exploration. **Boundary:** pruning must be justified by a sound rule for its declared scope; loop-back may be allowed only with explicit controls. **Sources:** OCSRE-008, SPEC-006.

**Read more:** [`DEF-044` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-044--nosubtree--loop-back-control).

### DEF-045 — Control Plane / Authorization Boundary

The governing interface that evaluates policies and grants or denies transitions such as promotion, mutation, deployment, or relay acceptance. **Boundary:** evidence, agent consensus, model confidence, and passing tests are not themselves authorization. **Sources:** OCSRE-009/010, SPEC-005/006, CASE-006.

**Read more:** [`DEF-045` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-045--control-plane--authorization-boundary).


## SIF localization, agents, and relay

### DEF-046 — SIF (Structural Intelligence Framework)

A broader framework organizing problem–capability mapping, localization/addressing, node intelligence, and control/governance. OCSRE is proposed as an interoperable object-centric contribution, not a replacement for SIF. **Sources:** OCSRE-010, EXT-002.

**Read more:** [`DEF-046` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-046--sif-structural-intelligence-framework).

### DEF-047 — Localization / Addressing

A typed process of finding or generating an appropriate reference, capability, evidence source, state, or action path under context and constraints. **Boundary:** locating a representation ≠ proving entity identity or authorizing an action. **Sources:** OCSRE-010, EXT-002.

**Read more:** [`DEF-047` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-047--localization--addressing).

### DEF-048 — Referential Localization

Locating an already represented entity, state, metric, evidence item, relation, or capability through a declared addressing mechanism. **Boundary:** retrieval does not prove semantic correctness. **Sources:** EXT-002.

**Read more:** [`DEF-048` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-048--referential-localization).

### DEF-049 — Evolutionary Localization

Searching for a valid yet not necessarily pre-existing state or transition path, including CDE-based candidate generation and validation. **Boundary:** finding a candidate ≠ demonstrating optimality or authorizing execution. **Sources:** EXT-002, OCSRE-008.

**Read more:** [`DEF-049` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-049--evolutionary-localization).

### DEF-050 — UTN / MDT / WE-HDT Interface Relation

UTN, Metric Differential Tree (MDT), and WE-HDT are distinct proposed structural addressing, indexing, or representation mechanisms that may interoperate through ObjectRef and typed contracts. **Boundary:** shared interface ≠ algorithmic equivalence, interchangeable guarantees, or common implementation. **Sources:** OCSRE-010, EXT-002, CASE-006.

**Read more:** [`DEF-050` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-050--utn--mdt--we-hdt-interface-relation).

### DEF-051 — Agent Role / Independent Validator

An Agent Role declares permitted contributions (generate, challenge, verify, audit, authorize only if separately empowered). An **independent validator** evaluates a candidate under a sufficiently separated process and evidence path. **Boundary:** multiple agreeing agents are not independent validation by default. **Sources:** EXT-003, CASE-005/006.

**Read more:** [`DEF-051` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-051--agent-role--independent-validator).

### DEF-052 — Relay Artifact

A portable, versioned package of capability, contracts, dependency bindings, test evidence, provenance, negative cases, scope limits, and unresolved residuals. **Boundary:** portability ≠ accepted deployment or successful target-domain transfer. **Sources:** OCSRE-011, SPEC-004/006, EXT-003.

**Read more:** [`DEF-052` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-052--relay-artifact).

### DEF-053 — Capability Relay

A governed process for transferring or adapting a capability between tasks, agents, systems, or domains with target-side conformance and independent evaluation. **Boundary:** copying code or reusing an API does not by itself establish semantic transfer. **Sources:** OCSRE-011, CASE-005, OCSH-008.

**Read more:** [`DEF-053` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-053--capability-relay).

### DEF-054 — Collective Structural Learning

Accumulation and revision of validated structural artifacts, including reusable successes, failures, counterexamples, dependencies, and leftovers across participants or runs. **Boundary:** growing artifact count ≠ growing intelligence. **Sources:** OCSRE-011/012, EXT-003/005.

**Read more:** [`DEF-054` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-054--collective-structural-learning).

### DEF-055 — Competitive Relay / Strategy Candidate

Multiple alternative, potentially conflicting capability or action proposals evaluated against common constraints and distinct perspectives before promotion. **Boundary:** winning a score contest ≠ policy compliance or empirical superiority. **Sources:** EXT-003; conceptual relation to SSICR.

**Read more:** [`DEF-055` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-055--competitive-relay--strategy-candidate).


## Open-ended evolution and scaling

### DEF-056 — Metric Evolution

Governed generation, refinement, or retirement of metrics with semantic versioning, independent assessment, and anti-gaming safeguards. **Boundary:** optimizing a self-created metric does not establish external utility. **Sources:** EXT-004.

**Read more:** [`DEF-056` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-056--metric-evolution).

### DEF-057 — Plugin Evolution

Governed generation, composition, specialization, replacement, or retirement of Object Plugins, preserving dependency and conformance traces. **Boundary:** new plugin ≠ new verified capability. **Sources:** EXT-004, SPEC-004.

**Read more:** [`DEF-057` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-057--plugin-evolution).

### DEF-058 — Policy Evolution

A controlled process for proposing and reviewing policy changes with separate authorization and rollback rules. **Boundary:** an agent may propose a policy change but MUST NOT grant itself permission by changing its own evaluator. **Sources:** EXT-004, SPEC-005/006.

**Read more:** [`DEF-058` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-058--policy-evolution).

### DEF-059 — Structural Capability Spillover

A hypothesized benefit of a structural capability outside its original target scope, established only through predeclared independent tasks, suitable controls, and resource-accounted evaluation. **Boundary:** cross-domain reuse ≠ untargeted spillover. **Sources:** OCSRE-011/012, EXT-005, OCSH-009.

**Read more:** [`DEF-059` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-059--structural-capability-spillover).

### DEF-060 — Structural Scaling Hypothesis

A falsifiable claim that accumulated, interoperable, validated structural capabilities produce repeatable growth in independently measured useful performance as resources or capability stock vary. **Boundary:** no scaling law is demonstrated by this repository; a rising number of documents, plugins, or agents is insufficient. **Sources:** EXT-005, OCSH-010.

**Read more:** [`DEF-060` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-060--structural-scaling-hypothesis).

### DEF-061 — Untargeted Task

A task frozen before a capability or evaluation policy is developed, and not used to tune that capability, serving as a test of non-directed generalization. **Boundary:** a retrospectively chosen success is not a clean untargeted-task test. **Sources:** EXT-005.

**Read more:** [`DEF-061` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-061--untargeted-task).


## AI-generated code governance

### DEF-062 — Calling Graph

A typed directed graph of potential function or procedure invocation relationships within a declared program version and analysis scope. **Boundary:** unchanged calling edges ≠ unchanged behavior, security, data flow, or configuration. **Sources:** CASE-006, OCSRE-010.

**Read more:** [`DEF-062` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-062--calling-graph).

### DEF-063 — Multi-Graph Code Dependency View

A composite model integrating calling relationships with data flow, control dependencies, schemas, configuration, permissions, tests, and deployment dependencies where available. **Boundary:** static graph coverage is incomplete unless declared; unknown edges remain explicit. **Sources:** CASE-006.

**Read more:** [`DEF-063` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-063--multi-graph-code-dependency-view).

### DEF-064 — Change Impact Localization

A contract-governed process for identifying potentially affected software objects, tests, invariants, and security boundaries after a proposed code Delta. **Boundary:** impact localization is a hypothesis about affected scope, not a proof of absence of other effects. **Sources:** CASE-006, OCSH-011.

**Read more:** [`DEF-064` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-064--change-impact-localization).

### DEF-065 — Code Change Governance State

The status of a proposed change as generated, analyzed, tested, security-reviewed, authorized, merged, deployed, or rolled back, with distinct gates. **Boundary:** a passing test or AI-generated explanation is not approval to merge or deploy. **Sources:** CASE-006, SPEC-005/006.

**Read more:** [`DEF-065` in the Definition Registry](research-trace/DEFINITION-REGISTRY.md#def-065--code-change-governance-state).


## Critical distinctions (do not collapse these terms)

| Pair or sequence | Distinction that must be preserved |
|---|---|
| WE / Object / ObjectRef | Entity under WE semantics / OCSRE analytical interface / typed reference to that interface. |
| Identity / representation / similarity | Identity is governed referential continuity; representation and metric proximity are not identity proof. |
| SQL row / WE | A database record does not become a WE without identity, type, temporal, provenance, and authority semantics. |
| Object state / perspective / granularity | A state is contextualized; perspective selects a viewpoint; granularity determines the unit of inference. |
| Metric / evidence / proof | Numerical comparison, defeasible support, and formal entailment have different standards of validity. |
| ODK Differential / CDE Typed Delta | A computed comparison versus a proposed state transition subject to constraints. |
| Candidate / committed state | A proposed state is not an authorized or executed change. |
| Constraint satisfaction / authorization | Feasibility does not confer permission to act. |
| Agent agreement / independent validation | Consensus is not proof and may reflect correlated error. |
| Relay / validated transfer | Packaging or forwarding a capability does not establish semantic correctness in a target domain. |
| Reuse / generalization / spillover / scaling | These are increasingly strong and separately testable claims. |
| Calling Graph / complete code semantics | Call edges alone do not capture data flow, configuration, security policy, or runtime behavior. |

## Commonly used abbreviations

| Abbreviation | Expansion or role |
|---|---|
| OCSRE | Object-Centric Structural Reasoning and Evolution |
| WE | World Entity |
| ODK | Object Differential Kernel |
| CDE | Constrained Delta Evolution |
| SIF | Structural Intelligence Framework |
| UTN | Structural localization/addressing framework interface; consult its source project for its full formal name and semantics |
| MDT | Metric Differential Tree; consult the source project for authoritative details |
| WE-HDT | WE-related hierarchical/differential-tree interface; consult the source project for authoritative details |
| UIERU | Universal Intelligence Evolution and Relay Unit |
| SSICR | Strategic Structural Intelligence and Competitive UIRTU Relay |
| ISGFTR | Intelligence Spillover, Generalization, Fluidity, Transfer and Relay |
| OCSH | OCSRE research hypothesis identifier (`OCSH-001`–`OCSH-011`) |
| SPEC | Proposed specification and contract document |
| CASE | Synthetic or proposed application and adversarial study |
| EXT | Research extension |
| CEX | Counterexample registry record |
| ADR-OCSRE | OCSRE architecture decision record |

## A small worked example: school-bus scheduling

A SQL `Trip` row is imported through a **semantic adapter**, producing a typed WE-compatible object view with a stable identity, a time interval, and a capacity metric. An **Object Plugin** may calculate load ratio for a particular **Perspective**; the **ODK** can compare two load ratios after unit and temporal alignment. Neither the comparison nor a high score proves that a schedule is feasible. A **CDE Typed Delta** may propose reassigning a trip within a **Composite State-Container**; global capacity, timing, and safety constraints must be checked before any **Control Plane** can authorize commitment. A validated, portable optimization component may later become a **Relay Artifact** for a different resource-allocation domain, but target-domain conformance is still required.

Read the progression in [`CASE-002`](cases/CASE-002-SQL-Native-Object-Adaptation.md), [`CASE-003`](cases/CASE-003-School-Bus-Scheduling-and-Composite-WE-State.md), and [`CASE-005`](cases/CASE-005-Cross-Domain-Object-Plugin-Relay.md).

## Navigation and precedence

- **First orientation:** [`README.md`](README.md), [`START-HERE.md`](START-HERE.md), [`CONTENTS.md`](CONTENTS.md).
- **Full definitions:** [`research-trace/DEFINITION-REGISTRY.md`](research-trace/DEFINITION-REGISTRY.md).
- **Hypotheses and evidence levels:** [`research-trace/HYPOTHESIS-REGISTRY.md`](research-trace/HYPOTHESIS-REGISTRY.md).
- **Failures and revisions:** [`research-trace/COUNTEREXAMPLE-REGISTRY.md`](research-trace/COUNTEREXAMPLE-REGISTRY.md), [`research-trace/DECISION-LOG.md`](research-trace/DECISION-LOG.md), [`research-trace/UNRESOLVED-RESIDUALS.md`](research-trace/UNRESOLVED-RESIDUALS.md).
- **Normative contract precedence:** `SPEC-001`–`SPEC-006` govern their respective interfaces; this glossary is explanatory. A conflict should be recorded and resolved explicitly rather than silently reconciled.

## Maintenance protocol

Keep the 65 `DEF` identifiers stable across revisions. New terms should be proposed first in the Definition Registry with sources, boundaries, counterexamples, and relevant contracts; then synchronize this glossary. Record semantic changes in the decision log, affected tests in the counterexample registry, and unresolved ambiguity in the residuals registry. Do not label a claim as empirically supported until evidence has been reviewed under the hypothesis registry's evidence-state rules.

**Guiding principle:** *Unify interfaces where useful; preserve semantic distinctions where necessary; validate before promotion; keep failures and leftovers available for the next relay.*
