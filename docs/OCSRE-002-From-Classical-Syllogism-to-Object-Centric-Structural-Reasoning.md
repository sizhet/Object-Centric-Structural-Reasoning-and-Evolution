# OCSRE-002 — From Classical Syllogism to Object-Centric Structural Reasoning

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Release track:** v1.0.0 — Research Framework and Contracts  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**Status:** Research proposal and formalization sketch; no proof of a general conservative extension or empirical validation is claimed  
**License:** Apache-2.0

## Abstract

Classical syllogistic reasoning provides a small, transparent example of validity-preserving inference. Object-Centric Structural Reasoning and Evolution (OCSRE) proposes to retain such inference as a **restricted, testable subsystem**, while enabling reasoning over identified world entities (WEs), typed relationships, time-indexed state, metric comparisons, perspective-dependent evidence, and variable granularity. This paper specifies an initial translation from categorical predicates to object-level assertions, separates logical consequence from defeasible evidence and policy decisions, and identifies conditions under which familiar syllogisms remain valid. It then outlines a progression from static deduction to dynamic structural reasoning, with explicit contracts for identity, quantification, type, temporal scope, provenance, and uncertainty. The objective is not to replace logic with object graphs, nor to claim that richer structures inherit validity automatically. Rather, the objective is to make classical validity a **conformance obligation** within a broader, auditable reasoning interface.

**Keywords:** categorical logic; syllogism; world entity; object-centric reasoning; typed relation; temporal logic; multi-granularity; epistemic governance; structural intelligence; conformance.

## 1. Motivation: preserve what logic guarantees, extend what it can describe

A classical syllogism is compelling because a conclusion follows from premises by form, not because a system is confident about it. Consider:

1. All humans are mortal.
2. Socrates is human.
3. Therefore Socrates is mortal.

This is a valid first-order inference when the two premises are true and the name denotes an individual in the domain. The conclusion does not require a numerical similarity score or a learned heuristic. OCSRE must preserve that distinction.

Real-world reasoning also asks whether Socrates refers to the same entity across records; when a statement holds; whose perspective supplied it; how evidence was obtained; whether a class label applies at the current granularity; and what should change when new evidence arrives. These questions are not resolved merely by drawing an object graph. They require additional semantics and explicit contracts.

**Central research question:** Can a contract-governed object interface host a sound restricted embedding of classical deduction while supporting richer, explicitly qualified structural inferences?

## 2. Scope and terminology

OCSRE uses **WE** for a world entity and **Object** for its contractually accessible representation. A WE identity is not identical to a database key, graph node label, type name, or momentary state. An object assertion can be expressed schematically as:

```text
Assertion {
  subject: WE-ID,
  predicate: Predicate-ID,
  object_or_value: WE-ID | TypedValue,
  logical_scope: {quantifiers, domain, assumptions},
  temporal_scope: interval | instant | timeless,
  perspective: Perspective-ID | objective-formal,
  provenance: EvidenceRef[],
  epistemic_status: asserted | derived | hypothesized | disputed,
  validity_status: valid | invalid | unknown,
  version: StateVersion
}
```

This is a **conceptual record**, not a mandatory serialization or implementation. The formal core below uses only a subset. Rich metadata must not alter a proof's truth conditions unless the reasoning system declares additional semantics.

A **metric** is a typed, meaning-bearing observable or derived attribute; `Object[metricIndices]` is a candidate access interface, not a license to treat every numeric comparison as logical implication. A **relation** has a declared signature and interpretation. A **perspective** qualifies a claim or its evidence, not automatically its truth in classical logic. A **delta** is a typed change to an object or composite state, subject to constraints and validation.

## 3. A restricted classical core

### 3.1 Syntax and model

Let a classical signature contain a nonempty domain `D`, unary predicates `A`, `B`, `C`, and constants such as `s`. A model `M` assigns each predicate a subset of `D` and each constant an element of `D`. Classical negation, conjunction, implication, and quantification have their standard two-valued first-order meanings.

For example:

```text
∀x (Human(x) → Mortal(x))
Human(s)
────────────────────────
Mortal(s)
```

The schema is valid in every classical model satisfying the premises. **Validity is distinct from whether the premises are actually true** in a deployed knowledge base.

### 3.2 Categorical forms

For unary predicates `S` and `P`:

| Form | Classical reading | First-order representation |
|---|---|---|
| A | All S are P | `∀x (S(x) → P(x))` |
| E | No S are P | `∀x (S(x) → ¬P(x))` |
| I | Some S are P | `∃x (S(x) ∧ P(x))` |
| O | Some S are not P | `∃x (S(x) ∧ ¬P(x))` |

In modern first-order semantics, a universal affirmative does **not** entail that any `S` exists. Any syllogistic rule relying on existential import needs an explicit existence premise or a separately declared alternative semantics.

### 3.3 Safe example and unsafe near-neighbor

**Valid (Barbara):**

```text
∀x (M(x) → P(x))
∀x (S(x) → M(x))
──────────────────
∀x (S(x) → P(x))
```

**Invalid conversion:** `∀x (S(x) → P(x))` does not entail `∀x (P(x) → S(x))`. If all buses are vehicles, it does not follow that all vehicles are buses. A graph traversal that treats `is-a` edges as bidirectional violates this elementary contract.

## 4. Translating classical predicates into object assertions

Define a translation `T` over the restricted signature:

```text
T(P(c))       = HasType(object(c), P)
T(¬P(c))      = NotHasType(object(c), P)
T(P(x))       = HasType(object(x), P)
T(φ ∧ ψ)      = T(φ) ∧ T(ψ)
T(φ → ψ)      = T(φ) → T(ψ)
T(∀x φ)       = ∀x T(φ)
T(∃x φ)       = ∃x T(φ)
```

Here `object` is an identity-preserving map from domain individuals to WE handles. `HasType` is interpreted as the original predicate extension; `NotHasType` represents **classical negation**, not absence of a type record. For a faithful embedding, the object model must represent the same domain and predicate interpretations, or specify an isomorphism preserving satisfaction. Object metadata is ignored by `T` unless explicitly included in the signature.

### 4.1 Preservation target, not a completed theorem

For a class of restricted classical models `K`, the intended obligation is:

```text
For every M in K and every classical formula φ:
    M ⊨ φ  iff  F(M) ⊨ T(φ)
```

where `F(M)` is an object interpretation constructed from `M`. If this satisfaction-preservation property is proved, consequence preservation follows for translated premises and conclusions **within the image of the restricted translation and its specified model class**. The present paper gives the construction sketch and test obligations, **not a completed formal proof**, and makes no general claim that unrestricted OCSRE is a conservative extension of first-order logic.

### 4.2 Preconditions for a faithful mapping

- **Identity:** each classical individual has a stable, unambiguous referent; merges and splits are explicit.
- **Predicate meaning:** type names have fixed interpretations within the proof context.
- **Domain and quantifiers:** `all` and `some` range over a declared domain, not just the currently retrieved rows unless that restricted domain is intentional.
- **Negation:** explicit falsehood is not conflated with missing information.
- **Scope:** all translated premises and conclusions share compatible temporal and perspective scopes, or are intentionally timeless.
- **Inference:** the restricted engine uses sound logical rules, not unverified similarity propagation.

## 5. From static predicates to object-centric structural assertions

The broader object layer may expose:

```text
WE(id, type, stateVersion)
Relation(subjectWE, relationType, objectWE, scope)
Metric(WE, metricID, value, unit, time, perspective)
Evidence(assertionID, source, provenance, confidenceMetadata)
Constraint(stateContainer, invariant)
```

These records provide additional *questions*, not automatic answers. For example, `owns(person, vehicle)` and `vehicleIsElectric(vehicle)` do not imply `personIsElectric(person)`. A domain-specific rule must declare how a relation supports an inference, with a soundness justification or a defeasible status.

### 5.1 Typed relational inference

Suppose a rule is explicitly declared:

```text
∀x∀y ((AssignedDriver(x,y) ∧ CertifiedFor(x, ClassOf(y)))
      → AuthorizedToDrive(x,y))
```

The inference is classical only if the predicates and rule are interpreted as stated. Whether `AssignedDriver` or `CertifiedFor` is correctly observed is a separate evidence question. No universal rule of the form “related objects inherit each other's properties” is valid.

### 5.2 Metric reasoning is not categorical deduction

A comparison `Object[metricIndices]` may yield a differential vector:

```text
Δ_metric(a,b,p,t) = CompareTyped(Metric(a,p,t), Metric(b,p,t))
```

The comparator must check unit, normalization, missingness, perspective, and measurement provenance. A small distance between two objects can support a similarity hypothesis; it does not entail identical type, identity, authorization, or behavior. An Object Differential Kernel should return typed results and unresolved dimensions rather than silently converting scores into proofs.

## 6. Time, state, and change

A statement such as `Enrolled(student, school)` can change over time. If an object is enrolled at `t1` and transferred at `t2`, it is unsound to combine an unqualified `Enrolled(student, schoolA)` premise from `t1` with a current-state rule at `t2`.

Use explicit state- or time-indexed predicates when necessary:

```text
Enrolled(student, schoolA, t1)
Transfer(student, schoolA, schoolB, Δ, t1→t2)
Enrolled(student, schoolB, t2)
```

A typed delta may propose or record a transition; its effect is not established until constraints and relevant observations validate the new state. Some facts are persistent, some are transient, and some are derived under a policy. Persistence rules require their own contracts. A **time-slice classical proof** is valid only relative to premises that hold within the same declared interpretation.

## 7. Granularity and composite objects

OCSRE supports objects at multiple granularities: person, household, vehicle, route, school, fleet, transaction, account, or inferred actor cluster. A composite WE may have aggregate properties not possessed by each member, and vice versa.

Examples of **invalid unlicensed inference**:

- A fleet's average capacity is 40; therefore each bus has capacity 40.
- A school district is compliant; therefore every individual route is compliant.
- Two transactions belong to the same inferred cluster; therefore they have the same verified human owner.
- A function belongs to a safe module; therefore the function is safe under every calling context.

Cross-granularity movement requires a declared operator such as `aggregate`, `project`, `memberOf`, `contains`, or `derive`, with explicit semantics, scope, and evidence. **No default inheritance across granularity boundaries** is permitted. This requirement is central to `OCSH-006` and `SPEC-003`.

## 8. Multiple perspectives and epistemic separation

A source's claim, an agent's belief, a model prediction, and a formally derived theorem occupy different epistemic categories:

| Category | Example | Permitted treatment |
|---|---|---|
| Deductive consequence | `Mortal(s)` from valid premises | Mark as derived, conditional on premises |
| Observational assertion | “sensor reports location L” | Record source, time, calibration, reliability |
| Statistical hypothesis | “cluster C may share an actor” | Score and test; do not promote to identity fact |
| Policy decision | “approve assignment” | Check authority, constraints, and audit trail |
| Counterevidence | “source B disputes type P” | Preserve conflict and qualification |

Perspectives may disagree without making classical logic inconsistent **within each separately scoped theory**. Combining contradictory premises into one unrestricted classical theory risks triviality by explosion. The system should detect scope collisions, quarantine inconsistent contexts, or employ a separately specified nonclassical reasoning mode. It must not quietly claim ordinary classical entailment after changing the logic.

## 9. In-situ learning without proof laundering

In-situ learning updates an object's evidence, metrics, rule candidates, or policies through feedback tied to the correct WE identity and state version. It must distinguish:

1. **Observed:** a feedback event occurred.
2. **Inferred:** an explicitly named rule or model produced a conclusion.
3. **Validated:** a designated test or independent evidence supports promotion.
4. **Promoted:** an authorized process changes a shared object state or reusable rule.

A high-confidence learned association is not a theorem. A failed inference should leave an explicit residual: missing premises, scope mismatch, ambiguous identity, type incompatibility, contradictory evidence, or unvalidated operator. This preserves the repository's **Explicit Leftover** principle and connects reasoning to `OCSRE-007`, `OCSRE-009`, and `SPEC-005`.

## 10. Constrained evolution and reasoning over possible states

WE-native CDE introduces a State-Container `S` holding one WE or a constrained composite of WEs and relations. A candidate transition has the form:

```text
(S, Δ_typed, constraints, evidence) → Validate → S'
```

The reasoning engine may establish that a proposed state satisfies a formal invariant, but this is not proof that an external action has been executed or that the physical world has reached `S'`. State changes require ownership, permission checks, validation, and, where possible, rollback or compensation. Irreversible external actions need a separate authorization boundary.

For school-bus scheduling (`CASE-003`), a route delta might reduce fleet count while violating capacity or travel-time constraints; the candidate must be rejected or revised. For code governance (`CASE-006`), a Calling Graph can locate possible impact, but function-call edges alone cannot establish program correctness: data flow, control flow, contracts, security boundaries, and regression evidence remain necessary. These are illustrations of the same distinction between **reasoning about a state** and **authorizing a state transition**.

## 11. Architectural interface and proof boundaries

```text
Classical formulas and proof rules
             │  restricted translation T
             ▼
Object assertions ── identity / type / scope / provenance contracts
             │
             ├── Classical proof adapter (sound rules only)
             ├── Typed relational reasoning plugins
             ├── Object Differential Kernel / Object[metricIndices]
             ├── Temporal and multi-granular operators
             ├── Evidence and perspective governance
             └── WE-native CDE candidate-state reasoning
                         │
                         ▼
                Conformance + validation
                         │
                 promoted / rejected / residual
```

**Figure insertion:** `../figures/Fig-002-From-Classical-Syllogism-to-Object-Centric-Reasoning.png` is the planned primary illustration. The PNG is not included or claimed as complete in this document.

OCSRE reuses WE-SIO identity and object semantics, UTN/MDT/WE-HDT addressing and differential localization, SIF's structural-intelligence context, CDE's constrained state evolution, and UIERU/ISGFTR's relay and spillover research framing. These are interface relationships, **not assertions of algorithmic equivalence**. MLIU and other prior pieces may be integrated through separately specified adapters rather than assumed dependencies.

## 12. Contract-first conformance requirements

The definitive contract is planned for `../specs/SPEC-003-Classical-Reasoning-Preservation-and-Granularity-Contract.md`; identity and epistemic boundaries are also addressed by `SPEC-001` and `SPEC-005`. The following are proposed acceptance criteria, not completed test results.

| ID | Priority | Conformance obligation | Example negative test |
|---|---|---|---|
| CR-001 | P0 | Preserve validity of translated restricted classical inferences | Reject reverse `is-a` inference |
| CR-002 | P0 | Preserve quantifier domain and existential-import semantics | Universal statement over empty subclass must not imply existence |
| CR-003 | P0 | Distinguish explicit negation from unknown/missing | Missing `P(a)` must not entail `¬P(a)` |
| CR-004 | P0 | Resolve identity with declared mapping and ambiguity handling | Same display name must not merge WEs |
| CR-005 | P0 | Enforce compatible time and perspective scopes | Do not combine conflicting time slices without rule |
| CR-006 | P0 | Require typed relational and cross-granularity operators | Fleet average must not propagate to each vehicle |
| CR-007 | P0 | Separate proof status from confidence/evidence scores | Similarity 0.99 must not imply identity |
| CR-008 | P0 | Expose unresolved premises, conflicts, and residuals | Contradiction must not silently become proof |
| CR-009 | P1 | Preserve provenance across derivation chains | Derived claim must retain premise references |
| CR-010 | P1 | Detect regressions when object plugins change | Replacing comparator must not alter classical core |

### 12.1 Suggested test corpus

**Positive:** Barbara; Celarent; Darii; Ferio; individual instantiation; chained subtype inclusion with fixed semantics.  
**Negative:** affirming the consequent; invalid conversion; illicit existential import; open-world negation; type confusion; temporal mismatch; perspective mismatch; composite-to-member inheritance; similarity-to-identity promotion; contradictory-premise mixing.

Tests should include generated finite-model counterexamples and, where feasible, independent theorem-prover or model-checker cross-validation. The proposal does not claim that such tests have been run.

## 13. Research hypotheses and evaluation

This paper directly elaborates:

- **OCSH-001:** A restricted OCSRE subsystem can preserve classical deductive validity.
- **OCSH-006:** Explicit cross-granularity contracts reduce invalid inheritance and aggregation.

It also supplies reasoning-related conditions for **OCSH-002** (kernel reuse), **OCSH-004** (traceable in-situ learning), **OCSH-005** (WE-native state transitions), and **OCSH-011** (code-governance impact localization).

A falsifiable evaluation should compare (a) a trusted classical logic baseline, (b) a naïve object-graph reasoner, and (c) a contract-governed OCSRE prototype. Measure soundness violations, missed valid inferences, granularity errors, scope collisions, traceability, unresolved-case detection, and adaptation cost. Use held-out examples and adversarial counterexamples; report coverage and negative results. The relevant hypothesis registry is `../research-trace/HYPOTHESIS-REGISTRY.md`, and the release-level protocol belongs in `../VALIDATION-ROADMAP.md`.

**Hypothesis status:** Proposed / E0 — no empirical validation is asserted.

## 14. Limitations and explicit leftovers

1. **Formal proof incomplete.** The translation and satisfaction-preservation target require a rigorous model-theoretic proof for a fixed restricted language.
2. **No universal inheritance rule.** Arbitrary graph edges and type hierarchies do not inherit syllogistic validity.
3. **Open-world and contradictory data.** A deployed evidence system needs explicit semantics for absence, disagreement, and inconsistent contexts.
4. **Temporal and modal semantics.** Persistence, possibility, belief, obligation, and counterfactual claims require separate formal systems and cannot be smuggled into classical rules.
5. **Identity uncertainty.** Inferred or composite identities must remain distinct from verified individual identity.
6. **Metric meaning.** Normalization and similarity require typed units, source provenance, and threshold governance.
7. **Runtime absent.** No general-purpose engine, benchmark results, or cross-domain deployment is claimed.
8. **Evolution governance.** A logically consistent proposed state may still be unauthorized, unsafe, or practically infeasible.
9. **Scaling unproven.** More plugins or richer object representations do not by themselves establish improved reasoning or a scaling law.

Each unresolved issue should remain visible in `../research-trace/UNRESOLVED-RESIDUALS.md` and, when appropriate, the counterexample and decision registries.

## 15. Companion-document map

| Companion | Intended role |
|---|---|
| `OCSRE-001-The-Object-Centric-Structural-Intelligence-Thesis.md` | Overall object-centric research thesis |
| `OCSRE-003-Dynamic-Relational-and-Multi-Granular-Reasoning.md` | Dynamic, relational, perspective-aware and multi-granular reasoning |
| `OCSRE-004-Object-Differential-Kernel-and-Generic-Operators.md` | Typed differential comparisons and generic operators |
| `OCSRE-007-In-Situ-Object-Learning-Decision-and-Feedback.md` | Feedback and local object learning |
| `OCSRE-008-WE-Native-CDE-and-Composite-State-Evolution.md` | State-container and typed-delta evolution |
| `OCSRE-009-Epistemic-Separation-and-Object-Centric-Evidence-Governance.md` | Evidence, provenance, uncertainty and epistemic status |
| `SPEC-003-Classical-Reasoning-Preservation-and-Granularity-Contract.md` | Normative preservation and granularity tests |
| `CASE-001-Person-and-Classical-Reasoning.md` | Minimal syllogistic worked example |
| `CASE-006-AI-Generated-Code-Governance-Through-Calling-Graphs-and-CDE.md` | Qualified reasoning about code impact and transitions |
| `EXT-001-Object-Centric-Reasoning-and-the-History-of-Logic.md` | Historical and logical context, including competing formalisms |

These names refer to the **planned repository structure**; listing a companion does not imply that its content has already been authored.

## 16. Conclusion

The route from classical syllogism to object-centric structural reasoning should be a **disciplined expansion of expressive interfaces**, not an erosion of logical guarantees. Classical deduction supplies a small, rigorous core; WE identity, typed relations, metric comparisons, temporal scope, granularity, provenance, and perspective provide additional structure. Each additional capability must declare its own semantics and validation boundary. The OCSRE proposition is that this separation—**Specifications/Contracts First, Conformance Before Runtime, Explicit Leftover**—can make object-centric reasoning interoperable with in-situ learning, constrained state evolution, and collective relay while keeping valid deduction distinguishable from plausible inference.

---

**Research integrity note:** All architecture, contract and hypothesis statements in this paper are proposals unless explicitly identified as established classical logical results. No runtime conformance, cross-domain performance gain, or scaling-law validation is claimed.
