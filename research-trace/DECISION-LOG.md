# DECISION-LOG — OCSRE Architecture and Research Decisions

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Version:** v1.0.0 — Research Framework and Contracts  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**Status:** Proposed architecture and research decision record; not a deployment or validation record  
**License:** Apache-2.0  
**Canonical location:** `research-trace/DECISION-LOG.md`

## 1. Purpose and authority

This log records **why** the OCSRE framework chooses particular representations, interfaces, research protocols and governance boundaries. It complements, but does not replace, the normative `SPEC-001`–`SPEC-006`, the terminology in `DEFINITION-REGISTRY.md`, the proposed claims in `HYPOTHESIS-REGISTRY.md`, the adversarial fixtures in `COUNTEREXAMPLE-REGISTRY.md`, and the outstanding work in `UNRESOLVED-RESIDUALS.md`. It is not evidence that a design has been implemented or empirically validated.

**Authority order:** applicable external framework authority for its own semantics; explicit versioned SPEC contract for an OCSRE interface; versioned decision for architectural rationale; definition registry for terminology; narrative paper for motivation. Conflicts must be logged rather than silently reconciled. This order is a proposed repository convention, not a claim of authority over WE-SIO, SIF, UTN, MDT, WE-HDT, CDE or UIERU.

All eleven core OCSH hypotheses remain **E0 — Proposed**. The word *adopt* in this log means **adopt for the research baseline**, not deployed, validated, or proven optimal.

## 2. Decision record schema and lifecycle

Each decision has a stable `ADR-OCSRE-NNN` ID, short title, context, baseline decision, considered alternatives, rationale, costs/risks, supporting sources, affected hypotheses, reconsideration trigger and lifecycle status. Future revisions should add a dated amendment with evidence links; never overwrite history or invent dates.

| State | Meaning | Promotion requirement |
|---|---|---|
| Proposed | Candidate architecture not yet accepted into the baseline | Explicit review and alternatives |
| Baseline | Adopted for the v1.0.0 research framework only | Documented rationale and known risks |
| Under review | New evidence or conflict requires reassessment | Linked counterexample, study or incompatible contract |
| Superseded | Replaced by a versioned decision | Replacement ID and migration notes |
| Rejected | Considered and not adopted | Recorded rationale |
| Validated in scope | A decision has supporting executed evidence for a bounded claim | Reproducible evidence, independent review, explicit scope |

**Current state:** the 30 decisions below are **Baseline (research only)**. None has the status “Validated in scope.” Any implementation outcome, reviewer approval, run timestamp, benchmark score or external adoption not documented in the repository must be recorded as `TBD`, not inferred.

## 3. Decision index

| ID | Decision | Primary domain | State |
|---|---|---|---|
| ADR-OCSRE-001 | Object-centric integration rather than universal algorithm replacement | Representation | Baseline (research) |
| ADR-OCSRE-002 | Preserve classical deduction in a restricted fragment | Representation | Baseline (research) |
| ADR-OCSRE-003 | Separate identity, object view, and storage key | Representation | Baseline (research) |
| ADR-OCSRE-004 | Make perspective, time, and granularity first-class | Representation | Baseline (research) |
| ADR-OCSRE-005 | Keep ODK differential distinct from CDE state delta | Kernel / semantics | Baseline (research) |
| ADR-OCSRE-006 | Keep the ODK core domain-neutral under adapters | Kernel / semantics | Baseline (research) |
| ADR-OCSRE-007 | Object Plugins are governed capabilities, not arbitrary code | Kernel / semantics | Baseline (research) |
| ADR-OCSRE-008 | SQL-to-WE is semantic adaptation, not row wrapping | Kernel / semantics | Baseline (research) |
| ADR-OCSRE-009 | Preserve SQL three-valued logic and query grain | Kernel / semantics | Baseline (research) |
| ADR-OCSRE-010 | In-situ learning requires traceable feedback | Evidence / evolution | Baseline (research) |
| ADR-OCSRE-011 | Separate evidence, inference, scoring and authorization | Evidence / evolution | Baseline (research) |
| ADR-OCSRE-012 | Represent composite optimization as a global State-Container | Evidence / evolution | Baseline (research) |
| ADR-OCSRE-013 | CDE candidates are not committed actions | Evidence / evolution | Baseline (research) |
| ADR-OCSRE-014 | Govern dynamic search with path memory and bounded loops | Evidence / evolution | Baseline (research) |
| ADR-OCSRE-015 | CDE is an evolutionary localization pillar in SIF | Localization / identity | Baseline (research) |
| ADR-OCSRE-016 | Integrate UTN, MDT, WE-HDT via typed bindings | Localization / identity | Baseline (research) |
| ADR-OCSRE-017 | Transaction graph is evidence, not verified identity | Localization / identity | Baseline (research) |
| ADR-OCSRE-018 | Relay requires target-domain conformance | Relay / governance | Baseline (research) |
| ADR-OCSRE-019 | Preserve failed relays and counterexamples | Relay / governance | Baseline (research) |
| ADR-OCSRE-020 | Multi-agent agreement is not independent validation | Relay / governance | Baseline (research) |
| ADR-OCSRE-021 | Metric, Plugin and Policy evolve on distinct surfaces | Relay / governance | Baseline (research) |
| ADR-OCSRE-022 | Policy proposal must not confer policy authority | Relay / governance | Baseline (research) |
| ADR-OCSRE-023 | Separate reuse, transfer, spillover and scaling claims | Growth / code / trace | Baseline (research) |
| ADR-OCSRE-024 | Test untargeted spillover with frozen capability versions | Growth / code / trace | Baseline (research) |
| ADR-OCSRE-025 | Treat sustained scaling as unproven | Growth / code / trace | Baseline (research) |
| ADR-OCSRE-026 | Calling Graph is a localization entry point, not complete semantics | Growth / code / trace | Baseline (research) |
| ADR-OCSRE-027 | Code governance uses CDE candidate and authorization lifecycle | Growth / code / trace | Baseline (research) |
| ADR-OCSRE-028 | Contracts before runtime; explicit leftovers | Growth / code / trace | Baseline (research) |
| ADR-OCSRE-029 | Keep research-trace registries separately governed | Growth / code / trace | Baseline (research) |
| ADR-OCSRE-030 | Research v1.0.0 is framework-and-contracts, not validated runtime | Growth / code / trace | Baseline (research) |

## 4. Detailed architecture decision records

### ADR-OCSRE-001 — Object-centric integration rather than universal algorithm replacement

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Adopt a typed WE/Object interface as the shared coordination surface.

**Alternatives considered.** A monolithic reasoner; unrestricted natural-language orchestration.

**Rationale.** Shared references support composition while preserving specialized semantics.

**Tradeoffs and risks.** Interface proliferation, adapter costs, and possible false appearance of semantic unity.

**Primary research references.** OCSRE-001; SPEC-001; DEF-001–008.

**Related hypotheses.** OCSH-002/003/008.

**Reopen if.** Reject any claim that one interface proves universal equivalence.

### ADR-OCSRE-002 — Preserve classical deduction in a restricted fragment

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Specify grammar, model interpretation, and proof trace for a classical subsystem.

**Alternatives considered.** Treat all object scores as logical inference; claim unrestricted first-order completeness.

**Rationale.** Validity is testable only with explicitly declared assumptions and mapping.

**Tradeoffs and risks.** Fragment restrictions may limit expressivity.

**Primary research references.** OCSRE-002; SPEC-003; CASE-001; EXT-001.

**Related hypotheses.** OCSH-001.

**Reopen if.** Translation fails to preserve a valid entailment or admits an invalid one.

### ADR-OCSRE-003 — Separate identity, object view, and storage key

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Use namespace-qualified identity and contextual ObjectRef; record provisional resolution.

**Alternatives considered.** SQL primary key equals WE identity; graph address equals actor.

**Rationale.** Identity continuity and provenance cannot be inferred from storage structure.

**Tradeoffs and risks.** More identity governance and unresolved aliases.

**Primary research references.** SPEC-001; DEF-001–009; CASE-002/004.

**Related hypotheses.** OCSH-006/007.

**Reopen if.** Unambiguous identity mappings cannot be represented without breaking compatibility.

### ADR-OCSRE-004 — Make perspective, time, and granularity first-class

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Require typed scopes in resolution, comparisons, and inference.

**Alternatives considered.** Implicit global context; silent individual-to-group inheritance.

**Rationale.** Prevents context collapse and ecological inference.

**Tradeoffs and risks.** Extra metadata and abstentions.

**Primary research references.** OCSRE-003; SPEC-001/003; EXT-002.

**Related hypotheses.** OCSH-006.

**Reopen if.** Context checks reject valid cases at unacceptable rates.

### ADR-OCSRE-005 — Keep ODK differential distinct from CDE state delta

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** ODK computes contracted metric differences; CDE proposes typed state transitions.

**Alternatives considered.** Use one untyped delta operator for both.

**Rationale.** Measurement and mutation have different safety and semantic obligations.

**Tradeoffs and risks.** Translation layers between evaluation and evolution.

**Primary research references.** OCSRE-004/008; SPEC-002/006; DEF-017–027/037–045.

**Related hypotheses.** OCSH-002/005.

**Reopen if.** Formal semantics show a safe common abstraction with no loss of obligations.

### ADR-OCSRE-006 — Keep the ODK core domain-neutral under adapters

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Freeze versioned kernel semantics; specialize via typed adapters and metrics.

**Alternatives considered.** Domain-specific branches in core; shared numeric vector without semantics.

**Rationale.** Allows a falsifiable invariance experiment.

**Tradeoffs and risks.** Some domains may need incompatible comparators.

**Primary research references.** OCSRE-004; SPEC-002; CASE-005.

**Related hypotheses.** OCSH-002.

**Reopen if.** Necessary core changes or invalid comparison despite conformant adapters.

### ADR-OCSRE-007 — Object Plugins are governed capabilities, not arbitrary code

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Version capability contracts, dependencies, preconditions, effects, authority and conformance.

**Alternatives considered.** Implicit dynamic tool invocation.

**Rationale.** Makes transfer and rollback auditable.

**Tradeoffs and risks.** Registry and verification overhead.

**Primary research references.** OCSRE-005; SPEC-004; EXT-004.

**Related hypotheses.** OCSH-003/008.

**Reopen if.** Measured integration overhead dominates benefits or bypass is required.

### ADR-OCSRE-008 — SQL-to-WE is semantic adaptation, not row wrapping

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Use Bucketize, Normalize, Combine, Encode, Derive with explicit SQL semantics.

**Alternatives considered.** One SQL row becomes one WE by default.

**Rationale.** NULL, joins, aggregation and security cannot be ignored.

**Tradeoffs and risks.** Dialect-specific adapters and complex equivalence testing.

**Primary research references.** OCSRE-006; CASE-002; SPEC-001/004/005.

**Related hypotheses.** OCSH-007.

**Reopen if.** Equivalent SQL fixtures systematically diverge or disclose forbidden data.

### ADR-OCSRE-009 — Preserve SQL three-valued logic and query grain

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Represent unknown, missing and not-applicable distinctly; track join multiplicity.

**Alternatives considered.** Coerce NULL to false/zero; deduplicate without provenance.

**Rationale.** Avoids silent result corruption.

**Tradeoffs and risks.** More complicated metric and grouping contracts.

**Primary research references.** CASE-002; DEF-017–027.

**Related hypotheses.** OCSH-007.

**Reopen if.** A supported query cannot be represented without semantic loss.

### ADR-OCSRE-010 — In-situ learning requires traceable feedback

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Bind feedback to object state, provenance, time and perspective; keep revision history.

**Alternatives considered.** Unversioned online overwrite; LLM narrative as sole evidence.

**Rationale.** Supports correction and audit reconstruction.

**Tradeoffs and risks.** Storage and conflict-resolution burden.

**Primary research references.** OCSRE-007/009; SPEC-005.

**Related hypotheses.** OCSH-004.

**Reopen if.** Traceability gains absent under matched-budget tests.

### ADR-OCSRE-011 — Separate evidence, inference, scoring and authorization

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Keep distinct proof, observation, hypothesis, similarity and permission states.

**Alternatives considered.** Promote high similarity to fact; infer authorization from confidence.

**Rationale.** Avoids epistemic and governance category errors.

**Tradeoffs and risks.** Slower promotion and extra reviews.

**Primary research references.** OCSRE-009; SPEC-005; CASE-004.

**Related hypotheses.** OCSH-004/006.

**Reopen if.** Contracted distinctions fail to prevent false promotions.

### ADR-OCSRE-012 — Represent composite optimization as a global State-Container

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Store member entities, relations and invariants; validate global feasibility.

**Alternatives considered.** Optimize bus or transaction objects independently.

**Rationale.** Feasibility is often relational and global.

**Tradeoffs and risks.** State explosion and solver cost.

**Primary research references.** OCSRE-008; SPEC-006; CASE-003/004.

**Related hypotheses.** OCSH-005.

**Reopen if.** Global invariants cannot be enforced with the proposed model.

### ADR-OCSRE-013 — CDE candidates are not committed actions

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Use proposed, validated, authorized, committed and rolled-back states.

**Alternatives considered.** Auto-commit the highest-scoring candidate.

**Rationale.** Separates search utility from safety and control.

**Tradeoffs and risks.** Approval latency.

**Primary research references.** SPEC-006; CASE-003/006.

**Related hypotheses.** OCSH-005/011.

**Reopen if.** Lifecycle cannot represent necessary rollback/approval semantics.

### ADR-OCSRE-014 — Govern dynamic search with path memory and bounded loops

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Specify typed deltas, non-reuse on paths, NoSubtree and Loop-Back controls.

**Alternatives considered.** Unbounded repeated operations or silent pruning.

**Rationale.** Improves reproducibility and termination reasoning.

**Tradeoffs and risks.** May prune useful revisits without state equivalence proofs.

**Primary research references.** OCSRE-008; SPEC-006; CASE-003.

**Related hypotheses.** OCSH-005.

**Reopen if.** Valid solutions lost or loops persist under declared assumptions.

### ADR-OCSRE-015 — CDE is an evolutionary localization pillar in SIF

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Distinguish referential addressing from generation and validation of reachable states.

**Alternatives considered.** Treat localization only as database lookup.

**Rationale.** Makes candidate-state discovery explicit in SIF.

**Tradeoffs and risks.** Potential overlap with existing search and planning vocabulary.

**Primary research references.** OCSRE-010; EXT-002; SPEC-006.

**Related hypotheses.** OCSH-005/011.

**Reopen if.** Formal comparison finds no operational distinction from ordinary addressing.

### ADR-OCSRE-016 — Integrate UTN, MDT, WE-HDT via typed bindings

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Use stable references and explicit capability contracts; do not assert algorithm equivalence.

**Alternatives considered.** Collapse distinct indexing and reasoning methods into one engine.

**Rationale.** Retains external framework autonomy and supports interoperation.

**Tradeoffs and risks.** Cross-framework version and ontology conflicts.

**Primary research references.** OCSRE-010; EXT-002; DEF-046–055.

**Related hypotheses.** OCSH-011.

**Reopen if.** Binding contracts prove inadequate on target workflows.

### ADR-OCSRE-017 — Transaction graph is evidence, not verified identity

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Model composite actors as competing defeasible hypotheses.

**Alternatives considered.** Merge wallets into actors based only on flow similarity.

**Rationale.** Avoids false attribution and circular evidence.

**Tradeoffs and risks.** Persistent ambiguity and reduced decisive outputs.

**Primary research references.** CASE-004; OCSRE-009; SPEC-005.

**Related hypotheses.** OCSH-004/006.

**Reopen if.** Independent ground truth shows systematic false merging despite checks.

### ADR-OCSRE-018 — Relay requires target-domain conformance

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Freeze source capability; test adapters, semantic contracts, negatives and utility in target.

**Alternatives considered.** Copy a plugin and declare transfer successful.

**Rationale.** Separates portability from correctness and usefulness.

**Tradeoffs and risks.** Additional transfer costs and failed candidates.

**Primary research references.** OCSRE-011; CASE-005; SPEC-004/006.

**Related hypotheses.** OCSH-008.

**Reopen if.** No measurable net transfer under preregistered baselines.

### ADR-OCSRE-019 — Preserve failed relays and counterexamples

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Store failure evidence, invalid transfers and explicit leftovers as research assets.

**Alternatives considered.** Keep only successful artifacts.

**Rationale.** Supports collective learning and regression prevention.

**Tradeoffs and risks.** Registry growth and curation cost.

**Primary research references.** EXT-003/005; COUNTEREXAMPLE-REGISTRY.

**Related hypotheses.** OCSH-008/010.

**Reopen if.** Curation cost exceeds measurable learning value.

### ADR-OCSRE-020 — Multi-agent agreement is not independent validation

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Separate generator, challenger, validator and authorizer roles with evidence isolation.

**Alternatives considered.** Majority vote or shared-context consensus as proof.

**Rationale.** Correlated failures can produce confident agreement.

**Tradeoffs and risks.** Compute and coordination costs.

**Primary research references.** EXT-003; SPEC-005/006.

**Related hypotheses.** OCSH-008/010.

**Reopen if.** Independent review adds no robustness at equal budgets.

### ADR-OCSRE-021 — Metric, Plugin and Policy evolve on distinct surfaces

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Permit proposals for each; require independent contracts and governance for promotion.

**Alternatives considered.** Treat all changes as untyped self-improvement.

**Rationale.** Different failure modes require distinct checks.

**Tradeoffs and risks.** Cross-surface dependency complexity.

**Primary research references.** EXT-004; OCSRE-012.

**Related hypotheses.** OCSH-010.

**Reopen if.** Separating surfaces demonstrably blocks safe, useful evolution.

### ADR-OCSRE-022 — Policy proposal must not confer policy authority

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** No autonomous expansion of permissions or relaxation of mandatory safeguards.

**Alternatives considered.** Self-approval based on improved reward/score.

**Rationale.** Avoids reward hacking and governance capture.

**Tradeoffs and risks.** Human or external authority bottlenecks.

**Primary research references.** EXT-004; SPEC-005/006.

**Related hypotheses.** OCSH-010/011.

**Reopen if.** Policy boundary cannot be enforced in relevant deployment.

### ADR-OCSRE-023 — Separate reuse, transfer, spillover and scaling claims

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Require progressively stronger prospective evidence and cost accounting.

**Alternatives considered.** Infer scaling from more plugins, artifacts or agent count.

**Rationale.** Avoids overclaiming and metric substitution.

**Tradeoffs and risks.** Longitudinal studies expensive.

**Primary research references.** OCSRE-011/012; EXT-005; HYPOTHESIS-REGISTRY.

**Related hypotheses.** OCSH-008/009/010.

**Reopen if.** Preregistered measures fail to distinguish constructs.

### ADR-OCSRE-024 — Test untargeted spillover with frozen capability versions

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Predeclare held-out tasks, freeze versions and compare equal-resource baselines.

**Alternatives considered.** Post-hoc cherry-pick a success and call it spillover.

**Rationale.** Controls leakage and retrospective selection.

**Tradeoffs and risks.** Task design and contamination concerns.

**Primary research references.** EXT-005; CASE-005.

**Related hypotheses.** OCSH-009.

**Reopen if.** No net benefit on prospectively held-out tasks.

### ADR-OCSRE-025 — Treat sustained scaling as unproven

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Use longitudinal net capability measures with negative evidence and uncertainty.

**Alternatives considered.** Claim unlimited Delta or inevitable Scaling Law.

**Rationale.** Finite results cannot establish open-ended growth.

**Tradeoffs and risks.** Restrained external claims.

**Primary research references.** OCSRE-012; EXT-004/005.

**Related hypotheses.** OCSH-010.

**Reopen if.** Growth saturates or validation cost dominates across time.

### ADR-OCSRE-026 — Calling Graph is a localization entry point, not complete semantics

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Join call edges with data/control flow, config, schemas, tests and security dependencies.

**Alternatives considered.** Assume unchanged call graph implies safe change.

**Rationale.** Captures semantic regressions invisible to call structure.

**Tradeoffs and risks.** Graph construction and false positives.

**Primary research references.** CASE-006; EXT-002; OCSRE-010.

**Related hypotheses.** OCSH-011.

**Reopen if.** Expanded graphs provide no improvement over simpler baselines.

### ADR-OCSRE-027 — Code governance uses CDE candidate and authorization lifecycle

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Represent patches and deployment changes as typed, reviewable deltas.

**Alternatives considered.** Conflate generated patch, passing tests, merge and deployment.

**Rationale.** Supports impact review, rollback and security boundaries.

**Tradeoffs and risks.** CI integration complexity.

**Primary research references.** CASE-006; SPEC-006.

**Related hypotheses.** OCSH-011.

**Reopen if.** No measurable improvement in defect containment or traceability.

### ADR-OCSRE-028 — Contracts before runtime; explicit leftovers

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Publish interfaces, negative tests and unresolved residuals prior to claims of execution.

**Alternatives considered.** Use demos as substitutes for definitions and tests.

**Rationale.** Improves auditability and honest maturity reporting.

**Tradeoffs and risks.** Documentation burden.

**Primary research references.** SPEC-001–006; all research-trace registries.

**Related hypotheses.** OCSH-001–011.

**Reopen if.** Contract-first workflow impedes reproducibility without measurable benefit.

### ADR-OCSRE-029 — Keep research-trace registries separately governed

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Maintain hypothesis, definition, counterexample, decision and residual registries with cross-links.

**Alternatives considered.** One unstructured changelog.

**Rationale.** Different records answer different audit questions.

**Tradeoffs and risks.** Cross-link drift and duplicate records.

**Primary research references.** research-trace/*.

**Related hypotheses.** OCSH-001–011.

**Reopen if.** Cross-reference maintenance cost overwhelms traceability gain.

### ADR-OCSRE-030 — Research v1.0.0 is framework-and-contracts, not validated runtime

**Status:** Baseline (research); **implementation:** TBD; **validation:** none claimed.

**Decision.** Publish synthetic examples and test designs with explicit E0 status.

**Alternatives considered.** Advertise benchmarks, proofs, production security or scaling without evidence.

**Rationale.** Preserves evidence integrity and reader expectations.

**Tradeoffs and risks.** May limit adoption claims.

**Primary research references.** README; HYPOTHESIS-REGISTRY; VALIDATION-ROADMAP.

**Related hypotheses.** OCSH-001–011.

**Reopen if.** Executed, reviewed evidence justifies explicit, scoped status promotion.

## 5. Cross-cutting non-equivalence constraints

The decisions above establish the following **non-equivalences**; they are not optional wording preferences. A conformant implementation must enforce the relevant contract rather than relying on a narrative disclaimer.

| Distinction | Why it matters | Anchoring decisions |
|---|---|---|
| WE identity ≠ SQL primary key ≠ actor attribution | Storage, referential continuity and real-world control have different authorities | 003, 008, 017 |
| ObjectRef ≠ mutation permission | Locating an object does not grant action authority | 003, 013, 022 |
| Deductive entailment ≠ evidence support ≠ metric similarity | Prevents false proofs and ungrounded conclusions | 002, 005, 011 |
| ODK Differential ≠ CDE Typed Delta | Evaluation does not itself define state mutation | 005, 012, 013 |
| Valid candidate ≠ authorized action ≠ committed deployment | Search and governance are separate | 013, 022, 027 |
| Shared interface ≠ domain equivalence | Reuse requires domain-specific semantic conformance | 001, 006, 018 |
| Agent consensus ≠ independent validation | Correlated errors survive voting | 020 |
| Capability reuse ≠ transfer ≠ untargeted spillover ≠ scaling | Different evidence thresholds | 023, 024, 025 |
| Calling Graph stability ≠ semantic stability | Dependencies beyond call edges matter | 026 |

## 6. Decision-to-specification conformance map

| SPEC | Decisions most directly governed | Required negative testing focus |
|---|---|---|
| SPEC-001 — Identity, Perspective and State | 001, 003, 004, 008, 012, 016 | Ambiguous identity, stale state, invalid cross-grain access |
| SPEC-002 — ODK and Comparator | 005, 006, 009, 021 | Unit mismatch, missing values, incompatible perspectives |
| SPEC-003 — Classical Reasoning and Granularity | 002, 004, 011 | Invalid entailment, quantifier misuse, group-to-person fallacy |
| SPEC-004 — Plugin and Capability Composition | 006, 007, 008, 018, 021 | Hidden effects, incompatible types, negative transfer |
| SPEC-005 — Learning, Feedback and Epistemic Governance | 009, 010, 011, 017, 020, 022 | Evidence laundering, unsupported fact promotion, correlated review |
| SPEC-006 — WE-Native CDE, Composite State and Relay | 005, 012–015, 018, 020–022, 027 | Constraint violation, path repetition, unauthorized commit |

**Note:** this is a traceability index. It does not assert that any conformance suite has been executed.

## 7. Decision-to-case and extension map

| Research surface | Relevant decisions | Proposed evaluation question |
|---|---|---|
| CASE-001 — Person and Classical Reasoning | 002–004, 011 | Is valid classical entailment preserved without identity or granularity leakage? |
| CASE-002 — SQL-Native Object Adaptation | 003, 006, 008, 009 | Are SQL semantics, access and provenance preserved under adapters? |
| CASE-003 — School-Bus Scheduling | 004, 005, 012–014 | Can global constraints survive candidate fleet-duty deltas? |
| CASE-004 — Transaction and Compositional Identity | 003, 010–013, 017 | Are competing actor hypotheses kept distinct from observations? |
| CASE-005 — Cross-Domain Object Plugin Relay | 006, 007, 018–020, 023 | Does target conformance yield net transfer under equal budgets? |
| CASE-006 — AI-Generated Code Governance | 011, 013, 016, 022, 026, 027 | Are semantic impacts and authority boundaries caught beyond call graphs? |
| EXT-001 — History of Logic | 002, 004, 011 | Are formal and non-formal inference claims separated? |
| EXT-002 — SIF Localization | 003, 012, 015, 016 | Is evolutionary localization distinguishable and operational? |
| EXT-003 — Multi-Agent Relay | 018–020 | Does independent challenge improve results net of coordination cost? |
| EXT-004 — Metric/Plugin/Policy Evolution | 005, 007, 021, 022 | Can evolution improve capability without self-authorizing policy changes? |
| EXT-005 — Spillover and Scaling | 018, 019, 023–025 | Are untargeted and longitudinal gains measurable without leakage? |

## 8. Proposed decision-change protocol

1. **Trigger.** A counterexample, failed conformance test, external framework revision, independent experiment, security incident or reproducible incompatibility opens a review.
2. **Preserve baseline.** Record the exact decision ID and contract versions; do not rewrite the original rationale.
3. **Describe the alternative.** State expected gains, affected identities, interfaces, evidence and permissions.
4. **Construct adversarial fixtures.** Include at least one positive preservation test and one negative boundary test for each changed invariant.
5. **Assess blast radius.** Enumerate affected SPECs, OCSRE papers, cases, hypotheses, definitions, relay artifacts and deployed consumers (if any).
6. **Review independently.** A proposer must not be the sole validator of a security-sensitive or policy-changing decision.
7. **Approve or reject.** Record accountable authority, dated evidence references and explicit leftovers; absent authority remains `TBD`.
8. **Version and migrate.** Supersede by new decision ID or amendment; record compatibility and rollback plan.
9. **Update registries.** Synchronize hypothesis status only with evidence, update counterexamples and residuals, and add release notes when applicable.

**No automatic status promotion:** a successful synthetic illustration, passing test on one fixture, or AI-generated recommendation is insufficient to mark a research decision as empirically validated.

## 9. Proposed conformance obligations for decision governance

The following **DLG-001–020** obligations are design requirements for a future registry checker and review process; none is asserted to have been executed.

| ID | Proposed obligation |
|---|---|
| DLG-001 | Every decision has a stable unique ID and explicit research status. |
| DLG-002 | A decision records at least one rejected or deferred alternative. |
| DLG-003 | A decision states its rationale and known cost. |
| DLG-004 | External framework semantics are not silently redefined. |
| DLG-005 | Decision references resolve to versioned source documents. |
| DLG-006 | Conflicting SPEC and decision language creates a review item. |
| DLG-007 | Identity decisions preserve provisional and ambiguous states. |
| DLG-008 | Inference decisions preserve proof/evidence/score distinctions. |
| DLG-009 | ODK and CDE deltas remain type-distinct in interfaces. |
| DLG-010 | SQL adapters preserve declared NULL and join semantics. |
| DLG-011 | Security decisions never infer permission from object access. |
| DLG-012 | CDE promotion requires separate validation and authorization. |
| DLG-013 | Composite changes are checked against global invariants. |
| DLG-014 | Agent agreement is not used as the only acceptance criterion. |
| DLG-015 | Relay promotion requires target-domain negative tests. |
| DLG-016 | Growth claims retain prospective baselines and cost accounting. |
| DLG-017 | Code governance tests include non-call dependencies. |
| DLG-018 | Supersession retains old record and links replacement. |
| DLG-019 | Every status promotion links immutable executed evidence. |
| DLG-020 | Residuals and counterexamples receive bidirectional links. |

## 10. Illustrative positive and adversarial registry tests

These are **test specifications**, not observed outcomes.

| Fixture | Setup | Expected result |
|---|---|
| POS-001 | ADR with alternatives, SPEC references and explicit risks | Registry accepts as research baseline |
| POS-002 | New evidence requests review of ADR-OCSRE-026 | Existing record preserved; review item opened |
| POS-003 | Proposed CDE delta passes feasibility but lacks approval | Remains uncommitted |
| POS-004 | SQL adapter reports `UNKNOWN` rather than coercing NULL | Semantic boundary retained |
| POS-005 | Independent failed relay is documented | Failure kept in trace registry |
| POS-006 | Scaling experiment reports null results | OCSH status remains evidence-appropriate; no positive overclaim |
| NEG-001 | Duplicate ADR ID | Reject registry update |
| NEG-002 | Status set to validated without evidence ID | Reject status change |
| NEG-003 | SPEC conflict silently overridden by decision log | Flag conflict |
| NEG-004 | Wallet flow similarity recorded as verified identity | Reject promotion |
| NEG-005 | Metric comparison treated as authorized mutation | Reject operation |
| NEG-006 | Policy plugin approves its own increased privileges | Reject authorization |
| NEG-007 | Calling Graph unchanged used as complete safety proof | Require additional semantic analysis |
| NEG-008 | Agent majority vote substitutes for independent checks | Reject validation claim |
| NEG-009 | Cross-domain plugin copied without target tests | Reject relay promotion |
| NEG-010 | Untargeted-task claim selected after examining all test tasks | Flag selection bias |
| NEG-011 | Invalid granularity inheritance introduced | Reject inferred conclusion |
| NEG-012 | Original decision deleted on supersession | Reject history rewrite |

## 11. Explicit leftovers and unresolved decision questions

The following **DLR-001–024** are open research and engineering tasks, not implied completed work.

| ID | Explicit leftover |
|---|---|
| DLR-001 | Specify the formal identity authority and alias-resolution conflict protocol. |
| DLR-002 | Define a machine-checkable ObjectRef schema and compatibility matrix. |
| DLR-003 | Freeze a precise classical proof fragment and translation semantics. |
| DLR-004 | Specify typed metric units, missingness and perspective algebra. |
| DLR-005 | Publish ODK kernel invariance tests across at least three domains. |
| DLR-006 | Measure Object Plugin adaptation cost against bespoke integrations. |
| DLR-007 | Formalize SQL NULL, join, snapshot and row-level security preservation. |
| DLR-008 | Implement and test feedback provenance and revision invalidation. |
| DLR-009 | Define evidence dependency and correlated-source accounting. |
| DLR-010 | Formalize CDE state-equivalence and non-reuse rules. |
| DLR-011 | Prove or bound Loop-Back termination under stated assumptions. |
| DLR-012 | Specify global invariants for composite WE membership and lifecycle. |
| DLR-013 | Operationalize evolutionary localization relative to ordinary search. |
| DLR-014 | Version UTN/MDT/WE-HDT external binding contracts. |
| DLR-015 | Construct independent ground truth for compositional identity cases. |
| DLR-016 | Define target-domain conformance thresholds for relay promotion. |
| DLR-017 | Quantify failed-relay retention cost and long-term value. |
| DLR-018 | Develop independent multi-agent evaluation with equal compute budgets. |
| DLR-019 | Specify governance authority for Metric/Plugin/Policy evolution. |
| DLR-020 | Prevent circular metrics and policy self-authorization. |
| DLR-021 | Preregister untargeted task families and contamination controls. |
| DLR-022 | Design longitudinal scaling studies with net resource accounting. |
| DLR-023 | Benchmark code-impact localization beyond Calling Graph alone. |
| DLR-024 | Implement registry linting, bidirectional links and review audit trail. |

## 12. Relation to research hypotheses and evidence status

No ADR is a proof of any OCSH claim. A decision may motivate an experiment, but only evidence gathered under a specified protocol may update `HYPOTHESIS-REGISTRY.md`. A failed test may indicate (a) an implementation defect, (b) an underspecified contract, (c) a counterexample to a stated guarantee, or (d) a falsification of a research hypothesis; the review must distinguish these outcomes. Negative results and narrowed scope are valid research outputs.

The log is intentionally **conservative**: the repository is a v1.0.0 research framework and contracts baseline, not a benchmark report, deployed system, independent replication, formal proof of general soundness, or demonstrated new scaling law.

## 13. Maintenance and release integration

- Keep this file at `research-trace/DECISION-LOG.md`; link it from `CONTENTS.md`, `START-HERE.md` and relevant specs when those files are prepared.
- Link each substantive change to `CHANGELOG.md` and the corresponding versioned release notes.
- Update `DEFINITION-REGISTRY.md` for semantic changes, `COUNTEREXAMPLE-REGISTRY.md` for observed or proposed failure fixtures, and `UNRESOLVED-RESIDUALS.md` for unresolved dependencies.
- Record actual reviewers, execution dates, hashes and evidence only after they exist; use `TBD` otherwise.
- Retain superseded decisions for reproducibility and collective learning.

## 14. Closing research position

OCSRE is an **object-centered integration and evolution research program**. Its architectural choices seek to make identity, reasoning, measurement, state transitions, localization, relay and governance composable without collapsing their distinct semantics. The decisions above are revisable hypotheses about sound engineering structure; their value must ultimately be established by executable contracts, adversarial counterexamples, independent evaluation and resource-accounted longitudinal evidence.
