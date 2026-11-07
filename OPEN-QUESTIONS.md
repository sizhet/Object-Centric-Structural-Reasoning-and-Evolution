# OPEN-QUESTIONS — OCSRE Research Questions and Collaboration Entry Points

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Version:** v1.0.0 — Research Framework and Contracts  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**Status:** Open research questions; hypotheses and evaluation designs are proposed, not validated  
**License:** Apache-2.0  
**Canonical location:** `OPEN-QUESTIONS.md`

## 1. Why this document exists

OCSRE explores a common typed World Entity (WE)/Object interface through which formal reasoning, differential metrics, domain plugins, in-situ learning, constrained state evolution, and capability relay might cooperate. Its value depends not only on proposing this architecture but on finding out **where the proposal breaks, where it is useful, and what it costs**.

This document is a *reader-facing research question map*. It is intentionally different from [`research-trace/UNRESOLVED-RESIDUALS.md`](research-trace/UNRESOLVED-RESIDUALS.md), the operational backlog of 40 open residuals (`URL-001`–`URL-040`). Questions below invite independent investigation; the residual ledger tracks closure criteria, priorities, dependencies, and evidence. Their identifiers are not interchangeable and mappings are thematic rather than automatically one-to-one.

**Research discipline:** Specifications/Contracts First; Conformance Before Runtime; Explicit Leftover. The eleven core hypotheses (`OCSH-001`–`OCSH-011`) are all **E0 — Proposed**. No proof of a general scaling law, implementation completeness, executed conformance suite, independent replication, or real-world deployment is claimed.

## 2. How to read and investigate a question

Each question has a stable `OQ-###` identifier, a primary challenge, an investigation approach, a disconfirming or limiting outcome, and related assets. A useful answer should report: (a) the exact semantic scope, (b) reproducible evidence or a formal argument, (c) counterexamples and rejected inputs, (d) comparison baselines and costs where applicable, and (e) remaining uncertainty. A *negative* answer is a legitimate research contribution.

A question is **not closed** by an appealing analogy, a successful synthetic illustration, an agent consensus, or a manuscript's existence. Proposed conformance cases become evidence only after execution with archived artifacts. Formal soundness, interface conformance, empirical utility, and action authorization are separate assurance claims.

## 3. WE/Object identity, perspective, and granularity

### OQ-001 — What constitutes persistent WE identity across changing representations?

If SQL keys, graph nodes, labels, and ObjectRefs change independently, which identity relations can remain stable? Investigate aliasing, splitting, merging, revoked references, and object lifecycle events using explicit identity witnesses. **Challenge:** two distinct entities with identical metric profiles must not collapse into one identity. **Related:** SPEC-001; OCSRE-003; OCSH-006; URL-001/002.

### OQ-002 — When may two perspectives share a metric comparison?

Can perspective compatibility be checked through a declared transformation rather than implicit normalization? Specify what is lost when an observer's operational view is translated into a regulator's or student's view. **Challenge:** a numerically equal value with incompatible meaning must be rejected or qualified. **Related:** SPEC-001/002; OCSRE-003; URL-003/008.

### OQ-003 — Which cross-granularity inferences are sound?

When may a Person property lift to Group, a Trip property to Fleet, or a wallet observation to a composite actor hypothesis? Distinguish universal, existential, aggregate, and defeasible assertions. **Challenge:** an aggregate average cannot license an individual claim. **Related:** SPEC-003; CASE-001/003/004; OCSH-006; URL-004.

### OQ-004 — How should time, snapshots, and mutable state enter an ObjectRef?

Determine whether identity references, state references, and observation windows require separate version dimensions. Test stale joins and contradictory time windows. **Challenge:** a valid claim at time `t1` must not be silently reused at `t2`. **Related:** SPEC-001; CASE-002; URL-005/016.

## 4. Formal reasoning, evidence, and uncertainty

### OQ-005 — Can a restricted OCSRE reasoning fragment preserve classical entailment?

Define syntax, semantics, scope of quantification, and translation to a reference logic. Seek soundness proofs and, where asserted, completeness results. **Challenge:** correct conclusions from false premises do not establish empirical truth; evidence support must not be presented as a theorem. **Related:** OCSRE-002; SPEC-003; CASE-001; EXT-001; OCSH-001; URL-006.

### OQ-006 — Can proof traces coexist with defeasible evidence without semantic leakage?

Represent deductive validity, evidential confidence, and decision permission as distinct typed outcomes. Test conflicting testimony, revoked observations, and provenance-dependent evidence. **Challenge:** a high confidence score cannot substitute for a proof step. **Related:** OCSRE-002/009; SPEC-003/005; URL-007/027.

### OQ-007 — How can weak evidence about compositional identity be calibrated?

Evaluate transaction graphs, temporal patterns, custody alternatives, and correlated signals under competing hypotheses. Use synthetic cases where identical observable flows admit different actors. **Challenge:** network similarity and shared addresses cannot uniquely establish real-world control. **Related:** CASE-004; OCSH-004/006; URL-026/027/028.

## 5. ODK, metrics, and object plugins

### OQ-008 — What is the smallest useful typed metric algebra?

Specify units, dimensions, direction, missingness, uncertainty, normalization, and permissible aggregation for `Object[metricIndices]`. **Challenge:** 15 percentage points must not be confused with 15 students, and incomparable units must not be silently coerced. **Related:** OCSRE-004; SPEC-002; URL-008/009.

### OQ-009 — What would demonstrate genuine ODK kernel invariance?

Freeze the kernel implementation before building adapters for scheduling, inventory, and transaction evidence. Compare outputs, defect rates, and domain-specific customization with bespoke comparators. **Challenge:** moving domain-specific code into hidden adapters may preserve a binary while defeating the reuse claim. **Related:** CASE-005; OCSH-002; URL-010.

### OQ-010 — Can Object Plugin contracts predict safe composition?

Test declared input/output types, effects, dependencies, perspectives, authority, and provenance across independent plugins. **Challenge:** signature compatibility may coexist with behavioral incompatibility or hidden side effects. **Related:** OCSRE-005; SPEC-004; OCSH-003; URL-011.

### OQ-011 — How should plugin revocation and replacement propagate?

When a metric plugin is corrected, which derived claims, cached scores, relay artifacts, and deployed actions become stale? Seek a dependency and invalidation protocol. **Challenge:** revoking a source plugin must not leave downstream conclusions falsely marked current. **Related:** SPEC-004/005; EXT-004; URL-012.

## 6. SQL-native adaptation and semantic preservation

### OQ-012 — Which SQL fragments admit faithful WE/Object adaptation?

Specify a supported fragment for `Bucketize → Normalize → Combine → Encode → Derive`. Compare against a real SQL engine, not only handwritten examples. **Challenge:** SQL `NULL` and three-valued predicates must not become ordinary falsehoods without a declared rule. **Related:** OCSRE-006; CASE-002; OCSH-007; URL-013.

### OQ-013 — How can join multiplicity and aggregation grain be preserved?

Test one-to-many joins, duplicates, grouping, window functions, and mixed entity granularities. **Challenge:** a join-induced row multiplication must not create additional students, trips, or evidence. **Related:** CASE-002; URL-014.

### OQ-014 — Can security and provenance survive SQL-to-WE transformation?

Verify row-level permissions, tenant boundaries, snapshot identity, data lineage, and revocation under derived objects. **Challenge:** a user forbidden from viewing a row must not infer its contents through a derived metric or relay artifact. **Related:** SPEC-001/005; CASE-002; URL-015/016.

## 7. In-situ learning and evidence feedback

### OQ-015 — What counts as object-local learning rather than data accumulation?

Separate raw observations, validated updates, policy decisions, and changes to reusable capability. Measure traceability, attribution quality, and retained utility. **Challenge:** storing more logs is not by itself an improvement in reasoning. **Related:** OCSRE-007/009; SPEC-005; OCSH-004; URL-017.

### OQ-016 — How can learning resist leakage and distribution drift?

Use temporal holdouts, versioned state, delayed feedback, independent test sets, and rollback. **Challenge:** improvements caused by future information leakage or shifting test distributions must not be credited to in-situ intelligence. **Related:** SPEC-005; URL-017/018.

## 8. WE-native CDE and composite-state evolution

### OQ-017 — What is a sound invariant calculus for composite WE states?

Represent buses, trips, drivers, students, and routes as typed objects with local and global constraints. Determine which invariants must be checked before and after every candidate transition. **Challenge:** a locally attractive reassignment must not violate fleet-wide feasibility. **Related:** OCSRE-008; SPEC-006; CASE-003; OCSH-005; URL-019.

### OQ-018 — When can typed deltas be composed, reversed, or rolled back?

Study preconditions, conflict detection, dependency order, path memory, and non-reuse constraints. **Challenge:** two individually legal deltas may be illegal in composition; an inverse may not restore external side effects. **Related:** SPEC-006; CASE-003/006; URL-020/021.

### OQ-019 — What are the limits of M→N dynamic branching and NoSubtree pruning?

Develop finite-state termination conditions, sound pruning contracts, and adversarial loop-back cases. Compare with search, dynamic programming, and branch-and-bound under matched budgets. **Challenge:** unsound pruning can discard the only feasible solution. **Related:** OCSRE-008; EXT-002; URL-021.

### OQ-020 — Where must candidate generation stop and authority begin?

Specify distinct states for proposed, scored, constraint-checked, independently reviewed, authorized, committed, and rolled back deltas. **Challenge:** an excellent optimization score is not permission to execute. **Related:** SPEC-006; CASE-006; URL-022.

### OQ-021 — Can CDE serve as an evolutionary SIF localization method?

Formalize the difference between locating an existing object/capability and locating a feasible not-yet-existing state via constrained evolution. Compare CDE's discovery costs and coverage with referential lookup. **Challenge:** a found candidate path is not automatically a validated reachable state. **Related:** EXT-002; SIF; URL-023.

### OQ-022 — How should UTN, MDT, WE-HDT, and OCSRE interoperate?

Define a common typed addressing contract without asserting their mathematical equivalence. Examine object identity, path provenance, scope, and version mismatch. **Challenge:** an address that resolves in one index may be semantically invalid in another. **Related:** OCSRE-010; EXT-002; URL-024.

## 9. Domain realism and compositional evidence

### OQ-023 — How far does the school-bus example transfer to real operations?

Extend fixed-trip synthetic schedules to travel-time uncertainty, driver shifts, student ride-time limits, accessibility, depot travel, and route construction. **Challenge:** reducing buses from three to two in a simplified fixture is not evidence of real-world fleet savings. **Related:** CASE-003; URL-025.

### OQ-024 — When is compositional identity intrinsically non-identifiable?

Construct observationally equivalent transaction networks controlled by different real-world actors. Identify the additional lawful, privacy-preserving evidence required to distinguish them. **Challenge:** some hypotheses may remain unresolved even with perfect graph analysis. **Related:** CASE-004; URL-026–028.

## 10. Multi-agent relay and collective structural learning

### OQ-025 — What constitutes a semantically valid relay artifact?

Require source/target scope, type contracts, evidence, negative tests, permissions, versions, costs, and revocation conditions. **Challenge:** transferring an algorithm does not transfer its domain assumptions. **Related:** CASE-005; EXT-003; OCSH-008; URL-029.

### OQ-026 — How can independent validation be distinguished from agent consensus?

Test correlated models, shared prompts, common training data, shared evaluation code, and common failure modes. **Challenge:** five agents repeating one mistaken assumption are not five independent confirmations. **Related:** EXT-003; URL-030.

### OQ-027 — When is relay economically beneficial?

Measure integration effort, validation overhead, compute, communication, maintenance, and negative transfer against single-agent and bespoke baselines. **Challenge:** a transferred capability that costs more to validate than to rebuild may have no net benefit. **Related:** CASE-005; OCSH-003/008; URL-031.

## 11. Open-ended metric, plugin, and policy evolution

### OQ-028 — Can a system generate genuinely useful new metrics?

Start from explicit residuals and counterexamples; propose new metrics with independent ground truth, stability checks, and ablation tests. **Challenge:** a metric optimized against its own scoring rule can improve without increasing task utility. **Related:** EXT-004; URL-032.

### OQ-029 — How can plugin and policy co-evolution remain governable?

Separate plugin proposals, metric proposals, policy proposals, and authorized policy changes. Require out-of-band approvals for permission expansions. **Challenge:** a system must not improve its measured performance by silently weakening its own constraints. **Related:** EXT-004; SPEC-004/006; URL-032.

### OQ-030 — Can explicit leftovers drive autonomous questioning without self-confirmation?

Connect residuals to AQSI-style question generation, independent challenge construction, and evidence review. **Challenge:** a generator must not grade the novelty or correctness of its own questions without external checks. **Related:** EXT-004/005; research-trace registries; AQSI.

## 12. Capability spillover and scaling hypotheses

### OQ-031 — What is the minimum evidence for untargeted capability spillover?

Freeze capability versions and preregister tasks not used in design or tuning. Compare with no-transfer, direct adaptation, and equal-budget baselines. **Challenge:** post-hoc selection of favorable tasks is not untargeted spillover. **Related:** EXT-005; OCSH-009; URL-033.

### OQ-032 — What would constitute a structural scaling relationship?

Measure validated novel capability, transfer success, task performance, and resource costs longitudinally; include uncertainty and failed trials. **Challenge:** a growing number of plugins, papers, or agents is not itself a scaling law. **Related:** EXT-005; ISGFTR; OCSH-010; URL-034/035.

### OQ-033 — Can capability growth persist after easy transfer opportunities are exhausted?

Test diminishing returns, incompatible interfaces, interference, and maintenance burden over successive relay generations. **Challenge:** early cross-domain successes may plateau or reverse. **Related:** EXT-005; OCSH-010; URL-034/035.

## 13. AI-generated code governance

### OQ-034 — What can Calling Graphs localize, and what do they miss?

Study dynamic dispatch, reflection, configuration, data flow, schema evolution, caches, permissions, and deployment dependencies. **Challenge:** unchanged call edges can conceal a changed authorization policy. **Related:** CASE-006; OCSH-011; URL-036.

### OQ-035 — Can multi-graph impact analysis achieve useful assurance at acceptable cost?

Compare ordinary CI, call-graph-only review, and OCSRE multi-graph + CDE governance using seeded faults and real change histories where authorized. Report false negatives, false positives, review cost, and time-to-detection. **Challenge:** exhaustive impact analysis may be intractable or incomplete in dynamic systems. **Related:** CASE-006; URL-037.

### OQ-036 — How should AI-generated changes move from proposal to deployment?

Define sandbox, tests, security review, approval, merge, rollout, monitoring, and rollback as distinct typed transitions. **Challenge:** passing tests or a high ODK score must never confer deployment authority. **Related:** CASE-006; SPEC-005/006; OCSH-011; URL-038.

## 14. Research infrastructure and external validation

### OQ-037 — What is the smallest auditable OCSRE implementation slice?

Prototype one versioned ObjectRef, a typed metric interface, an unchanged ODK, one SQL adapter, a minimal CDE delta checker, and a positive/negative conformance harness. **Challenge:** a demo that skips contract failures cannot test the central architecture. **Related:** FUTURE-DIRECTIONS; SPEC-001–006; URL-039.

### OQ-038 — How can independent researchers reproduce both success and failure?

Publish frozen fixtures, executable oracles, provenance, budgets, environment versions, negative cases, and review records. **Challenge:** tests requiring undisclosed data or undocumented human judgment are not independently reproducible. **Related:** HYPOTHESIS-REGISTRY; COUNTEREXAMPLE-REGISTRY; URL-039/040.

### OQ-039 — Which claims are formal, empirical, or governance claims?

For each OCSH, explicitly identify whether the required evidence is a proof, a conformance test, a controlled benchmark, an operational safety review, or some combination. **Challenge:** proof of a restricted logic fragment cannot establish transfer economics; benchmark gains cannot authorize actions. **Related:** OCSH-001–011; EXT-001/005; URL-040.

### OQ-040 — How should a failed hypothesis reshape the architecture?

Define a process for narrowing claim scope, revising contracts, reopening decisions, retiring plugins, and preserving the original negative evidence. **Challenge:** relabeling a failed claim as a success without changing the evidence is unacceptable. **Related:** DECISION-LOG; COUNTEREXAMPLE-REGISTRY; UNRESOLVED-RESIDUALS.

## 15. Cross-cutting research programs

| Program | Initial questions | Primary evaluation surface | Key falsification risk |
|---|---|---|---|
| P-A: Semantic substrate | OQ-001–007 | Formal fragments, identity fixtures | Invalid inference or identity collapse |
| P-B: Typed computation | OQ-008–011 | Frozen ODK and plugin conformance | Hidden domain coupling |
| P-C: Data integration | OQ-012–014 | SQL differential tests | Lost NULL, grain, or security semantics |
| P-D: Feedback intelligence | OQ-015–016 | Temporal holdouts and provenance | Leakage or drift |
| P-E: Constrained evolution | OQ-017–022 | Composite-state and path fixtures | Invariant breach or unsound pruning |
| P-F: Domain evidence | OQ-023–024 | Scheduling and transaction cases | Unrealistic or non-identifiable inference |
| P-G: Collective relay | OQ-025–027 | Independent multi-agent comparisons | Correlated validation or negative transfer |
| P-H: Open-ended growth | OQ-028–033 | Preregistered longitudinal studies | Self-scoring and selection bias |
| P-I: Code governance | OQ-034–036 | Seeded faults and controlled changes | Hidden dependencies or unsafe authorization |
| P-J: Research assurance | OQ-037–040 | Conformance harness and review logs | Irreproducibility and claim inflation |

**Suggested dependency order:** P-A and P-J before broad runtime claims; P-B/P-C before cross-domain comparisons; P-E and P-F before realistic optimization claims; P-G before P-H; P-I proceeds in a sandbox with explicit authorization boundaries. This is a proposed order of research, not a schedule or completion statement.

## 16. How to contribute a research answer

A contribution should include the question ID; exact claim and supported scope; contract and definition versions; a minimal reproducible fixture; a reference oracle or proof; positive and adversarial cases; evaluation baseline and resource accounting; limitations and counterexamples; and a proposed update to the relevant registry. Security-sensitive case data should be synthetic, appropriately de-identified, or used only under lawful authorization. Do not publish private identifiers or infer real-person identity from weak transactional signals.

Suggested evidence workflow:

1. **Propose** a bounded answer or a counterexample; identify the affected `OCSH`, `URL`, `CEX`, and `ADR` records where applicable.
2. **Specify** the semantics and test protocol before tuning a system against it.
3. **Challenge** the proposed answer with alternative explanations, invalid inputs, and negative cases.
4. **Execute** in a reproducible, permissioned environment; archive both successes and failures.
5. **Review independently**, including source provenance, evaluation leakage, and resource cost.
6. **Qualify or reject** the claim; update the canonical registries without erasing history.
7. **Relay** only the validated, bounded artifact, together with its known limitations and revocation conditions.

## 17. What this document does not claim

This file does not establish a universal object ontology, a complete formal logic, a safe autonomous policy editor, a real-world identity inference system, an optimized school-bus fleet, or an empirical structural scaling law. OCSRE is a research framework whose proposed contracts and mechanisms must be tested against explicit counterexamples and independent baselines. Different frameworks—SIF, UTN, MDT, WE-HDT, CDE, UIERU, AQSI, and ISGFTR—may cooperate through interfaces without being semantically or mathematically interchangeable.

## 18. Companion documents and next steps

- [README.md](README.md) — high-level research entry.
- [START-HERE.md](START-HERE.md) — reading paths by discipline.
- [CONTENTS.md](CONTENTS.md) — full repository map.
- [GLOSSARY.md](GLOSSARY.md) — accessible terminology.
- [FUTURE-DIRECTIONS.md](FUTURE-DIRECTIONS.md) — phased research agenda.
- [HYPOTHESIS-REGISTRY.md](research-trace/HYPOTHESIS-REGISTRY.md) — canonical hypothesis states and evidence gates.
- [DEFINITION-REGISTRY.md](research-trace/DEFINITION-REGISTRY.md) — canonical definition boundaries.
- [COUNTEREXAMPLE-REGISTRY.md](research-trace/COUNTEREXAMPLE-REGISTRY.md) — adversarial cases and failure records.
- [DECISION-LOG.md](research-trace/DECISION-LOG.md) — revisable architectural choices.
- [UNRESOLVED-RESIDUALS.md](research-trace/UNRESOLVED-RESIDUALS.md) — operational unresolved backlog.
- [TESTABLE-HYPOTHESES.md](TESTABLE-HYPOTHESES.md) — proposed test protocols.
- [VALIDATION-ROADMAP.md](VALIDATION-ROADMAP.md) — proposed execution stages.

The intended next step is to turn a small number of these questions into **frozen, executable, independently reviewable experiments**, rather than interpreting the number of questions as evidence of progress.

---

*Research baseline: v1.0.0. Questions remain open until evidence supports a bounded answer. Preserve explicit leftovers and failed trials as first-class inputs to collective structural learning.*
