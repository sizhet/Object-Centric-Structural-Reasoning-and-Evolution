# FUTURE-DIRECTIONS — OCSRE Research and Engineering Agenda

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Version:** v1.0.0 — Research Framework and Contracts  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**Status:** Forward-looking research agenda; no implementation or empirical validation claimed  
**License:** Apache-2.0  
**Canonical location:** `FUTURE-DIRECTIONS.md`

## 1. Purpose

OCSRE proposes that typed World Entity (WE) and Object interfaces can serve as a common substrate for classical deduction, metric-differential computation, domain-specific capabilities, in-situ learning, constrained state evolution, and structural capability relay. The purpose of this document is to convert that architectural proposition into a **prioritized, falsifiable, contract-first research agenda**. It is not a claim that the proposed system has been implemented, that its hypotheses have been validated, or that a new scaling law has been observed.

The next stage is not simply to add more Object Plugins. It is to determine which parts of the architecture can be made precise, which can be tested independently, which actually transfer between domains, and which fail under counterexamples. Failed tests, semantic incompatibilities, cost overruns, and unclosed residuals are first-class research outputs.

**Operating discipline:** Specifications/Contracts First; Conformance Before Runtime; Explicit Leftover. Every promoted capability requires traceable semantics, evidence, reproducible tests, an explicit authority boundary, and a revocation path.

## 2. Research baseline and nonclaims

The v1.0.0 research baseline consists of twelve core papers (`docs/OCSRE-001`–`012`), six specifications (`specs/SPEC-001`–`006`), six cases (`cases/CASE-001`–`006`), five extensions (`extensions/EXT-001`–`005`), and five research-trace registries. Eight conceptual figures describe the proposed architecture. These are authored research assets, not an executed runtime or a certified implementation.

The eleven core hypotheses `OCSH-001`–`OCSH-011` remain **E0 — Proposed** in [`HYPOTHESIS-REGISTRY.md`](research-trace/HYPOTHESIS-REGISTRY.md). The 40 cross-document unresolved residuals `URL-001`–`URL-040` remain open in [`UNRESOLVED-RESIDUALS.md`](research-trace/UNRESOLVED-RESIDUALS.md). Proposed test counts in different documents are local planning artifacts; they are not cumulative evidence of test execution.

Do not infer that (i) object identity is a database key, (ii) metric similarity proves identity or entailment, (iii) a valid candidate is authorized, (iv) agent agreement is independent validation, (v) successful reuse proves spillover, or (vi) accumulating artifacts establishes scaling.

## 3. Direction FD-01 — Canonical WE/Object semantics and reference integrity

**Question.** Can independent systems exchange a stable ObjectRef while preserving identity, perspective, granularity, temporal validity, state version, provenance, and authority?

**Proposed work.** Specify a machine-checkable ObjectRef schema; define aliasing, split/merge and revocation semantics; distinguish persistent WE identity from mutable object projections and storage keys; add versioned perspective and granularity contracts. Test time-window mismatches, stale snapshots, nonunique labels, group-to-individual inference, and cross-tenant access. Make all failed bindings explicit rather than silently coercing them.

**Deliverables.** Reference schema, compatibility decision procedure, synthetic fixture catalog, property-based negative tests, and a normative error taxonomy. **Acceptance gate:** independent adapters agree on permitted and rejected bindings under a frozen contract. **Related:** SPEC-001, OCSRE-003, OCSH-006, URL-001–005.

## 4. Direction FD-02 — Restricted classical reasoning preservation

**Question.** Can a declared object-centric logical fragment preserve classical entailment without confusing evidence, state changes, and uncertain premises with deductive validity?

**Proposed work.** Define the syntax, interpretation, quantification scope, identity substitution rules, and a translation to a reference theorem prover. Include valid and invalid Socrates-style syllogisms, contradictions, temporal changes, and granularity counterexamples. Compare proof traces rather than only final labels. Where the object layer supports defeasible evidence, make its proof status a separate typed result.

**Deliverables.** Formal fragment, translation specification, proof or counterexample, and executable regression corpus. **Acceptance gate:** soundness (and completeness where claimed) in the declared fragment, with known boundaries documented. **Related:** SPEC-003, CASE-001, EXT-001, OCSH-001, URL-006–007.

## 5. Direction FD-03 — Object Differential Kernel invariance and metric algebra

**Question.** Can a common ODK operate unchanged across heterogeneous domains while rejecting invalid comparisons?

**Proposed work.** Specify `Object[metricIndices]` as a typed projection; develop units, normalization, missingness, uncertainty, directionality, perspective compatibility, and aggregation rules. Freeze a kernel binary or hash before adapters are written. Compare school-bus capacity, inventory utilization, scheduling pressure, and transaction-evidence metrics using matched bespoke comparators. Log all domain-specific work outside the kernel and measure its cost.

**Deliverables.** Kernel API, metric-type algebra, frozen implementation, cross-domain test fixtures, reproducible benchmarks. **Acceptance gate:** correct typed results with kernel invariance; unacceptable coercions rejected. **Related:** SPEC-002, OCSRE-004, CASE-002/003/004/005, OCSH-002, URL-008–010.

## 6. Direction FD-04 — Object Plugin compatibility, composition and revocation

**Question.** Does contract-based composition reduce adaptation cost without introducing hidden semantic coupling?

**Proposed work.** Define Plugin manifests for inputs, outputs, metrics, effects, dependencies, provenance, security permissions, versioning, and rollback. Separate interface compatibility from behavioral equivalence. Introduce a conformance harness for capability discovery, sandbox execution, dependency conflicts, revoked plugins, and adversarial compositions. Compare integration hours, changed lines, defects, runtime overhead, and maintenance burden with bespoke implementations.

**Deliverables.** Manifest schema, composition checker, dependency graph, compatibility matrix, and matched-cost studies. **Acceptance gate:** no unauthorized side effects, explicit failure modes, and measured adaptation outcomes. **Related:** SPEC-004, OCSRE-005, CASE-005, EXT-004, OCSH-003, URL-011–012.

## 7. Direction FD-05 — SQL-native semantic adaptation

**Question.** Can SQL-derived objects preserve the database semantics needed for valid downstream reasoning and optimization?

**Proposed work.** Formalize Bucketize, Normalize, Combine, Encode, and Derive as typed transformations. Test NULL and SQL three-valued logic, duplicate and join multiplicity, aggregation grain, snapshot isolation, temporal alignment, row-level security, and provenance. Distinguish SQL primary keys from WE identity and query results from authorized state changes. Use CASE-002 fixtures as a starting point, not as evidence of a working adapter.

**Deliverables.** SQL-to-WE adapter contract, reference queries, expected-result oracle, differential testing against a real SQL engine, access-control audit. **Acceptance gate:** semantic and security preservation for declared supported SQL fragments; unsupported fragments rejected explicitly. **Related:** OCSRE-006, CASE-002, OCSH-007, URL-013–016.

## 8. Direction FD-06 — In-situ object learning and epistemic governance

**Question.** Can object-linked feedback improve traceability and useful adaptation without contamination, feedback leakage, or unwarranted certainty?

**Proposed work.** Define observation, hypothesis, metric, feedback, revision, and authorization records with temporal provenance. Compare static baselines to in-situ updating on held-out tasks. Introduce delayed outcomes, contradictory evidence, concept drift, dependent evidence sources, and revoked observations. Require reproducible attribution of each model or policy update to the evidence it consumed.

**Deliverables.** Feedback ledger, update protocol, uncertainty and contradiction handling, drift monitoring, and evaluation scripts. **Acceptance gate:** measurable improvement or documented null result with preserved auditability and no leakage. **Related:** SPEC-005, OCSRE-007/009, OCSH-004, URL-017–018.

## 9. Direction FD-07 — WE-native CDE and composite state evolution

**Question.** Can typed Delta operators evolve single-object and composite states while maintaining local and global invariants?

**Proposed work.** Define State-Container and candidate/committed state separation; typed Delta preconditions and postconditions; composition, reversibility, conflict detection, path-memory nonreuse, NoSubtree semantics, and Loop-Back termination policy. Start with synthetic school-bus duties and extend to equipment scheduling and transaction-hypothesis state. Report infeasible candidates and search overhead, not only improvements.

**Deliverables.** Delta schema, invariant checker, candidate ledger, rollback semantics, bounded search harness, negative-test suite. **Acceptance gate:** no committed state violates declared invariants; bounded termination or explicit stopping conditions; authorization independent of score. **Related:** SPEC-006, OCSRE-008, CASE-003/004, OCSH-005, URL-019–022.

## 10. Direction FD-08 — SIF Localization as referential and evolutionary addressing

**Question.** Can a shared object interface connect locating existing facts/capabilities with generating feasible new state paths?

**Proposed work.** Define distinct operations for problem, capability, object, state, evidence, and action localization. Compare UTN, MDT, WE-HDT, and OCSRE interfaces without asserting algorithmic equivalence. Develop a typed mapping from a problem gap to available capability, candidate Delta search, conformance result, and governed promotion. Treat **CDE as an evolutionary Localization pillar within SIF**, complementary to referential addressing.

**Deliverables.** Addressing protocol, bidirectional Problem↔Capability fixtures, traceable localization results, comparative search studies. **Acceptance gate:** correct localization with explicit failures and no conflation of discovery, proof, feasibility, and authority. **Related:** OCSRE-010, EXT-002, SIF, OCSH-011 where code localization applies.

## 11. Direction FD-09 — Multi-agent competition, independent challenge and relay

**Question.** Do specialized agents produce better validated outcomes than a resource-matched single-agent baseline?

**Proposed work.** Separate candidate generation, counterexample search, evidence audit, constraint checking, evaluation, and authorization. Record each agent's inputs, tools, model versions, and dependency on other agents' outputs. Test correlated failures and false consensus; require at least one independent challenger for promotion where feasible. Preserve rejected strategies as reusable negative evidence.

**Deliverables.** Relay Artifact manifest, agent-role protocol, challenge ledger, cost-accounted benchmark, failure replay. **Acceptance gate:** independently validated net benefit after compute, coordination, and review costs; otherwise retain negative result. **Related:** EXT-003, UIERU, SSICR, CASE-005, OCSH-008.

## 12. Direction FD-10 — Compositional identity and directional weak evidence

**Question.** Can transaction graph observations support useful, revisable composite-actor hypotheses without being promoted to identity facts?

**Proposed work.** Represent addresses, accounts, keys, transaction edges, and candidate actor groupings separately. Use explicit directional evidence with source dependence, time windows, and contradictory alternatives. Introduce merge/split Delta operations for hypotheses, not for real-world identity records. Test service intermediaries, coincidental timing, common-ownership false positives, and evidence retraction. Enforce privacy, proportionality, and lawful-access constraints.

**Deliverables.** Synthetic transaction fixtures, evidence graph schema, alternative-hypothesis registry, adversarial evaluation. **Acceptance gate:** calibrated uncertainty and transparent abstention; no unsupported identity attribution. **Related:** CASE-004, OCSRE-009, SPEC-005/006, OCSH-004/005.

## 13. Direction FD-11 — AI-generated code governance

**Question.** Can Calling Graph–UTN–OCSRE analysis improve change-impact localization and test targeting without missing non-call dependencies?

**Proposed work.** Build a versioned multi-graph representation of calls, data flow, control dependence, configuration, schemas, security policy, tests, and deployment. Treat proposed code patches as typed CDE candidate Deltas. Benchmark against standard CI/review and Calling Graph-only analysis. Include the counterexample of unchanged calls but changed authorization-cache semantics, dynamic dispatch, generated code, and hidden deployment coupling.

**Deliverables.** Multi-graph schema, patch-impact oracle, risk-sensitive test selector, sandbox review protocol. **Acceptance gate:** measured recall/precision, security regression detection, cost and traceability under fixed budgets; deployment requires independent authority. **Related:** CASE-006, OCSRE-010, EXT-002, OCSH-011.

## 14. Direction FD-12 — Open-ended Metric, Plugin and Policy evolution

**Question.** Can a system discover useful new measurement dimensions and composable capabilities without controlling its own acceptance criteria?

**Proposed work.** Model Metric Registry, Plugin Registry, Policy Registry, and Evidence Ledger as a governed composite state. Generate candidate metrics from residuals and counterexamples; validate on independent held-out tasks. Allow proposed plugin and policy changes but prevent self-authorization, reward manipulation, and silent relaxation of security boundaries. Require rollback, versioned dependencies, and retirement of harmful capabilities.

**Deliverables.** Registry-delta protocol, novelty and redundancy checks, independent evaluator, anti-gaming suite. **Acceptance gate:** reproducible incremental utility without governance regressions; failed candidates remain traceable. **Related:** EXT-004, OCSRE-012, AQSI, CDE, UIERU, OCSH-010.

## 15. Direction FD-13 — Capability spillover, untargeted transfer and scaling

**Question.** Do validated capabilities yield gains on tasks not selected during their development, and does accumulated capability predict sustained net growth?

**Proposed work.** Distinguish reuse, adapted transfer, generalization, untargeted spillover, cumulative growth, and scaling. Prospectively freeze task holdouts, plugin versions, evaluator criteria, and resource budgets. Include negative transfer and tasks with no plausible shared structure. Compare against increased model inference, additional bespoke engineering, and larger non-composable libraries. Measure effect sizes, uncertainty, maintenance, validation cost, and longitudinal decay.

**Deliverables.** Prospective holdout protocol, cost-normalized capability ledger, longitudinal evaluation plan, null-result reporting. **Acceptance gate:** separately evaluate OCSH-008, -009, and -010; do not claim a structural Scaling Law from a small positive transfer demonstration. **Related:** EXT-005, ISGFTR, OCSRE-011/012.

## 16. Cross-cutting direction — Research infrastructure and conformance harness

A common experimental infrastructure should make the preceding directions comparable rather than forcing their semantics to be identical.

Minimum proposed artifact set:

1. **Versioned schemas:** ObjectRef, metric projections, Plugin manifest, typed Delta, evidence record, and Relay Artifact.
2. **Synthetic fixture packages:** classical deduction, SQL, bus scheduling, transaction hypotheses, and code changes; each with expected results and counterexamples.
3. **Conformance runner:** separate logical, semantic, security, state-invariant, and authorization checks.
4. **Evidence store:** immutable run IDs, code and environment versions, seeds, datasets, evaluator, costs, and independent reviewer status.
5. **Registry links:** OCSH, DEF, CEX, ADR-OCSRE, URL, local leftovers, and experiment records; unresolved mappings marked `TBD`.
6. **Publication process:** publish positive, negative, inconclusive, and failed-transfer results with bounded claims.

A passing conformance suite demonstrates only compliance with the tested contract and fixtures. It does not by itself demonstrate empirical utility, transfer, novelty, or sustained scaling.

## 17. Proposed phased roadmap and dependency gates

Phases represent **logical dependencies**, not committed dates or a claim of completed work.

| Phase | Primary work | Entry condition | Exit evidence | Downstream dependency |
|---|---|---|---|---|
| P0 — Semantic foundations | FD-01, FD-02, metric types | Reviewed definitions and contracts | Schemas, reference oracles, adversarial fixtures | All subsequent work |
| P1 — Minimal conformance prototypes | FD-03, FD-04, FD-05 | P0 contracts frozen for experiment | Executed kernel, adapter and plugin conformance logs | Transfer studies |
| P2 — Governed state and feedback | FD-06, FD-07, FD-08 | Identity, state, metric semantics established | Composite invariants, feedback ledger, localization traces | Multi-agent/CDE cases |
| P3 — Domain and governance stress tests | FD-09, FD-10, FD-11 | P1/P2 reference artifacts | Independent challenge, security, cost and failure reports | Relay claims |
| P4 — Evolution and relay experiments | FD-12 and OCSH-008 | Transfer protocols and baselines frozen | Measured transfer with negatives and total cost | Spillover claims |
| P5 — Prospective spillover and scaling | FD-13 | Prior tasks/metrics frozen; independent oversight | Holdout and longitudinal reports with uncertainty | Any bounded growth claim |

**Stop conditions:** unresolved P0 safety boundaries, missing authority separation, invalid evidence provenance, or unmeasured confounding block promotion regardless of attractive performance numbers. Phases may overlap for research efficiency, but no downstream claim may borrow assurance from a prerequisite that has not passed its own gate.

## 18. Experimental design principles

- **Independent baselines:** compare like-for-like tasks and budgets; include bespoke, single-agent, Calling Graph-only, or SQL-native baselines where appropriate.
- **Predeclared metrics:** freeze accuracy, semantic rejection rate, invariant violations, adaptation effort, validation cost, transfer gain, and resource consumption before testing.
- **Negative controls:** incompatible metrics, wrong granularity, stale snapshots, untrusted plugins, correlated agents, and deliberately misleading evidence.
- **Provenance and reproducibility:** archive inputs, outputs, versions, evaluator code, seeds and exclusions; report missing data.
- **Uncertainty:** distinguish observed effect from statistical or causal inference; report failures, variance, and scope.
- **Security and privacy:** use synthetic or properly authorized data, least privilege, reviewable promotion and revocation.
- **Ablation:** remove identity typing, differential kernel, independent challenger, CDE invariants, or relay contracts to identify which components contribute.
- **No silent success promotion:** a designed fixture is not a passed test; a passed test is not independent replication; replication is not unlimited generality.

## 19. Research-to-hypothesis map

| Core hypothesis | Primary future directions | Principal experiment question |
|---|---|---|
| OCSH-001 | FD-02 | Does a restricted translation preserve entailment? |
| OCSH-002 | FD-03 | Is a frozen ODK kernel correct across domains? |
| OCSH-003 | FD-04 | Are contracted plugins cheaper or safer to adapt? |
| OCSH-004 | FD-06, FD-10 | Does object-linked feedback improve traceability or utility? |
| OCSH-005 | FD-07 | Are composite state transitions invariant-preserving? |
| OCSH-006 | FD-01, FD-02 | Do granularity contracts prevent invalid inference? |
| OCSH-007 | FD-05 | Are SQL semantics and access controls preserved? |
| OCSH-008 | FD-04, FD-09, FD-13 | Does validated cross-domain transfer occur? |
| OCSH-009 | FD-13 | Are gains observed on prospectively untargeted tasks? |
| OCSH-010 | FD-12, FD-13 | Is there sustained net capability growth? |
| OCSH-011 | FD-08, FD-11 | Does code-impact governance improve localization and traceability? |

These are proposed tests, not evidence. For canonical hypothesis wording and status transitions, see [`HYPOTHESIS-REGISTRY.md`](research-trace/HYPOTHESIS-REGISTRY.md).

## 20. Prioritization, risk and governance

**P0 — Assurance blockers:** identity and permission boundaries; metric compatibility; SQL access-control preservation; composite invariants; candidate-versus-authorized separation; code security blind spots. Research may proceed in a sandbox, but no real-world deployment or promotion should rely on unresolved P0 claims.

**P1 — Core validity:** logical preservation; ODK invariance; adapter correctness; reproducible feedback attribution; transfer baselines; search termination and cost.

**P2 — Exploratory opportunities:** multi-agent coordination optimization; new Metric discovery; prospective spillover; longitudinal scaling; broader collective learning ecosystems.

Priority reflects consequences and dependency structure, not certainty of benefit. Every major design change should create or update an `ADR-OCSRE` entry in [`DECISION-LOG.md`](research-trace/DECISION-LOG.md). Every serious failure should create or link a `CEX` entry in [`COUNTEREXAMPLE-REGISTRY.md`](research-trace/COUNTEREXAMPLE-REGISTRY.md). Unresolved gaps should be tracked as `URL` records in [`UNRESOLVED-RESIDUALS.md`](research-trace/UNRESOLVED-RESIDUALS.md). No record should be closed merely because a document was written.

## 21. Opportunities for external collaboration

OCSRE can support modular research contributions without requiring agreement on all high-level hypotheses. Logic researchers can test the restricted proof fragment; database researchers can stress SQL semantics; optimization researchers can build composite-state invariant checkers; software engineers can evaluate code-impact localization; security researchers can audit permissions and candidate promotion; multi-agent researchers can compare independent challenge protocols; empirical researchers can design prospective spillover experiments.

A useful contribution should identify its target contract, hypothesis, fixture versions, expected failure modes, evaluator, and provenance. An independent reproduction or a well-characterized failure is as valuable as a positive demonstration for advancing a reliable research program.

## 22. Explicit leftovers — next unresolved decisions

The following **FDL-001–024** are forward-looking planning leftovers, not replacements for the canonical `URL-001`–`URL-040` registry. Exact one-to-one mappings remain subject to review.

| ID | Explicit leftover | Required next artifact |
|---|---|---|
| FDL-001 | Canonical ObjectRef serialization | Versioned schema |
| FDL-002 | WE identity alias and merge policy | Identity conformance tests |
| FDL-003 | Perspective compatibility calculus | Formal decision rules |
| FDL-004 | Cross-granularity projection semantics | Positive/negative proof fixtures |
| FDL-005 | Restricted classical fragment | Formal grammar and prover mapping |
| FDL-006 | ODK unit and missingness algebra | Typed operator specification |
| FDL-007 | Frozen-kernel cross-domain benchmark | Reproducible benchmark harness |
| FDL-008 | Plugin effect and dependency semantics | Manifest and revocation tests |
| FDL-009 | SQL NULL and join semantics | SQL differential oracle |
| FDL-010 | SQL security and snapshot guarantees | Permission and provenance tests |
| FDL-011 | In-situ feedback causal attribution | Predeclared evaluation protocol |
| FDL-012 | Evidence dependence and retraction | Evidence-ledger semantics |
| FDL-013 | Composite State-Container invariants | Invariant checker |
| FDL-014 | Typed Delta composition/rollback | State transition oracle |
| FDL-015 | CDE path memory and termination | Bounded search specification |
| FDL-016 | SIF referential/evolutionary localization API | Bidirectional addressing contract |
| FDL-017 | Multi-agent independence criterion | Correlation and challenge tests |
| FDL-018 | Composite identity uncertainty policy | Abstention and alternative-hypothesis fixtures |
| FDL-019 | Code multi-graph coverage | Impact localization benchmark |
| FDL-020 | AI patch authorization boundary | Sandbox-to-deployment governance contract |
| FDL-021 | Metric/Plugin/Policy evolution approval | Registry-delta approval protocol |
| FDL-022 | Untargeted spillover holdouts | Frozen prospective task set |
| FDL-023 | Longitudinal resource-normalized scaling | Cost and capability ledger |
| FDL-024 | Independent replication and publication governance | Reviewer and evidence archive protocol |

Each leftover remains open until an identified owner supplies reviewed evidence. A completed plan is not a completed experiment.

## 23. Recommended next research milestone

The first milestone should be a **minimal, auditable conformance slice**, not an ambitious autonomous multi-agent deployment. A defensible slice would include: (1) one canonical ObjectRef schema; (2) a frozen typed ODK comparator; (3) one SQL-to-WE adapter with explicit NULL/granularity/security behavior; (4) one composite-state Delta and invariant checker; (5) a shared positive/negative fixture suite; and (6) an evidence ledger that records every accepted and rejected result. This slice should be evaluated against simple, well-matched baselines before more elaborate relay or open-ended evolution claims are advanced.

Only after such a slice has passed independently reviewed conformance tests should the research program attempt stronger claims about adaptation efficiency, multi-agent advantages, untargeted spillover, or scaling.

## 24. Closing perspective

The most consequential future direction for OCSRE is not to make every task look like the same object. It is to make **heterogeneous objects, metrics, reasoning methods, state transitions, and capabilities interoperable without losing their differences**. That requires strong interfaces, explicit epistemic separation, carefully governed evolution, and willingness to retain failed experiments as reusable knowledge.

The proposed path is therefore: **define → challenge → conform → measure → relay → revisit**. Its success remains to be established through executable artifacts, adversarial evaluation, and independent replication.

---

## Companion documents

- [START-HERE.md](START-HERE.md) — guided reading paths.
- [CONTENTS.md](CONTENTS.md) — complete repository navigation.
- [TESTABLE-HYPOTHESES.md](TESTABLE-HYPOTHESES.md) — planned hypothesis-level tests (when authored).
- [VALIDATION-ROADMAP.md](VALIDATION-ROADMAP.md) — planned execution and evidence gates (when authored).
- [HYPOTHESIS-REGISTRY.md](research-trace/HYPOTHESIS-REGISTRY.md) — canonical claim status.
- [DEFINITION-REGISTRY.md](research-trace/DEFINITION-REGISTRY.md) — canonical terms and distinctions.
- [COUNTEREXAMPLE-REGISTRY.md](research-trace/COUNTEREXAMPLE-REGISTRY.md) — adversarial research records.
- [DECISION-LOG.md](research-trace/DECISION-LOG.md) — architectural decision history.
- [UNRESOLVED-RESIDUALS.md](research-trace/UNRESOLVED-RESIDUALS.md) — canonical open backlog.

**Research status at publication:** proposals and contracts only; no experimental claims are asserted.
