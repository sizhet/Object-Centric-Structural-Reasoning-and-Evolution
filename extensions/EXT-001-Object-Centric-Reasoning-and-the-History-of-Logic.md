# EXT-001 — Object-Centric Reasoning and the History of Logic

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Release track:** v1.0.0 — Research Framework and Contracts  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**Status:** Historical and conceptual research extension; proposed architecture and validation obligations, not an established new logic or a verified conservative extension  
**License:** Apache-2.0  
**Companion papers:** OCSRE-001, OCSRE-002, OCSRE-003, OCSRE-004, OCSRE-007, OCSRE-008, OCSRE-009, OCSRE-010, OCSRE-011; SPEC-001, SPEC-002, SPEC-003, SPEC-005, SPEC-006; CASE-001, CASE-004, CASE-006

## Abstract

The history of logic is not a single progression from simple rules to increasingly complicated formulas. It includes distinct responses to distinct questions: what follows necessarily from premises; how quantified relations can be represented; how mathematical and computational proofs can be checked; what knowledge or belief an agent possesses; how truth varies across time or possible states; how action changes a state; and how uncertain evidence should affect a decision. Object-Centric Structural Reasoning and Evolution (OCSRE) proposes an engineering and research interface across several of these concerns. Its unit of integration is a contractually identified world entity (WE) and its typed object representation, rather than a replacement logical calculus. A restricted classical fragment must retain its original entailment semantics, while object identity, perspective, temporal state, metric differentials, compositional granularity, in-situ learning, and constrained delta evolution are added under separate contracts. This extension positions OCSRE against important logical traditions, identifies genuine conceptual inheritances and non-equivalences, sketches a layered semantics, and proposes falsifiable tests. The historical comparison is interpretive rather than a priority or originality claim. No universal soundness, completeness, decidability, or empirical performance result is asserted.

**Keywords:** history of logic; Aristotelian syllogistic; first-order logic; model theory; modal logic; temporal logic; dynamic logic; description logic; type theory; probabilistic reasoning; object-centric reasoning; WE; ODK; CDE; structural intelligence.

## 1. Research question and boundaries

**Question:** What does object-centric structural reasoning add to established logical methods, and what must it preserve rather than reinvent?

OCSRE addresses the integration problem: the same identified object may participate in deductive proofs, evidence-based hypotheses, metric comparisons, changing states, composite constraints, and learning feedback. These activities have different validity criteria. The research challenge is to provide a shared, auditable interface **without pretending they all constitute one kind of inference**.

This paper does not assert that historical logic lacked objects, relations, or state; nor that object orientation is a novel logical foundation. First-order logic already quantifies over individuals, and dynamic and temporal logics already represent change. OCSRE's proposed contribution is the *contract-governed composition* of established and exploratory capabilities around persistent WE identity and operational interfaces.

## 2. A disciplined historical map

| Tradition | Central problem | Representative formal resource | OCSRE relationship | Non-equivalence warning |
|---|---|---|---|---|
| Aristotelian syllogistic | Valid categorical inference | Terms, quantified categorical propositions | A restricted preservation benchmark | Not a general theory of changing object state |
| Stoic propositional reasoning | Consequence among propositions | Conditional and propositional inference | Rule-level proof obligations | Propositions are not WE identities |
| Fregean predicate logic | Quantification and relations | Variables, predicates, quantifiers | Reference semantics for restricted deduction | A WE graph is not itself a first-order interpretation |
| Tarskian model theory | Truth and consequence relative to interpretations | Models and satisfaction | Entailment criterion | Scores do not establish satisfaction in all models |
| Proof theory and type theory | Derivations and well-formed judgments | Proof rules, types, contexts | Proof artifacts and interface contracts | Type checking alone does not establish empirical truth |
| Modal and epistemic logic | Necessity, possibility, knowledge, belief | Accessibility relations and modal operators | Perspective-aware assertions | Agent confidence is not automatically knowledge |
| Temporal and dynamic logic | Truth over time and after actions | Time indices, transition relations, program modalities | Versioned state and typed delta transitions | An optimizer's proposed action is not a valid transition |
| Description and ontology logics | Structured concepts and roles | Concept/role axioms | Typed WE relations and schema bridges | Ontology membership is not identity resolution |
| Nonmonotonic and defeasible logic | Revisable conclusions | Defaults, priorities, exceptions | Hypothesis/evidence governance | A defeasible conclusion is not a theorem of classical premises |
| Probabilistic and decision reasoning | Uncertainty and choice | Probability models, utilities | Metric scores and decision policies | High probability is not deductive validity |

This map is selective, not an exhaustive chronology. Historical developments overlapped, and modern formalisms often combine several traditions.

## 3. Syllogistic reasoning: the value of a small sound core

The familiar example is:

1. Every human is mortal.
2. Socrates is human.
3. Therefore Socrates is mortal.

Its first-order rendering is:

```text
∀x (Human(x) → Mortal(x))
Human(s)
-------------------------
Mortal(s)
```

The conclusion follows by universal instantiation and modus ponens. The inference is valid **conditional on its premises**; neither premise's empirical truth is guaranteed by the inference form. In OCSRE, `s` must denote a stable individual within the declared interpretation, and `Human` and `Mortal` must retain their predicate meanings. A metric such as `similarity(s, prototypeHuman) = 0.97` cannot silently replace `Human(s)`.

OCSRE-002 and SPEC-003 treat this as a restricted preservation obligation. A successful implementation must produce the same consequence under an explicitly mapped fragment, or decline unsupported mappings. This is narrower and more defensible than claiming OCSRE subsumes all of classical logic.

## 4. Predicate logic: individuals were never absent

A common but misleading narrative says that traditional logic reasons about categories while OCSRE newly introduces objects. Predicate logic already reasons about individuals, n-ary relations, functions, and quantification. For example:

```text
Assigned(student17, trip8)
Operates(bus3, trip8)
∀s∀t (Assigned(s,t) → RequiresCoverage(s,t))
```

OCSRE instead asks how `student17` is *resolved* across databases, how the relation is scoped to a timetable version, whether an observation is authorized for a particular perspective, and which later state transition invalidates a cached derivation. These are integration and lifecycle concerns. They may be modeled formally, but are not absent from logical research.

A stable `WE-ID` is an engineered reference discipline, not a metaphysical proof of real-world identity. SPEC-001 governs its interpretation and reconciliation.

## 5. Model theory: consequence is not confidence

For premises Γ and conclusion φ, classical semantic consequence means:

`Γ ⊨ φ` iff every admissible interpretation satisfying Γ also satisfies φ.

OCSRE must not substitute a scalar score for this universal condition. Its Object Differential Kernel (ODK) may compute `Δmetric(o1,o2)` to compare objects, but the result is a typed measurement, not a derivation. A scoring threshold may trigger *review* or *hypothesis generation*; it must not produce `entailed` without a sound bridging rule.

A useful interface separates:

```text
DeductiveResult { conclusion, proof, semantics_version }
EvidenceResult  { hypothesis, evidence, uncertainty, provenance }
MetricResult    { metric_id, units, value, comparator_version }
DecisionResult  { proposal, policy, authorization_status }
```

These records may reference the same WE while retaining different epistemic statuses.

## 6. Proof theory and typed judgments

Proof theory emphasizes derivation rules and explicit assumptions. Type systems make some invalid expressions impossible to construct, but only within their declared guarantees. OCSRE can borrow both disciplines:

```text
Γ ⊢_F Human(s) : Proposition
Γ ⊢_F ∀x(Human(x) → Mortal(x)) : Proposition
Γ ⊢_F Mortal(s) : Proposition    [universal elimination, implication elimination]
```

Here `F` identifies the supported fragment and its version. A cross-granularity step, such as deriving `Safe(fleet)` from `Safe(bus3)`, requires a separate rule with its own conditions. It cannot inherit the proof status of a premise merely because the objects are related.

A practical proof artifact should include premise references, interpretation versions, rule IDs, state versions, and invalidation dependencies. Proof replay should fail when a required premise or interpretation is no longer applicable.

## 7. Modal and epistemic logic: whose claim, under what accessibility?

Modal logic asks what is necessary or possible across accessible worlds; epistemic logic can model what agents know or believe under specified accessibility relations. OCSRE's `PerspectiveRef` is an engineering field for a viewpoint, evaluation policy, or source context. It is **not automatically** an epistemic modal operator.

For example:

```text
AssertedBy(analystA, Controls(walletX, walletY))
SupportedBy(claim42, evidenceSet7)
```

Neither assertion entails `Controls(walletX, walletY)`, nor does it entail that analyst A *knows* the claim. Translating a perspective-qualified claim into epistemic logic would require explicit accessibility semantics and assumptions. This boundary is particularly important in CASE-004, where compositional identity is defeasible.

## 8. Temporal logic: the same object, different truth intervals

`Assigned(student17, trip8)` may hold on Monday but not Tuesday. A versioned assertion therefore needs valid time, observation time, and possibly transaction time. These axes should not be collapsed:

```text
Fact {
  predicate: Assigned,
  args: [student17, trip8],
  valid_interval: [2026-11-02T07:00, 2026-11-02T08:00),
  observed_at: 2026-11-02T09:10,
  state_version: schedule-v4
}
```

The record is illustrative. OCSRE does not claim temporal logic is novel; it proposes that temporal scope become mandatory where omission would change a conclusion. A cached proof from `schedule-v4` must not silently authorize action under `schedule-v5`.

## 9. Dynamic logic and CDE: action as a constrained transition

Dynamic logic distinguishes properties before and after programs or actions. OCSRE's WE-native Constrained Delta Evolution (CDE) can be viewed as a state-transition proposal framework:

`S --δ--> S'`, where `δ` is a typed candidate change.

This analogy is useful but incomplete. A valid CDE transition must satisfy domain constraints, state version preconditions, authority, provenance, and applicable policies. An optimizer can *propose* a change that improves a metric but fails a safety invariant.

For example, merging two bus duties may reduce fleet count while violating driver duty time or student arrival windows. The transition is rejected regardless of its score. CDE's M→N branching, path memory, NoSubtree, and loop-back controls are proposed search governance mechanisms, not established logical proof rules.

## 10. Description logic and ontology: types are not persons

Ontology languages describe classes and relations; their value includes tractable reasoning for selected fragments. OCSRE's typed objects can consume ontology constraints, but three mappings must be separated:

- `typeOf(WE, Person)` is a class-membership claim.
- `sameIdentity(WE1, WE2)` is an identity claim requiring distinct evidence.
- `memberOf(PersonWE, GroupWE)` is a relationship, not a license to transfer every property of the person to the group.

Similarly, `hasPart` and `partOf` do not generally transfer arbitrary predicates. A vehicle's safe status does not entail the fleet's safety; a fleet's average capacity does not determine every bus's capacity. SPEC-003 demands typed granularity bridges with explicit preconditions.

## 11. Nonmonotonic reasoning and defeasible identity hypotheses

Classical entailment is monotonic: adding premises cannot invalidate an existing entailment from the original premises under the same semantics. Real-world hypotheses are often defeasible: a new transaction record can overturn a tentative claim that two wallets share an operator.

OCSRE should maintain distinct result classes:

```text
ENTAILED       -- conclusion follows in declared formal fragment
SUPPORTED      -- evidence favors hypothesis under declared method
CONTESTED      -- credible competing hypotheses or counterevidence
UNKNOWN        -- evidence or semantics insufficient
RETRACTED      -- prior supported claim withdrawn with audit trail
```

`RETRACTED` describes an evidence-governance event, not necessarily a classical proof becoming invalid. A formal proof can become inapplicable when its source premises, scope, or version are withdrawn. The difference must remain visible.

## 12. Probability, measurement, and decision theory

A numerical metric can express utilization, latency, similarity, confidence, or estimated risk. These quantities have different mathematical interpretations. In particular:

`metric_similarity ≠ probability_of_identity ≠ logical_entailment ≠ authorization`.

An ODK comparator must declare units, direction, missing-value policy, uncertainty where relevant, and calibration requirements. If a risk model is probabilistic, its calibration must be measured on suitable data; an arbitrary 0–1 score must not be labeled a probability. A decision policy may use an estimated risk but remains a distinct governance layer.

## 13. Why the Object is an integration boundary

The central OCSRE proposal is not that an object replaces propositions. Instead, a WE-linked object acts as a stable anchor for multiple semantically separate interfaces:

```text
WE Identity / ObjectRef
  ├── Typed facts and relations → proof service
  ├── Evidence and provenance   → hypothesis service
  ├── Object[metricIndices]     → ODK comparator
  ├── Versioned state           → temporal query
  ├── Typed candidate deltas    → CDE evaluator
  ├── Policy and authority      → governance gate
  └── Feedback and trials       → in-situ learning / relay
```

Each branch requires a declared contract. A shared object address improves traceability but does not merge the semantics of the branches.

## 14. A layered semantics proposal

A conservative research design uses five layers:

**L0 — Identity and typing.** Resolve WE references, types, scopes, and versions. No inference is licensed by name similarity alone.

**L1 — Formal deduction.** Interpret a declared classical fragment with a reference semantics and proof checker. Only this layer issues `entailed` results under its supported rules.

**L2 — Evidence and measurement.** Manage hypotheses, observations, metric indices, ODK comparisons, and uncertainty. Results are `supported`, `contested`, or `unknown` unless separately proved.

**L3 — State transition and governance.** Propose typed deltas; verify constraints, policy, and authorization before committing state changes.

**L4 — Learning and relay.** Compare outcomes, retain negative trials, propose reusable plugins, and require target-domain conformance before promotion.

The layers are a proposed architecture, not a theorem of completeness or a requirement that every implementation use five runtime processes.

## 15. Restricted embedding: formal preservation obligation

Let `F` be a declared fragment of first-order logic with constants, unary predicates, universal quantification, and implication. Let `T` translate each constant to a resolved `WE-ID` and each predicate to a typed object assertion. Let `M` be a reference interpretation and `I(T(M))` the corresponding object-side interpretation.

A candidate preservation condition is:

`M ⊨ φ  iff  I(T(M)) ⊨ T(φ)` for every supported φ in F.

This condition requires a precise definition of `T`, `I`, and the admissible models. A practical conformance suite may first test soundness in the forward direction, then test counterexamples and the reverse direction. Such tests do **not** prove the property for all models. An eventual proof would require a formal semantics and induction or other suitable argument.

No such general proof is claimed here.

## 16. Worked example: three incompatible inferential moves

Consider a school transportation system:

```text
P1: ∀x (AssignedToRoute(x, R7) → NeedsPickup(x))
P2: AssignedToRoute(Student17, R7)
E1: GPS observation suggests Bus3 arrived late
M1: LoadRatio(Bus3, trip9) = 0.92
```

**Deduction:** `NeedsPickup(Student17)` follows from P1 and P2 under their shared scope.

**Evidence-based hypothesis:** GPS observations may support `LateArrival(Bus3, trip9)` but need time alignment, sensor provenance, and a threshold definition. This is not a consequence of P1 and P2.

**Metric comparison:** `LoadRatio = 0.92` is a measurement. Whether this violates a capacity or policy constraint depends on the denominator, observation basis, and threshold.

**State evolution:** Reassigning Student17 to another trip is a candidate delta; it requires coverage, capacity, time-window, and authorization checks. The deduction does not authorize the change.

This example shows why a unified WE reference is useful while inferential categories remain distinct.

## 17. Granularity and composition: the difficult bridge

OCSRE supports individual, group, system, and composite state objects. This introduces the risk of invalid upward and downward inheritance:

- `Safe(bus3)` does not imply `Safe(fleet)`.
- `AverageLoad(fleet) = 0.6` does not imply `Load(bus3) = 0.6`.
- `Controls(accountA, walletB)` does not imply `Controls(personP, walletB)` without identity evidence.
- `FunctionCalls(A, B)` does not imply that every behavioral effect of A is mediated by B.

A granularity bridge should specify source and target types, aggregation or decomposition operator, scope, required invariants, evidence, and a proof/evidence status. This aligns with SPEC-003 and the compositional cases CASE-003, CASE-004, and CASE-006.

## 18. Historical continuity versus proposed novelty

OCSRE's intellectual debts should be stated plainly. Objects, relations, quantification, modal and temporal semantics, typed programs, and evidence-sensitive inference all have substantial prior literatures. The potential research contribution is an *operational unification of interfaces*: persistent WE references, `Object[metricIndices]`, reusable ODK operators, typed plugins, in-situ feedback, CDE state containers, and governed capability relay.

That is an architectural hypothesis. Whether the architecture yields lower integration cost, fewer semantic errors, better traceability, or more useful capability transfer must be established through comparative experiments. Naming a unification does not demonstrate its utility.

## 19. Conformance obligations (HLC-001–HLC-020)

| ID | Proposed obligation | Failure to reject |
|---|---|---|
| HLC-001 | Declare supported formal fragment and interpretation | Unbounded validity claims |
| HLC-002 | Preserve classical entailment for supported cases | False negative on valid inference |
| HLC-003 | Reject invalid syllogistic forms | False positive proof |
| HLC-004 | Keep WE identity distinct from labels and row keys | False identity merge |
| HLC-005 | Declare predicate and relation signatures | Ill-typed inference |
| HLC-006 | Track premise and rule versions in proof artifacts | Stale proof replay |
| HLC-007 | Keep evidence support distinct from entailment | Score promoted to theorem |
| HLC-008 | Keep metric values distinct from probabilities | Uncalibrated confidence claim |
| HLC-009 | Require time-scope compatibility | Cross-version inference |
| HLC-010 | Require explicit perspective semantics | Attribution mistaken for truth |
| HLC-011 | Reject unsupported granularity inheritance | Individual-to-group fallacy |
| HLC-012 | Declare composite aggregation semantics | Mean substituted for individual |
| HLC-013 | Validate typed deltas against state constraints | Invalid state committed |
| HLC-014 | Separate candidate from authorized transition | Unauthorized action |
| HLC-015 | Track retractions and counterevidence | Hidden contradictory history |
| HLC-016 | Isolate proof checking from plugin score outputs | Plugin bypasses proof rules |
| HLC-017 | Preserve security scope through localization | Information leakage |
| HLC-018 | Require target-domain plugin conformance | Negative transfer |
| HLC-019 | Record unsuccessful and inconclusive relay trials | Selection bias in growth claims |
| HLC-020 | Report unverified theoretical claims as hypotheses | Overstated formal guarantees |

These obligations are proposed for a future conformance implementation; none is certified as passed by this document.

## 20. Reference tests and counterexamples

### 20.1 Positive tests (HLP-001–HLP-010)

| ID | Test | Expected result |
|---|---|---|
| HLP-001 | `∀x(H(x)→M(x)), H(s)` | `M(s)` entailed |
| HLP-002 | Same proof with stable renamed WE label | Entailment unchanged |
| HLP-003 | Typed two-step implication chain | Conclusion entailed |
| HLP-004 | Explicitly compatible time scopes | Inference accepted |
| HLP-005 | Proof replay with identical premise versions | Same result |
| HLP-006 | Metric difference with declared units | Typed metric result only |
| HLP-007 | Supported hypothesis with provenance | `supported`, not `entailed` |
| HLP-008 | Valid candidate delta with constraints and authority | Eligible for commit after gate |
| HLP-009 | Typed aggregation with explicit operator | Correct aggregate, scoped result |
| HLP-010 | Conforming cross-domain plugin with independent tests | Promotion eligible, not automatic |

### 20.2 Negative and adversarial tests (HLN-001–HLN-016)

| ID | Counterexample | Required behavior |
|---|---|---|
| HLN-001 | Affirming the consequent | Reject as invalid deduction |
| HLN-002 | Undistributed middle | Reject as invalid deduction |
| HLN-003 | Metric similarity substituted for predicate | Do not infer class membership |
| HLN-004 | Same display name, different WE identity | No identity merge |
| HLN-005 | Same WE, incompatible time intervals | No timeless conclusion |
| HLN-006 | Analyst belief presented as objective fact | Preserve perspective status |
| HLN-007 | Group mean used as individual value | Reject granularity bridge |
| HLN-008 | Member safety used to infer fleet safety | Reject unsupported aggregation |
| HLN-009 | Unsupported probability interpretation of score | Reject probability label |
| HLN-010 | Proposed delta violates driver constraint | Reject transition |
| HLN-011 | Valid candidate lacks execution authority | No commit |
| HLN-012 | Proof premise withdrawn or version changed | Invalidate or recheck proof |
| HLN-013 | Two correlated observations counted independently | Flag evidence dependence |
| HLN-014 | Wallet flow treated as proof of real-world identity | Reject identity conclusion |
| HLN-015 | Calling graph unchanged but security semantics altered | Require additional semantic checks |
| HLN-016 | Plugin passes source tests but fails target semantics | Reject promotion |

All tests are **designs with expected outcomes**, not records of executed test runs.

## 21. Hypothesis links and experimental comparisons

**OCSH-001:** The declared classical fragment can be preserved by a formally defined object translation. Test against a reference theorem prover and countermodels; seek a proof for a sufficiently small fragment.

**OCSH-006:** Explicit granularity contracts reduce invalid inheritance. Compare systems with and without typed bridges on a labeled cross-granularity benchmark.

**OCSH-002/003:** ODK and plugins can be reused across domains without changing kernel semantics. Compare adaptation effort, interface defects, and conformance pass rates against domain-specific implementations.

**OCSH-005:** WE-native CDE supports valid composite transitions. Compare constraint-violation rates and search quality under equivalent budgets.

**OCSH-008/009/010:** Capability relay and spillover may produce measurable new utility, but require target-domain tests, negative-transfer accounting, and longitudinal baselines. Repeated reuse alone does not prove open-ended scaling.

**OCSH-011:** Code governance may improve impact localization and traceability; test against calling-graph-only and conventional CI baselines. No equivalence between program behavior and call-graph structure is assumed.

Report task definitions, datasets, random seeds, evaluator independence, runtime budgets, and negative outcomes. Separate mathematical correctness from operational performance.

## 22. Explicit leftovers and open research questions

1. Formalize the exact supported classical fragment and translation function.
2. Prove or disprove restricted semantic preservation under stated assumptions.
3. Specify handling of equality, existential quantification, and empty domains.
4. Define proof invalidation under mutable premises and versioned schemas.
5. Distinguish valid time, observation time, and transaction time rigorously.
6. Define the formal interpretation, if any, of `PerspectiveRef`.
7. Clarify how contradictions are represented without trivializing classical proofs.
8. Choose a principled treatment of open-world versus closed-world assumptions.
9. Formalize typed granularity bridges for aggregates and composites.
10. Determine how uncertainty and missingness propagate through ODK operators.
11. Calibrate probabilistic outputs separately from heuristic scores.
12. Formalize authorization semantics for CDE transitions.
13. Establish termination and loop-back conditions for selected CDE searches.
14. Define cross-domain semantic equivalence and negative-transfer criteria.
15. Measure integration overhead relative to existing rule engines and graph systems.
16. Evaluate security and privacy effects of shared WE localization.
17. Specify the relationship to ontology reasoners and temporal databases.
18. Assess proof checker independence from AI-generated plugins.
19. Test whether in-situ learning improves outcomes without corrupting proof semantics.
20. Define meaningful longitudinal metrics for structural capability spillover.
21. Record historical interpretations and claims requiring specialist review.
22. Avoid treating conceptual synthesis as proof of historical novelty.
23. Define stable reproducible datasets for all conformance cases.
24. Determine which interfaces can be standardized without imposing a single runtime.

## 23. Research position and conclusion

Logic's history supplies multiple indispensable disciplines: validity, models, proofs, types, time, action, uncertainty, and revision. OCSRE should treat them as **complementary semantics**, not interchangeable operators. The proposed object-centric interface can make their interactions explicit: a WE identity anchors a claim, a proof establishes a consequence within a fragment, evidence supports a revisable hypothesis, a metric quantifies a property, a CDE delta proposes a constrained change, and a relay process tests whether a capability survives transfer.

The strongest defensible claim at this stage is therefore a research program: **preserve established logical guarantees where applicable, expose boundaries between different forms of reasoning, and test whether a shared object interface improves structural intelligence engineering.** Its value remains contingent on formalization, counterexamples, independent conformance, and empirical comparison.

## References and further reading (selected historical anchors)

These are orientation references, not evidence that OCSRE is a theorem or that the named authors anticipated its architecture.

- Aristotle, *Prior Analytics* — categorical syllogistic and valid argument forms.
- Gottlob Frege, *Begriffsschrift* (1879) — quantified logical notation and inference.
- Alfred Tarski, “On the Concept of Logical Consequence” (1936) — semantic consequence.
- Gerhard Gentzen, “Investigations into Logical Deduction” (1934–1935) — proof-theoretic calculi.
- Saul Kripke, “A Completeness Theorem in Modal Logic” (1959) — modal semantics and completeness results.
- Arthur Prior, *Time and Modality* (1957) — temporal logic foundations.
- Vaughan Pratt, “Semantical Considerations on Floyd-Hoare Logic” (1976) — program and dynamic reasoning.
- Ronald Fagin, Joseph Halpern, Yoram Moses, Moshe Vardi, *Reasoning About Knowledge* (1995) — epistemic logic.
- Franz Baader et al. (eds.), *The Description Logic Handbook* (2003) — description logics and reasoning.
- John McCarthy, “Circumscription—A Form of Non-Monotonic Reasoning” (1980) — nonmonotonic inference.

---

**Repository placement:** `extensions/EXT-001-Object-Centric-Reasoning-and-the-History-of-Logic.md`  
**Release note:** Conceptual research extension only; no formal preservation theorem, conformance certification, or empirical scaling result is claimed.
