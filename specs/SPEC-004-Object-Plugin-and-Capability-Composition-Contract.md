# SPEC-004 — Object Plugin and Capability Composition Contract

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Release target:** v1.0.0 — Research Framework and Contracts  
**Status:** Proposed normative research contract; no runtime or empirical conformance certified  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**License:** Apache-2.0  
**Primary dependencies:** SPEC-001, SPEC-002, SPEC-003; OCSRE-004, OCSRE-005, OCSRE-009, OCSRE-011  
**Primary hypotheses:** OCSH-002, OCSH-003, OCSH-008; secondary OCSH-005, OCSH-007, OCSH-009, OCSH-011

## Abstract

This specification proposes an auditable contract for **Object Plugins** and **composable intelligence capabilities** within Object-Centric Structural Reasoning and Evolution (OCSRE). A common World Entity (WE) interface and Object Differential Kernel (ODK) can expose reusable computation, but neither guarantees domain-semantic compatibility nor grants execution authority. The contract therefore treats plugins as versioned providers of explicitly typed capabilities, each carrying preconditions, postconditions, effect boundaries, evidence rules, permissions, dependency constraints, and conformance tests. It defines capability graph composition, compatibility proofs, uncertainty and provenance propagation, lifecycle governance, sandboxed relay, and negative-transfer accounting. It separates plugin installation from capability invocation, scoring from deduction, learning from state mutation, and local conformance from cross-domain usefulness. The proposal is **Specifications/Contracts First, Conformance Before Runtime, Explicit Leftover**: no implementation, security guarantee, or scaling law is claimed as validated.

**Keywords:** Object Plugin; capability graph; composition contract; World Entity; ODK; WE-native CDE; typed interface; provenance; permissions; structural relay; conformance.

## 1. Purpose and scope

OCSRE-005 introduces the conceptual model `P = (pluginId, version, manifest, capabilities, dependencies, contracts, evidence, governance)` and the notion of a capability as a typed transformation, observation, inference, evaluation, or proposed action. SPEC-004 converts that model into *proposed* conformance obligations. Its intended consumers include domain plugin authors, ODK implementations, WE adapters, reasoning services, learning systems, CDE proposal generators, SIF localization controllers, and UIERU/MLIU relay orchestrators.

The specification governs **interfaces and composition**, not the internals of every algorithm. It does not prescribe a programming language, serialization framework, plugin marketplace, deployment topology, or executable reference implementation. A plugin MAY be implemented by code, a model-backed service, a ruleset, or a hybrid, provided its observable contract can be checked.

The central research question is whether independently developed capabilities can be reused and composed across domains **without modifying the ODK core and without silently weakening semantics, evidence, or authority**.

## 2. Normative language and precedence

**MUST** and **MUST NOT** express mandatory conditions for a future implementation claiming conformance to this proposed specification. **SHOULD** and **SHOULD NOT** express recommendations requiring documented exceptions; **MAY** denotes optional behavior. These terms do not imply external standards certification.

- **SPEC-001** governs WE identity, state/version, perspective, temporal scope, ownership, and permissions.
- **SPEC-002** governs `Object[metricIndices]`, ODK stages, comparator semantics, metric alignment, and differential traces.
- **SPEC-003** governs classical deductive validity and cross-granularity reasoning.
- **SPEC-005** is reserved for in-situ learning, feedback, and epistemic governance.
- **SPEC-006** is reserved for WE-native CDE, composite state, and relay contracts.

Where two contracts apply, the more restrictive applicable semantic or authorization condition prevails. A plugin MUST NOT override an upstream contract through its own manifest.

## 3. Non-equivalence boundaries

A conforming system MUST preserve the following distinctions:

1. **Plugin installed ≠ capability authorized.** Discovery or installation grants no WE read, write, network, or external-action privilege.
2. **Matching schema ≠ matching semantics.** Field names or data types alone do not prove unit, temporal, granularity, or perspective compatibility.
3. **Capability available ≠ capability useful.** A callable component may yield no measurable benefit in a new domain.
4. **Capability composition ≠ proof composition.** Deductive guarantees require valid rule semantics under SPEC-003.
5. **Metric differential ≠ state delta.** ODK comparisons do not directly mutate a CDE State-Container.
6. **Learning revision ≠ committed WE state.** Feedback and model updates are not automatically external actions.
7. **Relay acceptance ≠ cross-domain validation.** A transferred artifact must be tested in its receiving context.
8. **Local success ≠ global constraint satisfaction.** Composite WE constraints must be evaluated at the applicable scope.
9. **Provenance present ≠ evidence independent.** Repackaged or duplicated sources cannot be counted as independent corroboration.
10. **Calling-graph reachability ≠ complete program semantics.** Code governance also needs data/control flow, security contracts, and regression evidence.

## 4. Reference plugin and capability records

### 4.1 Plugin manifest

The following language-neutral record is illustrative; exact machine-readable schemas remain an Explicit Leftover.

```text
PluginManifest {
  pluginId: StableIdentifier
  pluginVersion: VersionIdentifier
  publisher: PrincipalRef
  integrity: ArtifactDigest
  declaredDomains: Set<DomainRef>
  capabilities: Set<CapabilityRef>
  dependencies: Set<VersionConstrainedDependency>
  compatibility: Set<InterfaceVersionRange>
  requestedPermissions: Set<Permission>
  dataHandling: DataPolicyRef
  isolationProfile: IsolationProfileRef
  evidenceBundle: EvidenceBundleRef
  conformanceProfile: ConformanceProfileRef
  lifecycleStatus: proposed | tested | approved | deprecated | revoked
}
```

A manifest MUST be immutable for a given content digest. Reusing the same `(pluginId, pluginVersion)` with changed semantics MUST be rejected or assigned a distinct artifact identity. Publisher identity and integrity metadata are necessary for traceability but do not establish trustworthiness by themselves.

### 4.2 Capability contract

```text
CapabilityContract {
  capabilityId: StableIdentifier
  semanticVersion: VersionIdentifier
  category: representation | transformation | differential |
            reasoning | learning | evolution | governance | relay
  inputTypes: TypedSchema
  outputTypes: TypedSchema
  objectScope: IdentityStatePerspectiveScope
  preconditions: PredicateSet
  postconditions: PredicateSet
  semanticAssumptions: AssumptionSet
  effects: EffectDeclaration
  permissions: PermissionSet
  uncertaintyRules: UncertaintyPolicy
  provenanceRules: ProvenancePolicy
  failureModes: FailureTaxonomy
  validationSuite: TestSuiteRef
  evidenceLevel: EvidenceStatus
}
```

Capabilities MUST distinguish **pure evaluation**, **local ephemeral computation**, **learning-state update**, **CDE proposal**, **committed state mutation**, and **external irreversible action**. These are distinct effect classes; a generic `execute` flag is insufficient.

### 4.3 Invocation envelope and result

An invocation SHOULD carry `requestId`, `capabilityId@version`, `callerPrincipal`, `ObjectRef`, `StateRef`, `PerspectiveRef`, `timeScope`, `purpose`, `requestedEffect`, `authorizationContext`, `inputEvidenceRefs`, and `resourceBudget`. The result SHOULD carry a typed value, status (`success | rejected | indeterminate | partial | failed`), applied assumptions, output evidence, uncertainty qualification, trace identifiers, and explicit residuals. An indeterminate result MUST NOT be silently coerced into success or falsehood.

## 5. Capability categories and effect lattice

The baseline capability classes are:

| Category | Representative function | Default effect boundary |
|---|---|---|
| Representation | Resolve or project a WE view | Read-only |
| Transformation | Bucketize, normalize, encode, combine, derive | Read-only or ephemeral |
| Differential | Align, compare, rank, explain | Read-only |
| Reasoning | Apply typed rules, qualify claims | Read-only assertion generation |
| Learning | Calibrate metric or revise policy | Versioned learning-state proposal |
| Evolution | Generate typed CDE candidate delta | Candidate only |
| Governance | Check constraints, provenance, permissions | Evaluation / decision record |
| Relay | Package and transfer validated capability | No automatic receiving-side authority |

The effect declaration MUST be conservative: unknown or unmodeled effects are not treated as harmless. A consumer MUST reject an effectful invocation when the applicable policy cannot determine whether it is authorized.

## 6. Typed capability graph

A capability composition is a directed graph `G = (V, E)` where each node is a versioned capability invocation and each edge carries a typed output-to-input binding plus its semantic obligations. A graph is **well-typed** only if every edge satisfies all applicable compatibility conditions.

For an edge `A.out → B.in`, compatibility requires at minimum:

- Structural type and schema compatibility, including nullability and cardinality.
- WE identity and state/version scope compatibility under SPEC-001.
- Unit, metric, temporal, perspective, and granularity alignment under SPEC-002 and SPEC-003.
- Evidence and epistemic-class compatibility; a score cannot be passed as a proof without a justified conversion.
- Permission non-escalation and permissible information flow.
- Declared preconditions for `B`, established by outputs and admissible context from `A`.
- Explicit handling of partial failure, uncertainty, and provenance dependencies.

A composition checker MUST produce either a justified compatibility record, a qualified unresolved obligation, or a rejection. **Undischarged safety-critical obligations block promotion.**

## 7. Composition semantics and proof obligations

For sequential composition `B ∘ A`, a proposed sufficient rule is:

```text
Pre(A) holds
Post(A) entails Pre(B) under the declared semantics
Effects(A) ∪ Effects(B) are authorized and non-conflicting
All scope, evidence, and type adapters are validated
------------------------------------------------------
B ∘ A is admissible as a candidate composition
```

This rule licenses **admissibility for further testing**, not guaranteed correctness or usefulness. The actual postcondition of a composition must be established by an implementation-specific semantic argument and conformance evidence.

Parallel composition MUST declare read/write sets and conflict policy. Branching composition MUST state guard semantics and treatment of unknown values. Cyclic composition MUST declare a termination, budget, or convergence control; unbounded self-invocation is not permitted by default. Stateful composition MUST use explicit versioning and conflict handling rather than assuming serial execution.

## 8. Adapters and semantic alignment

An adapter is itself a capability subject to this contract. For example, a SQL-to-WE adapter may `bucketize`, `normalize`, `combine`, `encode`, or `derive` attributes before generating `Object[metricIndices]` projections. It MUST preserve SQL NULL/three-valued logic, aggregation grain, join multiplicity, row-level security, and data provenance where applicable. A SQL primary key MUST NOT automatically be promoted to WE identity.

Conversions that lose information MUST declare their loss profile and the downstream inferences they cannot support. A unit conversion, discretization, or temporal aggregation cannot be silently treated as invertible. Cross-perspective translation MUST name its policy and cannot manufacture an objective fact from a subjective score.

## 9. ODK core invariance and plugin portability

The ODK discipline remains **Resolve → Project → Align → Evaluate → Qualify → Trace**. Plugins MAY supply projectors, aligners, comparators, transformation policies, or explainers, but MUST NOT bypass kernel stages that enforce type checks, qualification, permissions, and traceability.

For OCSH-002 and OCSH-003, a portability trial SHOULD compare at least two materially different domains using the same declared kernel build and public interfaces. Kernel modifications, adapter effort, conformance failures, latency, maintenance, and regression burden MUST be logged. A claimed unchanged kernel requires artifact hashes or equivalent reproducible build evidence; a plugin-specific kernel fork does not count as unchanged-core portability.

## 10. Evidence, uncertainty, and epistemic separation

Every capability result MUST preserve source lineage sufficient to reconstruct its input dependencies and the plugin versions applied. The following epistemic classes MUST remain distinct: source record, observation, derived metric, deductive conclusion, statistical inference, hypothesis, evaluation, decision recommendation, authorized action, and observed outcome.

Uncertainty MUST be propagated or explicitly bounded when capabilities are composed. A downstream plugin MUST NOT strip uncertainty qualifiers or silently promote a weakly supported assertion to verified truth. Evidence duplication, correlated agents, and shared upstream sources MUST be represented rather than counted as independent support.

An evidence bundle MAY contain tests, proof artifacts, benchmark results, counterexamples, reviewer judgments, and deployment observations; each item MUST state its scope and status. No bundle implies general validity beyond its declared conditions.

## 11. Permissions, isolation, and least authority

Permissions are evaluated at **installation, binding, invocation, and promotion** boundaries. An invocation MUST receive no more authority than the intersection of caller permissions, WE policy, plugin policy, data policy, and receiving-system policy. A plugin MUST NOT expand permissions by chaining through another plugin or relay endpoint.

Untrusted plugins SHOULD run under an isolation profile with declared CPU/memory/time/network/filesystem limits. Secrets, private data, and restricted evidence MUST NOT be included in relay artifacts unless explicitly authorized for the destination. The conformance suite MUST test attempted privilege escalation, exfiltration, hidden side effects, and cross-tenant data mixing. These are proposed controls, not claims that sandboxing is foolproof.

## 12. Dependency resolution, versioning, and lifecycle

Dependencies MUST be version-constrained and pinned or reproducibly resolved for each validated composition. A plugin update MUST trigger impact analysis on dependent capability graphs and a risk-based regression plan. Semantic changes to comparator direction, unit policy, granularity interpretation, inference rules, or effect classification require explicit compatibility review even if input/output schemas are unchanged.

Recommended lifecycle:

`proposed → isolated-test → conformance-reviewed → approved-for-scope → monitored → deprecated/revoked`

A revoked capability MUST NOT be newly invoked in a governed production scope; historical evidence may remain accessible under retention policy. Rollback to an earlier plugin version is permitted only when its data and state compatibility are checked.

## 13. CDE, learning, and state promotion boundaries

A plugin may generate candidate typed deltas for a WE or composite State-Container. It MUST provide read/write scopes, preconditions, applicable constraints, state versions, and expected effects. A CDE candidate is not a committed state. Local admissibility does not prove global feasibility for shared buses, routes, inventories, transaction networks, or code repositories.

Learning plugins MUST distinguish updates to a learned model, metric calibration, policy proposal, and WE state change. Candidate promotions require separate validation and authority under SPEC-005 and SPEC-006 when those contracts are finalized. Irreversible external actions require a separately declared approval boundary; a rollback plan for internal state is not equivalent to reversing real-world effects.

## 14. Relay and collective structural learning

A relay package SHOULD include: capability artifact and digest, semantic contract, dependency lock, domain assumptions, conformance results, counterexamples, known limitations, provenance, authorization constraints, and receiving-side test plan.

The receiving environment MUST recheck identity, type, perspective, granularity, permissions, data access, and task-specific success criteria. A passing source-domain test is not sufficient. Relay outcomes SHOULD be recorded as **positive transfer**, **neutral transfer**, **negative transfer**, or **indeterminate**, with integration and validation costs. Failed relay attempts are retained as explicit learning evidence rather than silently discarded.

UIERU/MLIU MAY orchestrate relay portfolios and collective learning; SIF MAY localize needs and candidate capabilities; ISGFTR supplies hypotheses about spillover. These relationships do not establish algorithmic equivalence or a proven scaling law.

## 15. AI-generated code governance as a composition case

Consider a code change that alters a function signature. A candidate graph is:

`Repository Snapshot → Calling-Graph Extractor → UTN Locator → Object-Centric Impact Analyzer → Data/Control-Flow Analyzer → Contract Checker → Regression Selector → Evidence Reviewer`.

Each node is a versioned capability with scope and provenance. Calling-graph reachability proposes an impact region; it is **not** complete behavioral analysis. A governance decision MUST account for dynamic dispatch, reflection, generated code, data dependencies, security boundaries, and regression evidence as relevant. The pipeline MUST NOT automatically merge or deploy code solely because a graph-based impact score is low. This example connects CASE-006 and OCSH-011; it does not claim demonstrated improvement.

## 16. Conformance profiles and required artifacts

A proposed conformance report SHOULD declare one or more profiles:

- **CP-BASE:** manifest, types, immutable versions, provenance, permissions, failure semantics.
- **CP-COMP:** typed graph composition, adapters, uncertainty, dependency and effect checks.
- **CP-RELAY:** receiving-side validation, transfer accounting, negative-transfer recording.
- **CP-EVOLVE:** learning/CDE proposal separation, composite constraints, promotion boundaries.
- **CP-CODE:** calling-graph plus data/control-flow and regression evidence integration.

A report MUST include implementation/build identity, supported profiles, test cases, observed outcomes, unresolved obligations, and deviations. A profile is not passed when any of its mandatory P0 checks fails. A partial profile MUST be labeled partial, not certified.

## 17. Normative conformance requirements

| ID | Priority | Requirement |
|---|---|---|
| OPC-001 | P0 | A plugin MUST publish stable identity, version, integrity, and publisher metadata. |
| OPC-002 | P0 | Every capability MUST declare typed inputs, outputs, semantic assumptions, and failure modes. |
| OPC-003 | P0 | Capability invocations MUST bind WE identity, state/version, perspective, and time as applicable. |
| OPC-004 | P0 | Composition MUST reject incompatible units, granularities, temporal scopes, or perspectives without validated adapters. |
| OPC-005 | P0 | Plugins MUST NOT bypass ODK semantic alignment, qualification, or trace obligations. |
| OPC-006 | P0 | Evidence and epistemic classes MUST be preserved across capability edges. |
| OPC-007 | P0 | Invocation authority MUST NOT exceed the intersection of applicable policies. |
| OPC-008 | P0 | Unknown or unauthorized side effects MUST block governed execution. |
| OPC-009 | P0 | Comparator scores MUST NOT be promoted to deductive proofs without a valid inference contract. |
| OPC-010 | P0 | Learning updates and CDE proposals MUST NOT silently commit WE state or external actions. |
| OPC-011 | P0 | Dependency versions and effective plugin artifacts MUST be reproducible for validated compositions. |
| OPC-012 | P0 | Cycles and recursive invocation MUST have declared termination, convergence, or resource limits. |
| OPC-013 | P1 | A composition SHOULD provide an auditable graph and per-edge compatibility evidence. |
| OPC-014 | P1 | Semantic changes SHOULD trigger impact analysis and regression testing. |
| OPC-015 | P1 | Cross-domain relay MUST be validated in the receiving context before claims of transfer. |
| OPC-016 | P1 | Negative and indeterminate transfer outcomes MUST be recorded alongside successes. |
| OPC-017 | P1 | Portability studies SHOULD report kernel changes and integration/validation costs. |
| OPC-018 | P1 | A code-governance plugin SHOULD supplement calling graphs with applicable data/control-flow and security evidence. |
| OPC-019 | P2 | Systems MAY support multi-agent capability portfolios with conflict adjudication. |
| OPC-020 | P2 | Systems MAY generate new plugins or metrics, subject to the same conformance gates. |

## 18. Counterexample and negative test matrix

The following are **test designs**, not executed results.

| Test | Invalid or adversarial condition | Expected disposition |
|---|---|---|
| NEG-001 | Two plugins expose identical field names but incompatible units | Reject edge pending validated conversion |
| NEG-002 | SQL row key is used as WE identity without resolution | Reject identity promotion |
| NEG-003 | Fleet average is inferred as a property of every bus | Reject unsupported granularity bridge |
| NEG-004 | Statistical score is passed to a deductive-proof consumer | Reject or explicitly retype as non-proof evidence |
| NEG-005 | Plugin requests write permission after read-only installation | Deny unauthorized invocation |
| NEG-006 | Relay package contains restricted personal data | Block transfer; preserve incident trace |
| NEG-007 | Dependency update changes comparator direction but not schema | Require semantic review and regression |
| NEG-008 | Two parallel plugins mutate the same WE state version | Detect conflict; do not silently commit |
| NEG-009 | Cyclic plugin graph lacks a termination bound | Reject governed execution |
| NEG-010 | Plugin strips uncertainty and labels an estimate as fact | Reject epistemic promotion |
| NEG-011 | CDE candidate satisfies one bus constraint but violates fleet capacity | Reject global state promotion |
| NEG-012 | Source-domain relay passes but target-domain benchmark degrades | Record negative transfer; block benefit claim |
| NEG-013 | Two agents cite the same upstream evidence as independent | Mark correlated provenance |
| NEG-014 | A revoked plugin remains in a cached execution plan | Invalidate or block new invocation |
| NEG-015 | Calling graph omits reflective or dynamic invocation paths | Qualify incomplete impact; require complementary checks |
| NEG-016 | Plugin returns `partial` but downstream assumes `success` | Reject unsafe status coercion |
| NEG-017 | A normalized metric is treated as reversible raw measurement | Reject unsupported inverse semantics |
| NEG-018 | Sandbox rollback is cited as reversing an external side effect | Reject false rollback guarantee |

## 19. Illustrative end-to-end conformance scenarios

### 19.1 SQL-native object adaptation

A SQL adapter reads authorized rows, preserves NULL and join multiplicity, resolves WE identities through a declared mapping, and applies `bucketize` and `normalize` transformations. An ODK comparator consumes typed projections. The composition passes only when semantic alignment, provenance, and row-level permissions survive every edge. **Related:** CASE-002, OCSH-007.

### 19.2 School-bus scheduling

Student, bus, route, and fleet WEs are combined in a composite candidate state. Capacity and ride-time evaluation plugins score proposed changes; a CDE plugin emits typed deltas. No plugin commits a new schedule until global constraints and authority checks pass. **Related:** CASE-003, OCSH-005.

### 19.3 Transaction and compositional identity

Transaction records and possible actor relations are processed as evidence-bearing candidate associations. Similarity and graph scores remain hypotheses; plugins must not equate a composite actor inference with verified personal identity. **Related:** CASE-004, SPEC-005.

### 19.4 Cross-domain relay

A generic metric alignment plugin is moved from scheduling to code impact analysis without ODK core changes. The target-domain test suite must independently assess semantic fit, coverage, failure cases, and net validation cost. **Related:** CASE-005, OCSH-002/003/008.

## 20. Hypothesis-to-validation mapping

| Hypothesis | What this specification enables | Required evidence before claiming support |
|---|---|---|
| OCSH-002 | Common kernel across plugins | Same core build, distinct domains, reproducible tests |
| OCSH-003 | Contract-based domain adaptation | Baseline-controlled integration effort and correctness |
| OCSH-005 | Plugin-mediated WE-native CDE | Single/composite state safety and rollback-boundary tests |
| OCSH-007 | SQL-to-WE adapters | SQL semantic and permission preservation suites |
| OCSH-008 | Validated capability relay | Receiving-side held-out tests and transfer cost accounting |
| OCSH-009 | Untargeted capability spillover | Preregistered untargeted tasks, positive and negative results |
| OCSH-011 | Code governance transfer | Impact-localization and regression-targeting baselines |

All hypotheses remain **proposed / E0** at project inception. Passing an interface test does not demonstrate scaling or intelligence improvement.

## 21. Explicit leftovers

1. A canonical machine-checkable manifest schema and version negotiation protocol.
2. Formal semantics for capability effect composition across languages.
3. General decidability limits for semantic compatibility checking.
4. A reference proof format for precondition/postcondition discharge.
5. Quantified information-loss contracts for lossy adapters.
6. Privacy-preserving provenance across organizations.
7. Safe isolation guarantees for model-backed and native-code plugins.
8. Cross-tenant identity and authorization federation.
9. Deterministic replay under nondeterministic model outputs.
10. Cache invalidation across time, permission, and plugin version changes.
11. General conflict resolution for parallel stateful capability graphs.
12. Termination guarantees for cyclic and self-modifying plugin graphs.
13. Statistical calibration of uncertainty across heterogeneous capabilities.
14. Detection of evidence laundering and correlated multi-agent outputs.
15. Negative-transfer prediction before receiving-side deployment.
16. Comparable integration-cost metrics across domains and teams.
17. Security implications of dynamically generated plugins and policies.
18. Composite WE transaction protocols under distributed failure.
19. Formal rollback semantics for internal state versus external effects.
20. Dynamic-language calling-graph completeness and soundness tradeoffs.
21. Governance of plugin marketplace trust, revocation, and supply chains.
22. Independent benchmarks for OCSH-003 and OCSH-008.
23. Preregistered evidence thresholds for OCSH-009 untargeted spillover.
24. Whether accumulated plugin portfolios produce sustained net capability growth (OCSH-010), which remains unproven.

These items MUST remain visible in the future `research-trace/UNRESOLVED-RESIDUALS.md`, relevant hypothesis records, or validation roadmap. An implementation MUST NOT silently reinterpret an unresolved research question as an established guarantee.

## 22. Release discipline and conclusion

SPEC-004 is a **proposed research contract**, not a production-ready plugin security standard or certification. Its value is to make reuse conditional on semantics, evidence, and authority rather than on API shape alone. Object Plugins can become reusable structural intelligence components only when their compositions preserve typed meaning, remain auditable, and survive independent receiving-context validation. The next research tasks are to finalize SPEC-005 and SPEC-006, construct conformance fixtures, and run baseline-controlled cross-domain experiments. **Specifications/Contracts First; Conformance Before Runtime; Explicit Leftover.**

---

### Internal cross-references

- Core papers: [OCSRE-004](../docs/OCSRE-004-Object-Differential-Kernel-and-Generic-Operators.md), [OCSRE-005](../docs/OCSRE-005-Object-Plugins-and-Composable-Intelligence-Capabilities.md), [OCSRE-009](../docs/OCSRE-009-Epistemic-Separation-and-Object-Centric-Evidence-Governance.md), [OCSRE-011](../docs/OCSRE-011-Object-Capability-Spillover-Relay-and-Collective-Structural-Learning.md).
- Specifications: [SPEC-001](SPEC-001-Object-Identity-Perspective-and-State-Contract.md), [SPEC-002](SPEC-002-Object-Differential-Kernel-and-Comparator-Contract.md), [SPEC-003](SPEC-003-Classical-Reasoning-Preservation-and-Granularity-Contract.md).
- Planned follow-on contracts: `SPEC-005-In-Situ-Learning-Feedback-and-Epistemic-Governance-Contract.md`; `SPEC-006-WE-Native-CDE-Composite-State-and-Relay-Contract.md`.
- Planned validation cases: `CASE-002-SQL-Native-Object-Adaptation.md`, `CASE-003-School-Bus-Scheduling-and-Composite-WE-State.md`, `CASE-005-Cross-Domain-Object-Plugin-Relay.md`, `CASE-006-AI-Generated-Code-Governance-Through-Calling-Graphs-and-CDE.md`.
