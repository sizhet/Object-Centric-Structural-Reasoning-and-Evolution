# OCSRE-003 — Dynamic, Relational, and Multi-Granular Reasoning

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Release track:** v1.0.0 — Research Framework and Contracts  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**Status:** Research framework and proposed contracts; formal completeness and empirical performance are not claimed  
**License:** Apache-2.0

## Abstract

Object-centric reasoning must account for more than static classification. A world entity (WE) changes state, participates in typed relationships, appears under different perspectives, and may be represented at several levels of granularity. An inference that is sound for one entity, time interval, relation type, or aggregation level may fail when transferred to another. This paper develops a contract-first framework for **dynamic, relational, and multi-granular structural reasoning** over stable WE identities and versioned states. It distinguishes entity identity from state, class membership from relational evidence, object-level properties from aggregate properties, and deductive consequence from defeasible or probabilistic assessment. A conceptual object assertion and a typed reasoning pipeline are proposed, along with temporal, relational, granularity, perspective, and provenance guards. Worked counterexamples show why unqualified inheritance, temporal projection, relation composition, and composite-state updates must be rejected. The paper positions these mechanisms between the classical-validity subsystem of OCSRE-002 and the Object Differential Kernel of OCSRE-004, while preparing interfaces for in-situ learning, WE-native Constrained Delta Evolution (CDE), SIF localization, and collective relay. All mechanisms remain proposals pending conformance testing.

**Keywords:** world entity; object-centric reasoning; dynamic state; typed relation; temporal scope; multi-granularity; perspective; differential comparison; composite state; conformance; structural intelligence.

## 1. The problem: reasoning when objects are not static

Classical deduction can determine what follows from a fixed set of premises under an explicitly chosen logic. OCSRE-002 establishes the preservation of such validity as a restricted conformance target. Real systems also need to reason about **which object**, **in which state**, **at which time**, **through which relation**, **at what granularity**, and **under whose evidence or policy perspective** a conclusion applies.

For example, a bus may have sufficient seating capacity, yet an assignment of students to that bus may violate route-duration or pickup-window constraints. A transaction may be linked to a wallet, but that relationship does not establish the identity of the human controlling it. A software function may call another function, but the call edge alone does not prove data dependence or security impact. In each example, the reasoning error is not merely numerical: it is a failure to preserve semantic scope.

**Thesis:** A shared object interface can support richer reasoning only when identity, temporal validity, relational signatures, granularity transformations, evidence status, and constraint ownership are explicit and checked before a conclusion is promoted.

The aim is a reusable *reasoning interface*, not a claim that all domain-specific reasoning reduces to one universal algorithm.

## 2. Foundational distinctions and notation

Let `W` be the set of identified world entities. An entity `w ∈ W` has a stable identifier within a declared identity regime, while its state may change across time or versions. A perspective `p ∈ P` may select observable metrics, evidence, valuation rules, and permissible operations. A granularity descriptor `g ∈ G` identifies the level at which a claim is made: attribute, individual object, group, subsystem, or composite system, for example.

A conceptual object view is:

```text
ObjectView(w, t, p, g, v) = {
  identity: WE-ID,
  type: TypeRef,
  state: StateRef(version=v, valid_at=t),
  metrics: MetricRef[],
  relations: RelationRef[],
  perspective: PerspectiveRef(p),
  granularity: GranularityRef(g),
  evidence: EvidenceRef[],
  constraints: ConstraintRef[]
}
```

This notation is **illustrative**, not a mandated storage schema. It is compatible with the candidate `Object[metricIndices]` interface described in OCSRE-001, provided metric access is type-checked and does not silently alter identity, time, or perspective.

An assertion can be represented conceptually as:

```text
Claim = (
  subject, predicate, object_or_typed_value,
  valid_time, observed_time, state_version,
  granularity, perspective, provenance,
  inference_kind, epistemic_status, assumptions
)
```

`valid_time` describes when a claim is supposed to hold; `observed_time` describes when it was recorded. Their distinction matters for delayed, corrected, or retrospective evidence. Neither a source row key nor a graph node label automatically establishes WE identity.

### 2.1 Five non-equivalences

1. **Identity ≠ state:** an entity can persist while its attributes change.
2. **Type ≠ evidence:** a type declaration does not certify a particular observation.
3. **Relation ≠ inference rule:** an edge does not imply transitivity, symmetry, or causation unless its contract says so.
4. **Aggregate ≠ member:** a group property need not be inherited by each constituent, and vice versa.
5. **Score ≠ proof:** a metric similarity or probabilistic confidence is not a logical entailment.

These distinctions are mandatory semantic guards, not optional implementation details.

## 3. Dynamic reasoning: identity across changing states

A minimal state model separates an entity's identity from a versioned state:

```text
State(w, v0) --Delta(d1)--> State(w, v1)
```

A delta may change metric values, relationships, membership, or the validity of assertions. It must not silently replace the subject's identity. If the identity changes through a merge, split, reassignment, or re-identification, that operation requires an explicit identity-transition contract and provenance.

### 3.1 Temporal qualification

Consider:

```text
Available(bus-7, [08:00, 08:30])
Assigned(bus-7, route-A, [08:10, 09:00])
```

Availability at 08:05 does not entail availability at 08:45. A valid inference must carry or derive a temporal scope, and must reject unsupported projection beyond that scope. Intervals should specify boundary conventions; two claims cannot be joined simply because their timestamps are numerically close.

A conceptual guarded rule is:

```text
CanUse(w, task, interval I)
  only if TypeCompatible(w, task)
      and StateValid(w, I)
      and RequiredConstraintsHold(w, task, I)
      and PermissionsAllow(w, task, I)
```

This is a *policy-dependent eligibility rule*, not a theorem of classical logic. Its premises and conclusion must be auditable.

### 3.2 Event time, observation time, and revision

Late-arriving evidence may revise an earlier conclusion without implying that the underlying entity traveled backward in time. The framework therefore distinguishes:

- state transitions in the modeled world;
- observations or reports about those transitions;
- revisions to the knowledge base;
- proposed future transitions in a sandbox.

A revised observation should preserve a trace to the superseded claim. A speculative future state must not be promoted as an observed fact.

### 3.3 Persistence and frame conditions

A delta changes only the fields and relations authorized by its contract. Other properties should not be assumed invariant merely because they were not listed; persistence requires a declared frame condition, version dependency, or explicit revalidation. This avoids both needless global recomputation and unsound carry-forward.

## 4. Typed relational reasoning

Relationships should be represented with declared domain, range, cardinality, temporal scope, and applicable inference laws:

```text
RelationContract {
  relation_id,
  domain_type,
  range_type,
  cardinality,
  temporal_semantics,
  allowed_compositions,
  properties: [symmetric?, transitive?, functional?],
  provenance_requirements,
  authorization_policy
}
```

An edge `R(a,b)` may be valid without `R(b,a)`. Likewise, `R(a,b)` and `R(b,c)` do not imply `R(a,c)` unless transitivity is explicitly established for that relation and the relevant temporal and type scopes match.

### 4.1 A relation-composition example

Suppose:

```text
MemberOf(student-1, class-3)
LocatedIn(class-3, school-9)
```

It may be useful to infer that the student is associated with the school, but the new relation should be named and specified, e.g. `AffiliatedWith(student-1, school-9)`. It is generally incorrect to infer `LocatedIn(student-1, school-9)` at every moment, especially when the student is absent. **Relation composition must produce the relation its rule licenses**, not an arbitrary reused edge label.

### 4.2 Hyper-relations and contextual roles

Some facts involve more than two participants: a student is assigned to a particular bus on a particular route at a particular pickup time. Encoding this as independent binary edges can lose the binding among participants. OCSRE therefore permits a typed relation object or event object with named roles and its own WE-like identity where justified:

```text
Assignment {
  student, bus, route, pickup_stop, pickup_window,
  valid_interval, state_version, evidence
}
```

This is a representational option, not a requirement that every relation be reified.

## 5. Multi-granular reasoning: the central semantic risk

A WE can be viewed at multiple granularities. For a school-bus system, useful levels include seat, student, vehicle, route, fleet, and district. For code governance, levels include statement, function, module, service, and application. A granularity transition changes what a claim *means*, not only how much data it contains.

### 5.1 Aggregation requires a declared operator

Let `children(c)` denote members of a composite object `c`. An aggregate metric may be defined as:

```text
Capacity(c) = SUM(Capacity(w) for w in children(c))
```

But this rule is valid only when the child capacities are commensurable, non-overlapping under the intended interpretation, temporally aligned, and not double-counted. A fleet's summed seat capacity does not establish that every route can be served: geography, schedule, accessibility, and allocation constraints remain.

Typical transformation classes include:

| Transformation | Example | Required guard |
|---|---|---|
| Roll-up | students → class count | membership and deduplication |
| Drill-down | fleet → bus states | authorized member access |
| Bucketize | ages → age bands | interval definition and boundary policy |
| Normalize | travel times → scaled scores | units, reference population, version |
| Combine | capacity and duration → eligibility | compatible types and explicit rule |
| Derive | route graph → estimated delay | assumptions, model, uncertainty |

These operators also anticipate SQL-to-WE semantic transformations in OCSRE-006. A SQL `GROUP BY` result is not automatically a new real-world entity; the identity and granularity contract must say what the grouped row represents.

### 5.2 Inheritance is not automatic

From `Efficient(fleet-A)` one cannot infer `Efficient(bus-7)`. From `HighRisk(transaction-group)` one cannot infer that every transaction is high-risk. Conversely, a member property may not survive aggregation: each segment being locally short does not guarantee that a concatenated route meets a global travel-time constraint.

An inheritance rule needs a declared direction and sufficient conditions:

```text
Lift:    MemberClaims + AggregationContract -> CompositeClaim
Project: CompositeClaim + ProjectionContract -> MemberClaim
```

Without the appropriate contract, the correct result is **unsupported**, not false and not silently accepted.

### 5.3 Composite identities and overlap

Composite objects may overlap, nest, or change membership. A route can share a vehicle with another route at different times; a software function can participate in multiple calling paths. Aggregation must therefore carry membership version, overlap semantics, and the intended counting unit. This is particularly important when a composite object becomes a CDE State-Container.

## 6. Perspectives: multiple views without contradictory truth promotion

A perspective selects relevant metrics, thresholds, costs, and evidence priorities. For a bus assignment, a district planner may prioritize vehicle count, a parent may prioritize ride time, and a safety officer may enforce non-negotiable capacity and route constraints. These are different **evaluation perspectives**, not automatically different physical facts.

```text
Perspective {
  perspective_id,
  selected_metrics,
  scoring_policy,
  admissible_evidence,
  authority_scope,
  hard_constraints,
  version
}
```

A claim must distinguish at least:

- **formal/deductive:** follows from explicit premises under a declared logic;
- **observational:** supported by identified measurements or records;
- **estimated:** model-based with uncertainty;
- **hypothetical:** proposed but unverified;
- **normative/policy:** prescribed or preferred by a declared authority.

Two perspectives can rank the same state differently without either changing its observed seat count. A perspective-specific risk score must not be recast as an objective fact without its scoring contract.

### 6.1 Conflicting evidence

When two sources disagree about a metric, the framework should preserve source-specific claims and expose the disagreement. A resolver may select one estimate under a declared policy, but the competing evidence and unresolved residual remain traceable. No majority vote or learned score may silently transform contested evidence into a logical axiom.

## 7. Differential comparison and reasoning

The candidate **Object Differential Kernel** compares typed object views, metrics, or relations. A comparison request can be expressed as:

```text
Compare {
  left: ObjectView,
  right: ObjectView,
  metric_indices: MetricRef[],
  alignment_contract,
  comparator_contract,
  perspective,
  temporal_scope
}
```

A comparator may return differences, similarities, uncertainty bounds, alignment failures, and provenance. Its result is evidence for downstream reasoning; it is not itself a proof of identity, causation, or logical implication.

### 7.1 Alignment before comparison

Two numerical fields named `duration` may use minutes and seconds, represent actual and predicted times, or refer to different intervals. Comparability requires unit, meaning, sampling, and granularity alignment. A failed alignment should return a typed residual rather than an arbitrary score.

### 7.2 Relation differentials

Reasoning may compare changes in relational neighborhoods, e.g. route assignments before and after a proposed scheduling delta. This requires attention to added, removed, and modified edges, their validity windows, and membership version. Graph edit distance alone does not establish semantic equivalence.

### 7.3 Difference is not causation

An observed before/after difference does not identify its cause without a suitable causal design or assumptions. OCSRE explicitly separates `Changed(x)` from `CausedBy(change, intervention)` and treats causal claims as requiring their own contracts and evidence.

## 8. A guarded reasoning pipeline

A proposed processing sequence is:

```text
Input question / task
  -> Resolve WE identities and state versions
  -> Establish type, relation, time, perspective, and granularity scopes
  -> Retrieve admissible observations, rules, and metric views
  -> Align objects and validate operator preconditions
  -> Apply declared inference / comparison / aggregation operators
  -> Check hard constraints and authorization boundaries
  -> Classify result: proven | supported | estimated | hypothetical | rejected
  -> Attach provenance, assumptions, confidence where meaningful, residuals
  -> Return qualified result (never auto-promote into world state)
```

A result may be **rejected** because a required contract fails, or **unresolved** because evidence is missing. These must be distinguishable from a formally derived negative proposition. The pipeline is an architectural proposal, not an implemented runtime in v1.0.0.

### 8.1 Proof objects and evidence objects

For a deductive conclusion, a proof record should identify the logical system, premises, inference steps, and validity scope. For an evidential conclusion, an evidence record should identify sources, transformations, uncertainty, and conflicting reports. Keeping these records separate prevents *proof laundering*—the promotion of a model score or database assertion into a theorem.

## 9. Dynamic relations and WE-native CDE

OCSRE-008 will examine how a WE or a composite of WEs can serve as a CDE State-Container. Here the reasoning obligation is to describe and validate candidate transitions:

```text
S_v -- typed Delta(d) --> S_candidate
  -> type / permission / invariant checks
  -> constraint evaluation
  -> sandbox evaluation and evidence
  -> authorized promotion OR rejection / rollback
```

A state may include objects, relations, schedules, inventory, and constraints. A typed delta can modify a bus assignment, a transaction grouping hypothesis, or a code dependency representation, but its legal effects are domain-specific. A single-object delta may invalidate composite-level constraints, so validation must include affected relation neighborhoods and aggregates.

**Important boundary:** rollback of a modeled state is not equivalent to undoing an irreversible real-world action. External actions require separate authorization and compensation contracts.

### 9.1 Example: school-bus reassignment

Suppose a candidate delta moves a student from `bus-A` to `bus-B`. The change may improve total fleet utilization while violating a student's maximum ride time. The reasoning system should:

1. verify student and bus identities and relevant time windows;
2. update assignment relations in a candidate state only;
3. recompute affected capacity, route-time, and accessibility constraints;
4. evaluate the delta under declared hard constraints and optional scoring perspectives;
5. preserve failed checks as explicit residuals, and promote only if authorized.

This illustrates composite-state reasoning; it does not assert that a particular optimization algorithm will solve school-bus scheduling efficiently.

## 10. In-situ learning and feedback without semantic drift

In-situ learning may update metric calibration, evidence reliability, rule proposals, or plugin selection based on feedback. It must not silently rewrite historical facts, loosen hard constraints, or change the meaning of an established relation. Candidate changes to semantic contracts should be versioned and subjected to regression and counterexample tests before promotion.

A useful feedback record includes the question, object scope, proposed inference, predicted outcome, observed outcome, failure classification, and subsequent adjustment. Repeated execution may accumulate evidence for collective learning, but repetition alone is not validation of an inference rule.

## 11. Interfaces to the broader structural-intelligence ecosystem

| Neighboring work | OCSRE-003 interface | Boundary to preserve |
|---|---|---|
| **WE-SIO** | WE identity, metrics, state, perspectives, evidence | Reuse rather than redefine canonical WE semantics |
| **UTN / MDT / WE-HDT** | typed localization, addressing, differential lookup | Shared interface does not imply algorithmic equivalence |
| **SIF** | localized object and relation intelligence | Higher-level orchestration is outside this paper |
| **CDE** | state containers, typed deltas, constraint checks | Candidate evolution is not automatically authorized action |
| **MLIU** | potential metric/local intelligence interfaces | Exact interoperability remains to be specified |
| **UIERU** | reusable object-level results and relay artifacts | Relay requires recipient-side conformance |
| **ISGFTR** | cross-domain capability transfer hypotheses | Scaling behavior is unproven |

Calling graphs in AI-generated code governance are a useful relational perspective, but cannot by themselves establish full program semantics. Control/data flows, contracts, security policy, change impact, and regression evidence remain necessary. This is elaborated in CASE-006 and OCSRE-010.

## 12. Contract-first conformance obligations

The following **DRG** identifiers are proposed local obligations for this paper; they are not additional repository filenames. They should be reconciled with the canonical SPEC documents when those are authored.

| ID | Requirement | Minimal negative test |
|---|---|---|
| DRG-001 | Identity and state version are distinct | Treat changed attribute as new WE without identity rule |
| DRG-002 | Every dynamic claim carries valid temporal scope | Apply morning availability to afternoon |
| DRG-003 | Relations obey declared type/signature and inference laws | Infer inverse/transitive edge without contract |
| DRG-004 | Granularity lifting/projection requires explicit operator | Infer every member is efficient from fleet efficiency |
| DRG-005 | Aggregation guards overlap, units, and membership version | Double-count a shared bus |
| DRG-006 | Perspective-dependent scores retain policy provenance | Present preference score as objective measurement |
| DRG-007 | Differential comparison requires semantic alignment | Compare minutes to seconds without conversion |
| DRG-008 | Proof, evidence, and hypotheses remain distinguishable | Treat similarity threshold as logical proof |
| DRG-009 | Candidate state transitions validate affected constraints | Accept reassignment violating ride-time limit |
| DRG-010 | Missing/contradictory evidence yields qualified residual | Force binary true/false from disputed source |
| DRG-011 | Authorization is checked before state promotion | Promote sandbox state without approval |
| DRG-012 | Learning updates preserve versions and regressions | Change relation semantics without retesting |

**P0 semantic safety:** DRG-001 through DRG-010. **P0 evolution safety:** DRG-009 and DRG-011. **P1 reuse/learning:** DRG-012 and cross-domain tests. Runtime performance is a later P2 concern.

### 12.1 Conformance sequence

1. Define reference objects, relation signatures, temporal and granularity semantics.
2. Construct positive and negative cases, including contradictory and missing evidence.
3. Validate typed operators independently of optimization or LLM components.
4. Check state-transition and permission invariants.
5. Test cross-domain reuse with unchanged core interfaces and domain-specific plugins.
6. Report failures, unsupported cases, and residual uncertainty explicitly.

## 13. Research hypotheses and measurable evaluation

This paper chiefly supports the repository's existing hypothesis identifiers:

- **OCSH-001:** restricted classical deduction remains valid under the specified embedding; test preservation against a reference logic engine (see OCSRE-002).
- **OCSH-002:** a common differential kernel is reusable across domains without core changes; evaluate on heterogeneous typed metrics and relations (OCSRE-004).
- **OCSH-006:** explicit cross-granularity contracts reduce invalid inheritance and aggregation; compare guarded and unguarded systems on curated counterexamples.
- **OCSH-005:** WE-native CDE supports single-object and composite transitions under shared contracts; test invariant preservation on multi-object cases (OCSRE-008).
- **OCSH-007:** SQL-to-WE transformations retain relevant SQL semantics and permissions while exposing reusable object metrics (OCSRE-006).

Suggested measurements include invalid-inference rate, false promotion rate, granularity-violation rate, time-scope error rate, provenance completeness, constraint-violation detection, integration cost, and unresolved-case coverage. Compare against a simple unguarded graph baseline and a typed-rule baseline; report the costs of extra checks as well as benefits. No benchmark results are claimed here.

## 14. Counterexamples and failure modes

**CE-001 — Invalid temporal persistence.** `Open(door, t1)` is not enough to infer `Open(door, t2)` without a persistence rule and intervening-event assumptions.

**CE-002 — Invalid relational transitivity.** `Calls(A,B)` and `Calls(B,C)` do not entail `Calls(A,C)` as a direct-call relation. A distinct `ReachableCall(A,C)` may be derived under a declared path rule.

**CE-003 — Ecological fallacy.** High average group performance does not establish high performance for every member.

**CE-004 — Compositional double-counting.** Two groups sharing a vehicle cannot have their available seat capacities added as if independent for the same time window.

**CE-005 — Perspective confusion.** A high-risk score under policy P is not a proof of fraud, nor necessarily a high-risk score under policy Q.

**CE-006 — Identity conflation.** A wallet address, account key, device, and human controller are distinct candidate entities; an observed link is not identity equivalence.

**CE-007 — Incomplete code semantics.** A calling-graph edge may miss dynamically dispatched calls, side effects, or dataflow-based security dependencies.

**CE-008 — State-versus-world confusion.** A successful sandbox route reassignment is not evidence that the actual vehicles or students have moved.

These counterexamples should be incorporated into `research-trace/COUNTEREXAMPLE-REGISTRY.md` and the relevant SPEC conformance suites when authored.

## 15. Explicit leftovers and research limitations

1. **Formal semantics:** a full typed temporal-relational calculus, its model theory, and soundness/completeness conditions remain open. This paper supplies guarded interface obligations, not a complete logic.
2. **Identity resolution:** merging and splitting WEs under ambiguous evidence require separate governance; no universal identity oracle is assumed.
3. **Granularity algebra:** aggregation and projection need domain-specific proofs or testable contracts; no universally safe projection rule is asserted.
4. **Uncertainty:** calibration and combination of heterogeneous evidence sources remain unsettled; epistemic status is not a substitute for a probabilistic model.
5. **Causality:** differential observations do not establish causal effects without additional assumptions and designs.
6. **Computational complexity:** richer joins, temporal queries, and composite constraints may be expensive; performance claims require measured workloads.
7. **Concurrent evolution:** conflict resolution across multiple agents, snapshots, and real-world actions requires explicit isolation and authorization policies.
8. **Cross-project interoperability:** WE-SIO, UTN, SIF, CDE, MLIU, UIERU, and ISGFTR interfaces require versioned mapping tests, not assumed equivalence.
9. **Negative transfer:** reused relation or metric plugins may degrade accuracy in a new domain; this must be measured and reported.
10. **Scaling:** repeated capability spillover may be valuable, but no open-ended scaling law follows from the architecture alone.

These leftovers are deliberate research outputs and should not be hidden by an implementation demo.

## 16. Companion-document map

| Document | Relationship |
|---|---|
| `OCSRE-001-The-Object-Centric-Structural-Intelligence-Thesis.md` | overarching object-centric thesis and five-stage progression |
| `OCSRE-002-From-Classical-Syllogism-to-Object-Centric-Structural-Reasoning.md` | restricted classical validity and formal embedding target |
| `OCSRE-004-Object-Differential-Kernel-and-Generic-Operators.md` | typed comparison and alignment operator design |
| `OCSRE-006-SQL-to-Object-Attribute-Transformation-and-Semantic-Alignment.md` | bucketize/normalize/combine/derive and SQL permissions |
| `OCSRE-007-In-Situ-Object-Learning-Decision-and-Feedback.md` | feedback loops and controlled learning |
| `OCSRE-008-WE-Native-CDE-and-Composite-State-Evolution.md` | composite state and typed delta contracts |
| `OCSRE-009-Epistemic-Separation-and-Object-Centric-Evidence-Governance.md` | proof/evidence/policy separation |
| `SPEC-001-Object-Identity-Perspective-and-State-Contract.md` | identity, state, time, and perspective obligations |
| `SPEC-002-Object-Differential-Kernel-and-Comparator-Contract.md` | comparator typing and alignment |
| `SPEC-003-Classical-Reasoning-Preservation-and-Granularity-Contract.md` | validity and cross-granularity safety |
| `SPEC-006-WE-Native-CDE-Composite-State-and-Relay-Contract.md` | evolution and promotion governance |
| `CASE-003-School-Bus-Scheduling-and-Composite-WE-State.md` | multi-object scheduling constraints |
| `CASE-004-Transaction-and-Compositional-Identity.md` | relational identity evidence boundaries |
| `CASE-006-AI-Generated-Code-Governance-Through-Calling-Graphs-and-CDE.md` | call graph and program-change governance |
| `EXT-002-Object-Centric-SIF-Localization-and-Addressing.md` | multi-granular localization interfaces |

**Planned figure:** `figures/Fig-003-Object-Metric-Perspective-and-State.png`. Suggested placement: after Section 2 or before Section 6, once the actual figure asset has been created. No image is claimed to be present in this Markdown file.

## 17. Conclusion

Dynamic structural reasoning becomes trustworthy not by adding more edges or scores, but by retaining the conditions under which a claim is meaningful. OCSRE proposes a WE-centered interface that keeps identity separate from state, types relations, qualifies temporal scope, governs cross-granularity transformations, distinguishes perspectives from facts, and validates candidate deltas before promotion. Classical deduction remains a protected restricted subsystem; differential comparison, evidence-based inference, and policy evaluation remain distinct operations with their own contracts. The immediate contribution is a falsifiable research and conformance agenda for **dynamic, relational, and multi-granular reasoning**—a necessary bridge from object representation to object computation, in-situ learning, and constrained structural evolution.

---

**Research integrity note:** This document proposes architecture, examples, and testable requirements. It does not report implemented software, completed proofs, empirical validation, or demonstrated scaling behavior. All unresolved semantic and engineering questions are retained as explicit leftovers.
