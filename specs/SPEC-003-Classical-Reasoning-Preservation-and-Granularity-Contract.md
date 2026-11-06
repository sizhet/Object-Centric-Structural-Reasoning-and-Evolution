# SPEC-003 — Classical Reasoning Preservation and Granularity Contract

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Release target:** v1.0.0 — Research Framework and Contracts  
**Status:** Proposed normative research contract; no implementation or empirical conformance certified  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**License:** Apache-2.0  
**Primary dependencies:** SPEC-001, SPEC-002; OCSRE-002, OCSRE-003, OCSRE-009  
**Primary hypotheses:** OCSH-001, OCSH-006

## Abstract

This specification defines a contract for embedding a deliberately restricted fragment of classical deductive reasoning into object-centric structural reasoning while governing the more difficult transitions across time, perspectives, relationships, and granularities. The contract does not assume that object-centric reasoning is a conservative extension of first-order logic, that metric similarity entails logical identity, or that aggregation automatically licenses inheritance. Instead, it defines a precise reference semantics, a translation obligation, explicit proof-status boundaries, typed granularity operations, negative tests, and an auditable conformance report. Classical entailment is treated as a preserved capability within a declared fragment, not as a blanket guarantee for every OCSRE operator. Dynamic and probabilistic reasoning may extend the system's utility only under separate semantics and validation.

## 1. Purpose and applicability

OCSRE connects World Entity (WE) representation, `Object[metricIndices]` differential computation, typed relational reasoning, in-situ learning, and constrained state evolution. The purpose of SPEC-003 is to prevent this integration from silently weakening deductive validity or treating a change of granularity as a harmless formatting operation.

A conforming implementation MUST declare its supported logical fragment, its interpretation of object references, its admissible inference rules, and its granularity operators. It MUST be able to reject or qualify inferences outside those declared boundaries. This document specifies *proposed* requirements for future conformance, not a claim that any current OCSRE runtime meets them.

The contract applies to rule engines, proof services, object plugins, WE relation stores, UTN/SIF localization consumers, and CDE proposal evaluators. It does not prescribe a particular theorem prover, ontology language, database, or agent runtime.

## 2. Normative vocabulary and precedence

**MUST / MUST NOT** denote mandatory requirements for a conforming implementation; **SHOULD / SHOULD NOT** denote recommendations requiring documented justification if departed from; **MAY** denotes optional behavior. These are requirements proposed by this research specification, not external standards compliance claims.

- **IdentityRef:** a stable reference to a WE, as governed by SPEC-001; not a display name, row key, or graph address.
- **StateRef:** an immutable or version-addressed state snapshot with valid-time and observation-time metadata where relevant.
- **PerspectiveRef:** an identified evaluation or interpretation context; perspective-relative claims are not automatically objective claims.
- **Assertion:** a typed proposition with scope, provenance, epistemic class, and declared interpretation.
- **Derivation:** a sequence or DAG of rule applications, each referencing premises and the applied rule version.
- **Granularity:** the level and semantics of an entity or state representation, e.g., student, class, bus, fleet, function, module, or program.
- **Granularity bridge:** an explicitly typed operation mapping assertions between levels, with preconditions and proof or evidence obligations.
- **Entailed:** true in every model of the premises under the declared logical semantics.
- **Supported:** backed by evidence or scores without a deductive entailment guarantee.
- **Indeterminate:** neither proven nor refuted within the applicable scope, or blocked by incomplete evidence.

SPEC-001 governs identity, state, time, perspective, and permissions. SPEC-002 governs metric projections, semantic alignment, and comparator outputs. SPEC-003 governs inference validity and granularity bridges; it MUST NOT silently override either upstream contract.

## 3. Foundational non-equivalences

A conforming reasoner MUST preserve the following distinctions:

1. **WE identity ≠ predicate membership:** `Person(x)` does not resolve who `x` is without an IdentityRef mapping.
2. **Entailment ≠ similarity:** a comparator score is not a proof of membership, equality, or causation.
3. **Absence ≠ negation:** missing, redacted, inaccessible, and false claims have different semantics.
4. **Type membership ≠ inheritance without scope:** a rule may be conditional on time, state, jurisdiction, or perspective.
5. **Part ≠ whole:** a property of a fleet need not hold for any individual bus; a property of one bus need not hold for the fleet.
6. **Aggregate ≠ instance:** an average or percentile does not establish a universal statement about members.
7. **Association ≠ causal implication:** co-occurrence, graph adjacency, and directionally scored evidence do not license causal proof.
8. **Candidate state ≠ committed state:** CDE hypotheses and sandbox transitions cannot be asserted as observations of the world.
9. **Localization ≠ semantic equivalence:** UTN, MDT, and WE-HDT addresses may locate relevant structures without proving that their internal algorithms or referents coincide.
10. **Authorization ≠ truth:** a well-supported conclusion does not authorize external action.

## 4. Reference classical fragment F0

### 4.1 Syntax

The minimal reference fragment F0 is a many-sorted, function-free, first-order fragment with unary predicates, individual constants, equality only when a declared identity interpretation exists, explicit negation, conjunction, implication, and universal and existential quantification. A conforming implementation MAY support a richer fragment, but MUST publish its extra rules and proof obligations separately.

For the baseline categorical syllogism tests, use formulas of the forms:

- `All(A,B) := ∀x (A(x) → B(x))`
- `No(A,B) := ∀x (A(x) → ¬B(x))`
- `Some(A,B) := ∃x (A(x) ∧ B(x))`
- `SomeNot(A,B) := ∃x (A(x) ∧ ¬B(x))`

Classical two-valued Tarskian model semantics apply to F0 **within the declared domain and scope**. Universal statements do not imply that their subject class has a member. Implementations MUST NOT introduce existential import unless a separate premise or explicitly declared nonempty-domain/subclass axiom justifies it.

### 4.2 Sound example

Given `∀x (Human(x) → Mortal(x))`, `Human(socrates)`, and a stable interpretation of `socrates`, infer `Mortal(socrates)` by universal instantiation and modus ponens. The corresponding object-centric assertion is a **deductive** result only if the same premises, referent, scope, and inference rules remain valid.

### 4.3 Unsound near-neighbors

From `∀x (Human(x) → Mortal(x))` and `Mortal(socrates)`, one MUST NOT infer `Human(socrates)`. From `∀x (Unicorn(x) → Horned(x))`, one MUST NOT infer `∃x Unicorn(x)`. From unknown `Human(socrates)`, one MUST NOT infer `¬Human(socrates)` unless a separate closed-world rule is explicitly selected and the result is typed accordingly.

## 5. Embedding into object-centric assertions

Define a proposed translation `T_c` from F0 formulas to OCSRE assertions under a fixed context `c = (identityMap, domain, stateScope, timeScope, perspective, ontologyVersion, policy)`. Its intended preservation obligation is:

`Γ ⊨F0 φ  ⇒  T_c(Γ) ⊨OCSRE,F0 T_c(φ)`

**Only** where `T_c` is well-defined, referent-preserving, quantifier-domain-preserving, negation-preserving, and interpreted by a sound F0 subreasoner. This is a target property to be demonstrated, not an established theorem for the full OCSRE architecture. Reverse preservation, completeness, and conservativity are independent research questions.

The translation MUST:

- map each constant to an unambiguous, permission-valid IdentityRef or reject the translation;
- preserve the quantification domain, including empty classes;
- distinguish logical predicate interpretation from metric thresholds and learned classifiers;
- preserve explicit negative assertions and avoid inventing negative facts from missing data;
- bind premises and conclusions to compatible state/time/perspective scopes;
- preserve the source formula, ontology/rule version, proof dependencies, and derivation status;
- refuse automatic coercion of probabilistic, default, or abductive rules into F0 proof rules.

If any precondition fails, the output MUST be `blocked`, `indeterminate`, or a separately labeled non-deductive result rather than `entailed`.

## 6. Canonical reasoning records

The following are **illustrative schema contracts**, not an implemented API:

```yaml
AssertionRef:
  assertion_id: string
  subject: IdentityRef | QuantifiedVariable
  predicate: PredicateRef
  object: IdentityRef | TypedLiteral | QuantifiedVariable | null
  polarity: positive | explicit_negative
  scope:
    state_ref: StateRef | null
    valid_time: Interval | null
    perspective_ref: PerspectiveRef | null
    granularity_ref: GranularityRef
  epistemic_class: observed | asserted | derived_deductive | inferred_statistical | hypothetical
  provenance_refs: [EvidenceRef]
  access_policy_ref: PolicyRef
  ontology_version: string

InferenceRequest:
  premises: [AssertionRef]
  goal: FormulaRef
  fragment_id: F0 | RegisteredFragment
  identity_mapping_ref: MappingRef
  rule_set_version: string
  scope_policy_ref: ScopePolicyRef
  authority_context_ref: AuthorityRef

InferenceResult:
  status: entailed | refuted | indeterminate | blocked | inconsistent_premises
  logical_scope: FragmentRef
  proof_trace_ref: ProofTraceRef | null
  assumptions: [AssumptionRef]
  unresolved_residuals: [ResidualRef]
  source_refs: [EvidenceRef]
  disclosure_policy_ref: PolicyRef
```

`refuted` means a declared refutation procedure has established the negation within the chosen semantics; it is not the same as `not entailed`. If premises are inconsistent, an implementation MUST state its inconsistency policy. In classical logic, explosive entailment is a formal consequence of inconsistency; a safety-oriented OCSRE service SHOULD quarantine contradictory premise sets instead of reporting arbitrary actionable conclusions.

## 7. Proof discipline and rule registry

Every deductive rule MUST have a registered identifier, input signature, output signature, supported fragment, side conditions, and soundness rationale. A proof trace MUST identify its exact premises, rule versions, variable substitutions, and context. Reusing a proof under a changed ontology or identity mapping requires a compatibility check; a proof from one state snapshot MUST NOT be silently treated as valid for another.

A rule may be *deductive*, *defeasible*, *probabilistic*, *heuristic*, or *decision-policy*. These labels MUST NOT be conflated. Heuristic suggestions MAY feed a deductive prover as proposed premises only after separate admission and evidence governance. A score or confidence value MUST NOT alter a proof's logical validity.

## 8. Typed relational inference

Relation declarations SHOULD specify arity, domain/range types, direction, temporal scope, identity assumptions, and algebraic properties such as reflexivity, symmetry, transitivity, antisymmetry, or functional dependency. No property is presumed solely from a relation's English name.

Examples: `parentOf(a,b)` does not entail `parentOf(b,a)`; `dependsOn(a,b)` does not entail `dependsOn(b,a)`; `calls(f,g)` is not necessarily transitive as a direct-call relation, although its explicitly computed reachability closure may be. `memberOf(student,class)` does not automatically license transfer of a class-level attribute to the student.

Relational composition MUST check type compatibility, scope overlap, identity mapping, and declared inference laws. Graph path discovery is a localization result unless an appropriate relational rule makes it a proof.

## 9. Temporal, state, and perspective consistency

Each inference MUST declare whether predicates refer to an instantaneous snapshot, an interval, a historical observation, or a counterfactual candidate state. A statement true at `t1` MUST NOT automatically propagate to `t2`. Late-arriving evidence MUST retain both event-time and recording-time semantics where supplied by SPEC-001.

Perspective-dependent predicates (e.g., `acceptableToStakeholder`, `highRiskUnderPolicy`) MUST carry a perspective and policy version. A perspective-neutral predicate and a perspective-relative assessment MUST NOT be merged without a registered bridge. A policy change may invalidate an assessment without changing the underlying WE identity or objective observation.

## 10. Granularity model and bridge taxonomy

Granularity is a semantic property of a claim, not merely the resolution of a dataset. A bridge MUST declare its source granularity, destination granularity, mapping cardinality, membership semantics, loss characteristics, and valid inference direction.

| Bridge type | Illustrative transformation | Mandatory caution |
|---|---|---|
| Member-to-collection | buses → fleet | Member properties do not automatically become fleet properties |
| Collection-to-member | fleet → bus | Aggregates do not automatically become universal member claims |
| Part-to-whole | function → module | Local correctness does not prove whole-system correctness |
| Whole-to-part | module → function | Global performance does not prove per-function performance |
| Instance-to-type | observed person → Person class | Finite observations do not establish universal truth |
| Type-to-instance | `∀x(A→B)`, `A(a)` → `B(a)` | Requires valid membership and scope |
| Temporal coarsening | hourly → daily | Must specify window, missingness, and aggregation semantics |
| Perspective projection | stakeholder A → shared view | Value judgments are not perspective-neutral facts |
| Composite-state bridge | bus/student/route → schedule | Cross-object constraints remain in force |

A bridge MUST identify whether it is **lossless**, **lossy**, **conditional**, or **unsupported**. A lossy bridge MUST retain an explicit residual or qualification. Invertibility MUST NOT be presumed.

## 11. Aggregation and inheritance contracts

An aggregation operator MUST specify: population definition, membership snapshot, weighting, units, null policy, deduplication, time alignment, permissions, and uncertainty treatment. Its output MUST be typed as an aggregate claim rather than as an individual property.

For example, `meanOccupancy(fleet)=0.65` does not entail `occupancy(bus42)=0.65`, nor does it entail that every bus satisfies an occupancy threshold. `allMembersSatisfy(P, group)` can support a member claim only if membership and the universal statement are both valid under the same scope. A statistic based on sampled members MUST NOT be promoted to universal membership without a separately justified statistical or deductive rule.

When a composite WE contains members owned by distinct authorities, aggregation may be permitted while mutation of members remains forbidden. Reasoning authorization and action authorization MUST be evaluated separately.

## 12. Object Differential Kernel boundary

SPEC-002 may produce aligned metrics, differentials, ranks, similarity values, and explanatory traces. SPEC-003 MUST accept these as typed *inputs*, not as automatic logical premises. To derive a categorical assertion from a metric, the system MUST register a threshold/classification rule, its domain and validity assumptions, its epistemic status, and its provenance.

For example, `similarity(a,b)=0.99` cannot establish `sameIdentity(a,b)`. A normalized risk score cannot establish an unqualified fact `Unsafe(a)` without a declared interpretation. Metric transformations such as Bucketize, Normalize, Combine, Encode, and Derive MUST retain their SQL and object semantics when used in reasoning.

## 13. WE-native CDE and decision boundaries

CDE may explore typed Delta proposals over a single WE or a composite State-Container. Inferences over proposed states MUST be tagged as counterfactual or candidate-state results. A candidate's internally consistent reasoning does not establish constraint satisfaction, authorization, successful execution, or external-world truth.

A transition from reasoning to action SHOULD follow: `infer → qualify → propose Delta → check preconditions and global constraints → authorize → commit → observe → validate`. Rollback or compensating action semantics MUST be explicitly documented for irreversible external effects. SPEC-006 governs the detailed state-evolution contract; SPEC-003 governs the validity and scope of claims used within it.

## 14. Security, epistemic provenance, and residual handling

All derived claims MUST inherit applicable source disclosure restrictions, subject to an explicit authorized declassification policy. A proof trace MUST NOT expose restricted premises to an unauthorized recipient. Redaction MUST NOT be presented as logical falsity. When evidence is inaccessible, the inference result MUST be qualified or blocked.

Every failed premise, missing bridge, incompatible scope, ambiguous referent, conflicting ontology, or unsupported rule MUST yield an explicit residual record. Repeated failed attempts MAY be accumulated as learning/relay data, but they do not become valid proof through repetition. Collective Learning MUST preserve independent verification and avoid circular evidence amplification.

## 15. Conformance requirements

A conforming implementation MUST supply testable evidence for the following proposed obligations.

| ID | Priority | Requirement | Negative-test expectation |
|---|---|---|---|
| CRG-001 | P0 | Declare exact supported logical fragment and semantics | Unsupported formula cannot be labeled proved |
| CRG-002 | P0 | Preserve F0 validity for translated sound inferences | `All(A,B), A(a)` entails `B(a)` |
| CRG-003 | P0 | Reject invalid converse/affirming consequent | `All(A,B), B(a)` cannot entail `A(a)` |
| CRG-004 | P0 | Preserve quantifier domain and existential import | Empty subclass cannot yield existential witness |
| CRG-005 | P0 | Distinguish unknown, missing, and explicit negation | Missing `P(a)` cannot yield `¬P(a)` |
| CRG-006 | P0 | Require unambiguous IdentityRef mapping | Duplicate display names cannot merge WEs |
| CRG-007 | P0 | Enforce time and state snapshot compatibility | `t1` assertion cannot silently prove `t2` claim |
| CRG-008 | P0 | Preserve perspective and policy scope | Stakeholder rating cannot become objective fact |
| CRG-009 | P0 | Enforce typed relation signatures and declared laws | `parentOf` cannot be reversed |
| CRG-010 | P0 | Require explicit granularity bridge | Fleet mean cannot become per-bus value |
| CRG-011 | P0 | Prevent lossy bridge inversion | Daily mean cannot recover every hourly value |
| CRG-012 | P0 | Distinguish proof from comparator score | 0.99 similarity cannot establish identity |
| CRG-013 | P0 | Preserve epistemic class across derivations | Statistical hypothesis cannot be labeled deduction |
| CRG-014 | P0 | Preserve provenance and permissions | Restricted premise cannot leak through proof trace |
| CRG-015 | P0 | Detect and qualify inconsistent premise sets | Contradictory facts cannot yield unqualified action |
| CRG-016 | P0 | Separate candidate from committed CDE states | Proposed route cannot be reported as executed |
| CRG-017 | P0 | Record unsupported premises and bridges as residuals | Missing bridge cannot silently default to true |
| CRG-018 | P1 | Register rule versions and proof replay dependencies | Changed ontology requires revalidation |
| CRG-019 | P1 | Test cross-granularity membership and aggregation changes | Membership update invalidates stale aggregate |
| CRG-020 | P1 | Maintain domain-portable reasoning interfaces | Plugin switch cannot change F0 proof semantics silently |
| CRG-021 | P1 | Evaluate negative transfer and false promotion | Relay without conformance cannot be certified |
| CRG-022 | P1 | Publish machine-readable conformance and exceptions | Missing evidence cannot be reported as pass |

**Conformance level:** P0 requirements are mandatory for any claim of core semantic safety. P1 requirements are mandatory for claims of portability, relay readiness, or advanced reproducibility. P2 runtime optimizations are optional and cannot relax P0.

## 16. Counterexample-first test catalog

The following tests are proposed fixtures, not executed results. Each fixture SHOULD record premises, declared scope, expected status, actual status, and a trace of any blocked inference.

| Test | Scenario | Expected outcome |
|---|---|---|
| CE-001 | `All(Human,Mortal); Human(s)` | `Mortal(s)` entailed |
| CE-002 | `All(Human,Mortal); Mortal(s)` | `Human(s)` not entailed |
| CE-003 | `All(Unicorn,Horned)` with no unicorns | No existential witness |
| CE-004 | `P(a)` absent | `¬P(a)` not entailed |
| CE-005 | Two distinct WEs named “Alex” | No identity collapse |
| CE-006 | `Student(a)` at `t1`, claim at `t2` | Block without persistence rule |
| CE-007 | Stakeholder A accepts route, B rejects | No perspective-neutral acceptance |
| CE-008 | `parentOf(a,b)` | Reverse edge not inferred |
| CE-009 | `calls(f,g); calls(g,h)` | Direct `calls(f,h)` not inferred; closure separately typed |
| CE-010 | Fleet mean occupancy 65% | No member occupancy inference |
| CE-011 | Group includes a sampled subset | No universal conclusion over population |
| CE-012 | Daily mean from hourly readings | No unique inverse reconstruction |
| CE-013 | Similarity 0.99 | No identity or deductive membership proof |
| CE-014 | SQL `NULL` metric value | No implicit zero or false |
| CE-015 | Contradictory `P(a)` and `¬P(a)` | Conflict surfaced; no unqualified promotion |
| CE-016 | Redacted source premise | No unauthorized trace disclosure |
| CE-017 | CDE candidate schedule improves score | No committed-world assertion |
| CE-018 | Individual bus valid, fleet allocation invalid | Composite constraint violation retained |
| CE-019 | Rule/ontology version changed | Old proof revalidated or invalidated |
| CE-020 | Cross-domain plugin claims a new inference law | Separate registration and tests required |

## 17. Reference conformance procedure

A future conformance suite SHOULD implement the following reproducible stages:

1. **Declare:** publish fragment, sorts, ontology, rule registry, identity mapping, time model, perspective policy, granularity bridges, and security model.
2. **Generate:** build a reference set of valid and invalid F0 derivations, including empty classes and explicit negation.
3. **Translate:** map the corpus into scoped WE assertions; report mapping failures rather than silently repairing them.
4. **Execute:** run the object-centric reasoner under pinned versions and capture proof DAGs and residuals.
5. **Compare:** check entailment results against an independently implemented reference prover or model checker for the supported finite test corpus.
6. **Challenge:** run CE-001 through CE-020 and randomized adversarial cases involving identity, temporal changes, and aggregation.
7. **Revalidate:** mutate ontology, group membership, perspective, and StateRef; confirm invalidation and proof replay behavior.
8. **Audit:** inspect authorization, redaction, counterfactual-state handling, and cross-domain relay provenance.
9. **Report:** publish passes, failures, untested obligations, environment versions, and known residuals without treating non-execution as success.

A finite test suite can provide conformance evidence but cannot by itself prove the translation sound for all models. A formal soundness theorem would require an explicit semantics and proof independent of testing.

## 18. Worked contract sketches

### 18.1 Person and classical reasoning — CASE-001

A registered person WE has a valid identity mapping and `Human(person)` assertion. A registered F0 rule states `∀x(Human(x)→Mortal(x))`. The engine can derive `Mortal(person)` with a proof trace. If the identity mapping is ambiguous or the ontology version differs, the result is blocked or qualified. This example illustrates deductive preservation; it does not claim that every empirical category is timeless.

### 18.2 SQL-native object adaptation — CASE-002

A SQL row contains an age column and a nullable status column. Bucketizing age into an age group creates a typed derived attribute, not a universal fact about every person in that group. `NULL` status cannot be treated as explicit negative status. SQL permissions and provenance survive any `Object[metricIndices]` projection.

### 18.3 School-bus scheduling — CASE-003

A composite WE State-Container includes students, buses, routes, and temporal constraints. An average ride-time improvement does not imply every student's ride time improved. A candidate reassignment can be reasoned about under its candidate StateRef, but only CDE validation and authorization can promote it.

### 18.4 Transaction and compositional identity — CASE-004

Several transactions exhibit high metric similarity and shared weak signals. Such evidence can support a hypothesis of common control, but not deductively establish one real-world actor. Composite identity requires a separately governed evidence and identity-resolution process.

### 18.5 AI-generated code governance — CASE-006

A calling graph shows `f` calls `g`, and `g` calls `h`. This supports a typed reachability analysis, not a proof that changing `h` necessarily changes the behavior of `f`. Data/control flows, contracts, security boundaries, and regression evidence are additional required perspectives. UTN may localize affected structures, while OCSRE records the reasoning and CDE may govern candidate code changes.

## 19. Hypothesis traceability and evaluation

| Hypothesis | SPEC-003 contribution | Evidence needed |
|---|---|---|
| OCSH-001 | Restricted classical-preservation contract | Reference semantics, proof obligations, valid/invalid inference corpus |
| OCSH-006 | Explicit cross-granularity bridge contract | Error-rate comparisons with and without bridge enforcement |
| OCSH-002 | Typed comparator/proof separation | Cross-domain false-promotion tests |
| OCSH-004 | Feedback without proof laundering | Traceable revision and premise-invalidation tests |
| OCSH-005 | Candidate/committed state distinction | CDE counterfactual and global-constraint tests |
| OCSH-007 | SQL semantic alignment | NULL, join, aggregation and permission tests |
| OCSH-008 | Relay with rule and scope preservation | Independent target-domain conformance |
| OCSH-011 | Calling-graph inference boundaries | Change-impact localization and regression validation |

All hypotheses remain **proposed / E0** at the time of this research specification. A successful example is not evidence of general soundness or scaling.

## 20. Dependencies and companion-document map

- `../docs/OCSRE-002-From-Classical-Syllogism-to-Object-Centric-Structural-Reasoning.md`: restricted classical core and embedding thesis.
- `../docs/OCSRE-003-Dynamic-Relational-and-Multi-Granular-Reasoning.md`: dynamic, relational, perspective and granularity mechanisms.
- `../docs/OCSRE-004-Object-Differential-Kernel-and-Generic-Operators.md`: comparator and differential boundaries.
- `../docs/OCSRE-009-Epistemic-Separation-and-Object-Centric-Evidence-Governance.md`: proof, inference, hypothesis and authority separation.
- `SPEC-001-Object-Identity-Perspective-and-State-Contract.md`: canonical object identity, StateRef and PerspectiveRef.
- `SPEC-002-Object-Differential-Kernel-and-Comparator-Contract.md`: typed metric and comparator semantics.
- `SPEC-004-Object-Plugin-and-Capability-Composition-Contract.md`: proposed rule/plugin registration and portability (planned).
- `SPEC-005-In-Situ-Learning-Feedback-and-Epistemic-Governance-Contract.md`: proposed evidence-promotion and feedback rules (planned).
- `SPEC-006-WE-Native-CDE-Composite-State-and-Relay-Contract.md`: proposed state-transition and relay controls (planned).
- `../cases/CASE-001-Person-and-Classical-Reasoning.md`: proposed reference syllogism case (planned).
- `../extensions/EXT-001-Object-Centric-Reasoning-and-the-History-of-Logic.md`: historical and theoretical context (planned).
- `../research-trace/HYPOTHESIS-REGISTRY.md` and `../research-trace/COUNTEREXAMPLE-REGISTRY.md`: proposed trace records (planned).

Companion paths marked *planned* are repository targets, not claims of completed files.

## 21. Explicit leftovers and open research questions

1. Provide a fully formal denotational semantics for the OCSRE F0 embedding.
2. Prove or refute soundness for each supported translation and rule set.
3. Determine completeness under restricted finite domains and evolving ontologies.
4. Decide whether any conservative-extension theorem is achievable under sharply limited assumptions.
5. Define decidable richer fragments for typed relations and composite objects.
6. Formalize the interaction of classical negation, SQL three-valued logic, and open-world missingness.
7. Specify a non-explosive inconsistency-handling profile and its proof guarantees.
8. Characterize identity aliases, merges, splits, and proof invalidation under changing WE mappings.
9. Define temporal proof systems for valid-time and observation-time corrections.
10. Formalize cross-perspective reconciliation without erasing disagreement.
11. Establish a machine-checkable granularity bridge language.
12. Classify lossless, lossy, and non-invertible aggregation operators.
13. Define uncertainty propagation across sampling, aggregation, and metric derivation.
14. Determine conditions under which group-level predicates can safely descend to members.
15. Specify probabilistic-to-deductive admission rules, if any, without proof laundering.
16. Establish proof-carrying plugin registration and revocation.
17. Measure the computational cost of proof tracing and fine-grained provenance.
18. Test robustness against adversarially generated rule and ontology changes.
19. Develop privacy-preserving proof traces for restricted premises.
20. Define multi-agent dispute resolution and independent proof verification.
21. Benchmark cross-domain transfer and negative-transfer detection.
22. Integrate formal proof checks with CDE candidate-state exploration at scale.
23. Characterize code-graph abstraction limits and unreachable-path semantics.
24. Determine when incremental proof invalidation is safe after state or membership changes.

These leftovers MUST remain visible in release and validation documents until independently resolved. Repeated execution and failed proof attempts MAY generate valuable relay evidence but MUST NOT be represented as validation success.

## 22. Release discipline and conclusion

SPEC-003 is a **research and contract artifact**, not a verified proof engine or a certified implementation. Any v1.0.0 release SHOULD report which conformance tests were actually executed, which formal results were proved, and which obligations remain open. A manuscript, schema sketch, or counterexample catalog is not an executed validation report.

The central design principle is simple: **preserve classical deductive validity where the formal embedding warrants it, and demand explicit semantic contracts whenever object-centric reasoning crosses relations, time, perspectives, or granularities.** Under that discipline, OCSRE can expand reasoning capability without silently confusing inference, evidence, scoring, or authorized evolution.
