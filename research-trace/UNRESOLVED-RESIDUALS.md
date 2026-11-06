# UNRESOLVED-RESIDUALS — OCSRE Research Trace

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Version:** v1.0.0 — Research Framework and Contracts  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**Status:** Open research backlog and explicit-leftover registry; no implementation or empirical validation implied  
**License:** Apache-2.0  
**Canonical location:** `research-trace/UNRESOLVED-RESIDUALS.md`

## 1. Purpose and research discipline

An **unresolved residual** is an identifiable gap between a stated research claim, a normative interface, an available evidence artifact, and what can actually be established. Residuals include missing definitions, incomplete proofs, absent test fixtures, unmeasured engineering costs, semantic mismatches, negative results awaiting diagnosis, and unresolved governance boundaries. A residual is **not** a hidden success, an implementation bug by default, or evidence that a hypothesis has been falsified.

This file is the canonical *cross-document* backlog for OCSRE v1.0.0. Local `Explicit Leftovers` in papers, SPECs, CASEs, and EXTs remain authoritative within their documents. The cross-document records here consolidate **themes**, not necessarily one-to-one mappings to local leftover identifiers. Do not silently equate `URL-###` with local `SBS`, `CXR`, `DLR`, or other IDs. Where precise matching has not been reviewed, the link is marked `mapping TBD`.

**Research rule:** Specifications/Contracts First; Conformance Before Runtime; Explicit Leftover. A completed manuscript, an illustrative calculation, or agreement among agents does not resolve a residual. All eleven core hypotheses `OCSH-001`–`OCSH-011` remain **E0 — Proposed**. No execution, replication, deployment, independent review, or measured scaling is asserted in this document.

## 2. Authority, links, and non-equivalence

- `SPEC-001`–`SPEC-006` own their proposed normative interface requirements; a residual cannot amend a SPEC by implication.
- `DEFINITION-REGISTRY.md` owns terminology; `HYPOTHESIS-REGISTRY.md` owns OCSH claim wording and evidence states.
- `COUNTEREXAMPLE-REGISTRY.md` owns `CEX-001`–`CEX-034` challenge records; a proposed adversarial fixture is not an observed failure.
- `DECISION-LOG.md` owns `ADR-OCSRE-001`–`ADR-OCSRE-030` research-baseline rationales. Decisions can be reopened; the historical decision must remain intact.
- Papers `OCSRE-001`–`012`, cases `CASE-001`–`006`, and extensions `EXT-001`–`005` supply conceptual and proposed evaluation surfaces.
- External frameworks WE-SIO, SIF, UTN, MDT, WE-HDT, CDE, UIERU, SSICR, AQSI, and ISGFTR retain their own semantics and authority. Interface interoperability does **not** imply mathematical or implementation equivalence.

The following distinctions must survive every closure decision: identity versus storage key; proof versus empirical truth; evidence versus identity attribution; metric differential versus state delta; candidate versus committed action; agent consensus versus independent validation; reuse versus transfer versus spillover versus sustained scaling.

## 3. Registry schema and status model

Each entry has a stable ID `URL-001` onward (URL here means **Unresolved Residual Ledger**, not a web address). Required fields are: `id`, `title`, `domain`, `problem`, `why_unresolved`, `affected_claims`, `dependencies`, `priority`, `status`, `closure_artifact`, `acceptance_criteria`, `negative_test`, `owner`, `evidence`, `review_date`, and `next_action`. The compact records in Section 5 provide the core fields; the remaining operational fields are initially `TBD` until a named owner and reproducible protocol exist.

| Status | Meaning | Evidence gate |
|---|---|---|
| O — Open | Gap identified; no accepted closure evidence | Entry and affected contract/claim identified |
| S — Specified | Closure protocol and adversarial oracle reviewed | Frozen fixtures, metrics, baselines and ownership |
| I — Investigating | Work underway; no conclusion assumed | Dated study or formal analysis log |
| B — Blocked | External dependency or ambiguity prevents test | Explicit blocker and restart trigger |
| Q — Qualified closure | Resolved only within a declared bounded scope | Executed/reviewed artifact, limitations, regression tests |
| C — Closed | Closure criteria satisfied for the recorded claim | Reproducible evidence, independent review, linked revisions |
| R — Reopened | New counterexample invalidates or narrows closure | New evidence and prior closure reference |

**Initial status:** all `URL-001`–`URL-040` are `O — Open`. Priority `P0` indicates a potential assurance or safety boundary, `P1` a core research validity blocker, and `P2` a valuable longer-term research opportunity. Priorities are planning judgments, not measured likelihoods.

## 4. Master index

| ID | Short name | Domain | Priority | Primary OCSH | Status |
|---|---|---|---|---|---|
| URL-001 | Canonical WE identity binding | Identity | P0 | 006,007 | O |
| URL-002 | ObjectRef lifecycle and versioning | Identity | P1 | 006 | O |
| URL-003 | Perspective compatibility calculus | Identity | P1 | 006 | O |
| URL-004 | Granularity lifting and projection | Identity | P0 | 001,006 | O |
| URL-005 | Temporal and snapshot alignment | Identity | P0 | 006,007 | O |
| URL-006 | Restricted deduction preservation proof | Logic | P1 | 001 | O |
| URL-007 | Defeasible versus deductive proof traces | Logic | P0 | 001,004 | O |
| URL-008 | Metric type and unit algebra | ODK | P0 | 002,006 | O |
| URL-009 | Missingness and partial metric semantics | ODK | P1 | 002,007 | O |
| URL-010 | Kernel invariance benchmark | ODK | P1 | 002 | O |
| URL-011 | Plugin contract compatibility | Plugin | P0 | 003,008 | O |
| URL-012 | Plugin dependency and revocation | Plugin | P0 | 003,008 | O |
| URL-013 | SQL NULL and three-valued semantics | SQL | P0 | 007 | O |
| URL-014 | Join multiplicity and grain | SQL | P0 | 007 | O |
| URL-015 | Row-level security preservation | SQL | P0 | 007 | O |
| URL-016 | SQL snapshot and provenance | SQL | P1 | 007 | O |
| URL-017 | Feedback attribution and leakage | Learning | P1 | 004 | O |
| URL-018 | In-situ learning versus drift | Learning | P1 | 004 | O |
| URL-019 | Composite-state invariant calculus | CDE | P0 | 005 | O |
| URL-020 | Typed Delta composition and rollback | CDE | P0 | 005 | O |
| URL-021 | Path memory and loop termination | CDE | P1 | 005 | O |
| URL-022 | Candidate scoring versus authorization | CDE | P0 | 005,011 | O |
| URL-023 | CDE evolutionary localization contract | SIF | P1 | 005,008 | O |
| URL-024 | UTN/MDT/WE-HDT interoperability | SIF | P1 | 006,008 | O |
| URL-025 | School-bus realism gap | CASE | P1 | 005 | O |
| URL-026 | Composite identity non-identifiability | CASE | P0 | 004,006 | O |
| URL-027 | Weak evidence dependence and calibration | Evidence | P0 | 004 | O |
| URL-028 | Evidence access and privacy | Evidence | P0 | 004,011 | O |
| URL-029 | Relay semantic equivalence limits | Relay | P1 | 003,008 | O |
| URL-030 | Independent multi-agent validation | Relay | P1 | 008 | O |
| URL-031 | Relay cost and negative transfer | Relay | P1 | 003,008 | O |
| URL-032 | Metric/Plugin/Policy co-evolution safety | Evolution | P0 | 009,010 | O |
| URL-033 | Untargeted-task evaluation protocol | Spillover | P1 | 009 | O |
| URL-034 | Resource-normalized longitudinal scaling | Scaling | P1 | 010 | O |
| URL-035 | Novelty and capability-count inflation | Scaling | P1 | 010 | O |
| URL-036 | Calling Graph blind spots | Code | P0 | 011 | O |
| URL-037 | Multi-graph impact soundness | Code | P0 | 011 | O |
| URL-038 | AI code change authorization chain | Code | P0 | 011 | O |
| URL-039 | Reproducible conformance harness | Infrastructure | P1 | 001–011 | O |
| URL-040 | Independent review and evidence governance | Infrastructure | P1 | 001–011 | O |

## 5. Detailed unresolved residual records

### 5.1 Identity, perspective, granularity, and time

**URL-001 — Canonical WE identity binding.** A database row key, display name, account address, and WE identity may refer to different semantic entities. *Unresolved:* a portable binding protocol with authority, collision handling, lineage, and cross-source identity uncertainty. **Closure:** SPEC-aligned identity mapping with synthetic collisions and reversible provenance; independently verified that no ambiguous join silently merges identities. **Negative test:** equal labels or reused keys must not imply same entity. **Links:** SPEC-001, CASE-002, CASE-004, CEX-001–004; OCSH-006/007.

**URL-002 — ObjectRef lifecycle and versioning.** References may outlive snapshots, permissions, schemas, or entity revisions. *Unresolved:* stable referent versus versioned view semantics, invalidation, and migration. **Closure:** versioned ObjectRef contract and stale-reference tests, including revoked authority. **Negative test:** a stale ObjectRef cannot silently resolve to a newly reassigned entity. **Links:** OCSRE-001/003, SPEC-001; OCSH-006.

**URL-003 — Perspective compatibility calculus.** Different perspectives can produce distinct metrics or truth assessments. *Unresolved:* when comparison, fusion, and delegation are lawful. **Closure:** explicit compatibility predicates, conversion provenance, and counterexamples for incompatible perspectives. **Negative test:** scores under incompatible perspectives cannot be compared as if commensurate. **Links:** OCSRE-003/004, EXT-001; OCSH-006.

**URL-004 — Granularity lifting and projection.** Individual, group, and composite-system predicates are not interchangeable. *Unresolved:* typed aggregation and projection rules with formal proof obligations. **Closure:** validated permitted operators and rejection of ecological/atomistic fallacies. **Negative test:** a group-level mean does not prove an individual's value. **Links:** CASE-001/003, SPEC-003, CEX-007/008; OCSH-001/006.

**URL-005 — Temporal and snapshot alignment.** Inferences and object comparisons may combine observations from incompatible times. *Unresolved:* temporal validity intervals, snapshot isolation, and event-time versus processing-time policies. **Closure:** versioned temporal contracts and replayable stale-data fixtures. **Negative test:** a current claim cannot silently inherit a past state. **Links:** CASE-002/004, SPEC-001/005; OCSH-006/007.

### 5.2 Logic, proof, and epistemic boundaries

**URL-006 — Restricted deduction preservation proof.** The Socrates-style fragment illustrates classical entailment but does not prove a general preservation theorem. *Unresolved:* exact grammar, semantics, soundness assumptions, and a mechanized or independently checked proof. **Closure:** formal fragment and proof obligations with positive and invalid-syllogism regression suite. **Negative test:** invalid inference must not acquire a proof solely through object annotation. **Links:** OCSRE-002, CASE-001, EXT-001, SPEC-003; OCSH-001.

**URL-007 — Defeasible versus deductive proof traces.** Evidence, metric similarity, and probabilistic support can appear alongside logical derivations. *Unresolved:* machine-checkable typed traces preventing promotion between epistemic classes. **Closure:** proof/evidence/decision trace schema with rejection of unauthorized coercions. **Negative test:** a high similarity score is not accepted as entailment or identity proof. **Links:** OCSRE-009, CASE-004, CEX-005/006; OCSH-001/004.

### 5.3 ODK, metrics, and Object Plugins

**URL-008 — Metric type and unit algebra.** Metrics require units, domains, orientation, normalization, missingness, and comparison compatibility. *Unresolved:* compositional type rules and unit conversions. **Closure:** typed reference implementation with unit-mismatch rejection and dimensionally valid outputs. **Negative test:** counts cannot be subtracted from percentages without a declared transform. **Links:** OCSRE-004, SPEC-002; OCSH-002/006.

**URL-009 — Missingness and partial metric semantics.** Absent, null, censored, inaccessible, and not-applicable values have different meanings. *Unresolved:* cross-adapter treatment and partial order semantics. **Closure:** explicit missingness lattice and tests for each category. **Negative test:** unknown is not silently treated as zero. **Links:** OCSRE-004/006, CASE-002; OCSH-002/007.

**URL-010 — Kernel invariance benchmark.** An unchanged ODK core is a research claim, not a demonstrated cross-domain property. *Unresolved:* operational boundary of core versus adapter and performance under equivalent budgets. **Closure:** frozen kernel binary/hash, domain adapters, independent conformance and performance reports. **Negative test:** hidden domain-specific patches invalidate the claimed invariance. **Links:** CASE-005, EXT-005; OCSH-002.

**URL-011 — Plugin contract compatibility.** A Plugin may accept an ObjectRef while misinterpreting its perspective, unit, or authority. *Unresolved:* behavioral subtyping, compatibility profiles, and version negotiation. **Closure:** executable SPEC-004 contract suite and explicit incompatibility errors. **Negative test:** syntactic interface matching must not bypass semantic incompatibility. **Links:** OCSRE-005, CASE-005, EXT-004; OCSH-003/008.

**URL-012 — Plugin dependency and revocation.** Relay artifacts can retain capabilities after a source Plugin or permission is revoked. *Unresolved:* dependency graph, revocation propagation, and rollback. **Closure:** lineage and revocation tests across composed Plugins and cached artifacts. **Negative test:** revoked authority cannot persist via a previously cached relay. **Links:** SPEC-004/006, EXT-003/004; OCSH-003/008.

### 5.4 SQL-to-WE semantic adaptation

**URL-013 — SQL NULL and three-valued semantics.** SQL predicates may evaluate to TRUE, FALSE, or UNKNOWN. *Unresolved:* faithful mapping into WE evidence and typed missingness. **Closure:** SQL engine reference fixtures and expected WE outputs for NULL-sensitive predicates. **Negative test:** `UNKNOWN` must not silently become `FALSE`. **Links:** OCSRE-006, CASE-002, SPEC-001/004; OCSH-007.

**URL-014 — Join multiplicity and aggregation grain.** One-to-many joins can multiply rows and inflate aggregate metrics. *Unresolved:* declared grain contracts and lineage-preserving aggregation. **Closure:** fixtures with duplicate joins, grouped outputs, and cardinality assertions. **Negative test:** joined duplicates cannot silently increase student counts or inventory totals. **Links:** CASE-002, CEX SQL category; OCSH-007.

**URL-015 — Row-level security preservation.** Semantic adaptation can accidentally expose restricted rows or derived aggregates. *Unresolved:* policy equivalence, aggregation leakage, and cross-tenant isolation. **Closure:** access-control threat model, deny-by-default fixtures, and independent security review. **Negative test:** restricted data cannot be reconstructed through an Object Plugin. **Links:** CASE-002, SPEC-004/006; OCSH-007.

**URL-016 — SQL snapshot and provenance.** Transformation outputs may combine transactions or views from different database snapshots. *Unresolved:* snapshot token propagation and source-to-object provenance. **Closure:** replayable versioned extraction pipeline and invalidation checks. **Negative test:** mixed-snapshot data cannot be promoted as a coherent state without an explicit reconciliation rule. **Links:** OCSRE-006, CASE-002; OCSH-007.

### 5.5 In-situ learning and CDE state evolution

**URL-017 — Feedback attribution and leakage.** Observed gains may reflect target leakage, selection bias, or feedback from an already altered policy. *Unresolved:* causal attribution protocol and held-out evaluation. **Closure:** pre-registered feedback sources, leakage tests, ablations, and baseline comparisons. **Negative test:** evaluation labels cannot enter the candidate-generation context. **Links:** OCSRE-007, EXT-005; OCSH-004.

**URL-018 — In-situ learning versus drift.** Feedback-driven adaptation may improve local scores while degrading safety or transferability. *Unresolved:* drift detectors, rollback criteria, and time-based evaluation. **Closure:** longitudinal protocol with negative-transfer detection and reversible versions. **Negative test:** local improvement cannot suppress a newly observed hard-constraint violation. **Links:** OCSRE-007, SPEC-005; OCSH-004.

**URL-019 — Composite-state invariant calculus.** Individually legal changes may jointly violate fleet, temporal, capacity, or privacy constraints. *Unresolved:* complete invariant coverage and compositional checking. **Closure:** formal or exhaustive bounded invariant tests for a specified composite-state model. **Negative test:** locally feasible trip assignments must be rejected if fleet-wide conflicts remain. **Links:** OCSRE-008, CASE-003, SPEC-005; OCSH-005.

**URL-020 — Typed Delta composition and rollback.** Delta ordering, reversibility, conflicts, and partial failures remain underspecified across domains. *Unresolved:* algebraic composition rules and transaction boundaries. **Closure:** state-transition reference semantics, conflict fixtures, rollback and idempotency tests. **Negative test:** a partially committed composite Delta must not leave an unapproved intermediate state. **Links:** CDE, CASE-003/006, SPEC-005; OCSH-005.

**URL-021 — Path memory and loop termination.** Dynamic M→N branching, NoSubtree and Loop-Back require precise scope and termination conditions. *Unresolved:* path-local non-reuse, finite-budget completeness tradeoffs, and convergence guarantees. **Closure:** declared search semantics, termination proof for bounded fragment, stress tests for cycles. **Negative test:** a candidate path cannot reuse a forbidden Delta through aliasing. **Links:** OCSRE-008, CASE-003, EXT-003; OCSH-005.

**URL-022 — Candidate scoring versus authorization.** ODK scores and validators do not grant execution authority. *Unresolved:* enforceable transition between proposal, validated candidate, approval, commit and rollback. **Closure:** capability-based authorization contract and fail-closed tests. **Negative test:** a high-scoring candidate cannot bypass policy approval. **Links:** SPEC-005/006, CASE-006, EXT-004; OCSH-005/011.

### 5.6 SIF localization and applied composite cases

**URL-023 — CDE evolutionary localization contract.** SIF localization of existing nodes differs from searching for new reachable states. *Unresolved:* formal addressability of generable states and their validation evidence. **Closure:** typed interface for `existing-reference` versus `candidate-state/path`, with conformance fixtures. **Negative test:** a generated candidate must not be represented as an existing committed WE. **Links:** EXT-002, OCSRE-010, ADR-OCSRE-015; OCSH-005/008.

**URL-024 — UTN/MDT/WE-HDT interoperability.** Shared ObjectRef bindings do not establish algorithmic equivalence or lossless conversion. *Unresolved:* mapping semantics, address stability, complexity, and provenance. **Closure:** versioned adapters with round-trip tests where losslessness is claimed; explicit loss reports otherwise. **Negative test:** an incompatible locator cannot silently resolve to a different object. **Links:** OCSRE-010, EXT-002; OCSH-006/008.

**URL-025 — School-bus realism gap.** Fixed-trip synthetic examples omit road travel, driver shifts, stop sequences, special-needs requirements, and operational uncertainty. *Unresolved:* realistic data and optimization quality under hard constraints. **Closure:** privacy-safe benchmark, documented solver baseline, complete constraints, and sensitivity analysis. **Negative test:** a two-bus candidate is invalid if required deadhead or driver rules make it infeasible. **Links:** CASE-003, CASE-005; OCSH-005.

**URL-026 — Composite identity non-identifiability.** Multiple actor-control hypotheses may explain the same transaction graph. *Unresolved:* identifiability conditions, confidence calibration, and permissible evidence scope. **Closure:** explicit non-identifiability reporting, competing hypotheses and independent evidence protocol. **Negative test:** a shared transaction pattern cannot by itself establish real-world common control. **Links:** CASE-004, OCSRE-009; OCSH-004/006.

### 5.7 Evidence, privacy, and relay

**URL-027 — Weak evidence dependence and calibration.** Correlated clues can be double-counted as independent support. *Unresolved:* dependence-aware scoring and empirical calibration. **Closure:** synthetic correlated-evidence fixtures, calibration plots, and held-out challenge sets. **Negative test:** duplicated evidence must not increase confidence as if independent. **Links:** CASE-004, OCSRE-009; OCSH-004.

**URL-028 — Evidence access and privacy.** Cross-domain identity or code analysis may combine sensitive data across authority boundaries. *Unresolved:* purpose limitation, retention, consent/authorization, and redaction proofs. **Closure:** reviewed threat model and access policy with auditability and negative tests. **Negative test:** relay must not widen evidence access without explicit authorization. **Links:** CASE-004/006, SPEC-006; OCSH-004/011.

**URL-029 — Relay semantic equivalence limits.** Structural resemblance is not enough to transfer domain meaning. *Unresolved:* target-domain contract checks and negative-transfer detection. **Closure:** target conformance suite, compatibility matrix, explicit rejected transfers. **Negative test:** bus capacity constraints cannot be reused as inventory constraints without adaptation. **Links:** CASE-005, EXT-003, SPEC-004; OCSH-003/008.

**URL-030 — Independent multi-agent validation.** Agents may share training data, assumptions, prompts or tools, creating correlated errors. *Unresolved:* operational independence and adjudication. **Closure:** blinded review protocol, provenance separation, disagreement records and error analysis. **Negative test:** unanimous agent agreement must not substitute for external oracle or formal check. **Links:** EXT-003, SSICR, UIERU; OCSH-008.

**URL-031 — Relay cost and negative transfer.** Added orchestration can consume more resources than the transferred capability saves. *Unresolved:* resource-normalized utility and rollback. **Closure:** equal-budget baselines, end-to-end cost accounting, failed-relay ledger. **Negative test:** a transfer that worsens cost-adjusted target outcomes cannot be labeled beneficial. **Links:** CASE-005, EXT-005; OCSH-003/008.

### 5.8 Open-ended evolution and structural scaling

**URL-032 — Metric/Plugin/Policy co-evolution safety.** Systems that generate evaluation metrics and policies risk self-scoring and self-authorization. *Unresolved:* separation of duties, immutable constraints, and external governance. **Closure:** authority lattice, adversarial policy-change tests and independently controlled promotion. **Negative test:** a policy proposal cannot grant itself approval rights. **Links:** EXT-004, SPEC-006, ADR-OCSRE-021/022; OCSH-009/010.

**URL-033 — Untargeted-task evaluation protocol.** Apparent spillover may reflect task contamination or retrospective task selection. *Unresolved:* frozen capabilities, preregistered unseen tasks and independent evaluators. **Closure:** prospective held-out suite and negative controls with resource accounting. **Negative test:** a task chosen after inspecting gains cannot count as prospective untargeted evidence. **Links:** EXT-005, ISGFTR, OCSH-009.

**URL-034 — Resource-normalized longitudinal scaling.** More artifacts and agents may yield diminishing returns. *Unresolved:* growth curves, sample efficiency, cost, reproducibility, and extrapolation limits. **Closure:** repeated time-series studies, explicit model comparisons, confidence intervals and failed periods. **Negative test:** artifact count alone cannot be the scaling outcome. **Links:** EXT-005, OCSRE-012; OCSH-010.

**URL-035 — Novelty and capability-count inflation.** Renamed Plugins, redundant metrics, and correlated tasks can inflate apparent growth. *Unresolved:* novelty tests, dependency-aware counting, and deduplication. **Closure:** blinded capability novelty rubric, equivalence checks, and independent review. **Negative test:** semantically duplicate capabilities do not count as independent discoveries. **Links:** EXT-004/005, AQSI; OCSH-010.

### 5.9 AI-generated code governance

**URL-036 — Calling Graph blind spots.** Reflection, dynamic dispatch, configuration, data flow, and permission semantics can change without changing call edges. *Unresolved:* soundness limits and fallback analysis. **Closure:** adversarial programs with unchanged call graphs but changed security behavior; measured detection coverage. **Negative test:** tenant-scoped authorization cache changes must be flagged despite unchanged calls. **Links:** CASE-006, OCSRE-011, ADR-OCSRE-026; OCSH-011.

**URL-037 — Multi-graph impact soundness.** Combining calling, control, data, schema, policy and deployment graphs creates uncertain completeness and high false-positive rates. *Unresolved:* graph provenance, dynamic dependencies, coverage guarantees and evaluation costs. **Closure:** frozen benchmark with known impacts, precision/recall, missed critical cases and cost. **Negative test:** a changed configuration dependency cannot be omitted merely because it is absent from static calls. **Links:** CASE-006, SPEC-006; OCSH-011.

**URL-038 — AI code change authorization chain.** Passing tests does not authorize merge or deployment; sandbox outcomes may not match production. *Unresolved:* approval signatures, separation of duties, environment parity and rollback. **Closure:** executable candidate-to-commit state machine, audited approvals and fail-closed deployment tests. **Negative test:** an agent cannot promote its own unapproved security-sensitive change. **Links:** CASE-006, EXT-004, SPEC-005/006; OCSH-011.

### 5.10 Cross-cutting reproducibility and governance

**URL-039 — Reproducible conformance harness.** Paper test counts and synthetic fixtures are not an executable test system. *Unresolved:* versioned schemas, deterministic runners, expected outputs and CI evidence. **Closure:** public or auditable reference harness covering SPEC-001–006, CASE-001–006, negative fixtures, environment manifests and archived results. **Negative test:** a deliberately invalid fixture must fail the correct contract check. **Links:** all SPECs/CASEs; OCSH-001–011.

**URL-040 — Independent review and evidence governance.** Internal consistency and self-evaluation cannot establish replication. *Unresolved:* reviewer independence, conflict resolution, immutable evidence storage, and evidence-state promotion. **Closure:** documented review protocol with independent reruns, preserved dissent, linked revisions and reproducibility audit. **Negative test:** no OCSH status advances from E0 on manuscript completion or agent consensus alone. **Links:** HYPOTHESIS-REGISTRY, DECISION-LOG, COUNTEREXAMPLE-REGISTRY; OCSH-001–011.

## 6. Dependency graph and critical-path research sequence

The following sequence is a **proposed ordering**, not a completed schedule:

1. **Semantic safety foundation:** URL-001–009, URL-011–016, URL-019/020/022, URL-027/028, URL-032, URL-036–038. Freeze definitions, authority, time, granularity and negative oracles before comparing utility.
2. **Reference conformance infrastructure:** URL-039 and URL-040. Implement independently reviewable fixtures and evidence capture; publish failures as well as passes.
3. **Bounded demonstrators:** URL-006 (logic), URL-010 (ODK), URL-013–016 (SQL), URL-019–025 (CDE and school bus), URL-026–028 (transaction hypotheses), URL-036–038 (code governance).
4. **Transfer experiments:** URL-011/012 and URL-023/024 and URL-029–031; freeze core binaries and target-domain semantics before relay trials.
5. **Open-ended and longitudinal studies:** URL-017/018, URL-032–035. Start prospective untargeted tests only after baseline, leakage, and version controls exist.

A P0 residual need not block all conceptual publication; it blocks any **stronger claim** whose validity or safety depends on its closure. If a dependency cannot be resolved, explicitly narrow the claim and record that decision.

## 7. Proposed work packages and measurable deliverables

| Package | Residual IDs | Deliverable | Minimum acceptance evidence |
|---|---|---|---|
| WP-01 Identity and semantics | 001–009 | Versioned object/proof/metric contracts | Positive and adversarial fixtures; formal fragment where claimed |
| WP-02 SQL adapter | 013–016 | SQL-to-WE reference adapter | NULL, join, grain, snapshot, authorization checks |
| WP-03 ODK and Plugin | 010–012 | Frozen kernel and Plugin compatibility harness | Multi-domain conformance and negative-transfer reports |
| WP-04 CDE and SIF | 019–025 | Composite-state demonstrator and localization adapters | Invariant, rollback, termination and realism tests |
| WP-05 Evidence and identity | 026–028 | Defeasible hypothesis analysis protocol | Non-identifiability, dependence, privacy negative tests |
| WP-06 Relay and agents | 029–031 | Independent relay trial ledger | Equal-budget comparisons and failed transfers |
| WP-07 Evolution and scaling | 017–018, 032–035 | Prospective longitudinal protocol | Frozen tasks, leakage controls, uncertainty and cost |
| WP-08 Code governance | 036–038 | Multi-graph code-change governance prototype | Security-sensitive impact detection and authorization gates |
| WP-09 Research infrastructure | 039–040 | Evidence registry and independent review pipeline | Immutable results, reviewers, versioned OCSH status updates |

**Not scheduled:** owners, dates, budgets, hardware, datasets, and reviewers are `TBD`. No deployment or benchmark promise is implied.

## 8. Crosswalk to the eleven core hypotheses

| Hypothesis | Critical residuals | Necessary disconfirming direction |
|---|---|---|
| OCSH-001 | 004,006,007,039 | Restricted-fragment proof or countermodel fails |
| OCSH-002 | 008–010,039 | Domain transfer requires hidden core modifications |
| OCSH-003 | 011,012,029,031 | Contract approach does not reduce adaptation cost |
| OCSH-004 | 007,017,018,026–028 | Feedback harms traceability or misattributes evidence |
| OCSH-005 | 019–023,025 | Typed CDE fails required invariants or feasible search |
| OCSH-006 | 001–005,007–009,024,026 | Invalid cross-granularity or identity inference passes |
| OCSH-007 | 001,005,009,013–016 | SQL semantics or authorization change silently |
| OCSH-008 | 011,012,023,024,029–031 | Relay fails target conformance or costs exceed benefit |
| OCSH-009 | 017,029,031–033 | No prospective benefit on untargeted tasks |
| OCSH-010 | 032–035,039,040 | Growth not sustained or explained by added resources |
| OCSH-011 | 022,028,036–040 | Critical impact missed or authorization bypassed |

A residual can affect several hypotheses. This crosswalk identifies research dependencies, not evidence of truth or falsity.

## 9. Crosswalk to the 34 counterexamples and 30 decisions

The current registry includes **34 proposed `CEX` records** and **30 baseline `ADR-OCSRE` decisions**. Their precise fixture-level mappings require review before a conformance claim is made. The following are **thematic links only**:

| Residual cluster | Related CEX themes | Related ADR themes |
|---|---|---|
| Identity / logic (001–007) | CEX-001–009 | ADR-OCSRE-001–004, 011 |
| Metrics / Plugins (008–012) | Metric and Relay categories | ADR-OCSRE-005–007, 018–019 |
| SQL (013–016) | SQL category | ADR-OCSRE-008–009 |
| CDE (019–025) | CDE category | ADR-OCSRE-012–016 |
| Transaction / evidence (026–028) | Identity and Evidence categories | ADR-OCSRE-011, 017 |
| Multi-agent / Relay (029–031) | Relay category | ADR-OCSRE-018–020 |
| Growth (032–035) | Growth category | ADR-OCSRE-021–025 |
| Code (036–038) | Code category | ADR-OCSRE-026–027 |
| Evidence governance (039–040) | All categories | ADR-OCSRE-028–030 |

**No implied equivalence:** a `CEX` may be a proposed guardrail fixture while a `URL` is an open proof or experimental gap. Close and cross-link only after reviewing the actual test oracle and evidence.

## 10. Candidate resolution protocol

For each residual, create a separate evidence packet with:

```yaml
residual_id: URL-XXX
status_before: O
owner: TBD
reviewer: TBD
claim_scope: TBD
contract_versions: []
fixture_or_dataset_versions: []
baseline_and_budget: TBD
expected_oracle: TBD
negative_tests: []
observed_results: TBD
evidence_artifact_uri_or_hash: TBD
limitations: []
linked_CEX: []
linked_ADR: []
linked_OCSH: []
proposed_status_after: TBD
review_date: TBD
```

Workflow: (1) specify the gap; (2) freeze claim, protocol and oracle; (3) construct negative controls; (4) run in a recorded environment; (5) independently reproduce or review; (6) decide whether the evidence supports, narrows, refutes, or leaves the claim open; (7) update affected SPEC, ADR, CEX and OCSH records with explicit version links; (8) retain the old residual and evidence history. A partial fix may yield `Q — Qualified closure`, not `C — Closed`.

**Forbidden shortcuts:** marking resolved because an example is intuitive; using synthetic expected outputs as observed results; upgrading E0 because a paper was released; deleting a counterexample after fixing a bug; changing an oracle after seeing test outcomes without a logged protocol revision; allowing an AI agent to authorize its own policy changes.

## 11. Negative evidence and stopping rules

A productive research backlog must support *stopping*, not only expansion. Suspend or narrow an experiment if it repeatedly fails predeclared safety invariants, leaks evaluation information, lacks independent verification, or consumes resources without a credible marginal benefit. Publish failed and inconclusive trials with the same provenance discipline as positive results. When an apparently universal claim fails in a bounded case, prefer a **qualified narrower claim** over an unsupported universal statement.

Suggested stopping questions:

- Did the new Plugin improve target outcomes beyond an equal-budget non-Plugin baseline?
- Does the result persist when object identity, perspective, time and granularity are adversarially perturbed?
- Does CDE find a feasible composite state without violating authorization or loop constraints?
- Are apparently independent Agent judgments actually correlated?
- Does the claimed untargeted spillover survive prospective, frozen-task evaluation?
- Are added capability counts truly novel, and are net benefits positive after verification costs?

If the answer is unknown, record `unknown`, not `pass`.

## 12. Relay of unresolved problems into Collective Structural Learning

The registry is a candidate input for AQSI autonomous questioning, CDE candidate-state exploration, SIF problem/capability localization, UIERU Relay and SSICR competitive strategy generation. A useful *residual relay artifact* includes: exact question, typed objects, scope and authority, known counterexamples, candidate methods, target evidence, constraints, evaluation budget, unresolved uncertainty, and receiving-agent obligations. Transfer does not confer new permissions or change the residual's evidence status.

Example proposed relay:

```text
URL-021 (CDE loop termination)
  -> AQSI: generate bounded termination questions
  -> SIF: localize proof obligations and candidate methods
  -> CDE: explore path-memory designs in sandbox
  -> Independent checker: attempt counterexample construction
  -> Research trace: retain failed paths and explicit leftovers
```

This is an **illustrative workflow**, not a claim that any component has been executed.

## 13. Versioning, amendments, and audit trail

- IDs are immutable; never reuse `URL-###` for a different question.
- If a residual splits, add new IDs and record `split_from`; if several combine, preserve old IDs with `merged_into` links.
- Record scope changes and status transitions with a date, owner, reviewer, and evidence URI/hash. Unknown metadata remains `TBD`.
- Keep local paper leftovers in place; link to this registry instead of deleting their history.
- Any change to a normative interface requires the applicable SPEC revision; any OCSH state change requires a hypothesis-registry update.
- A failed test should produce or update a CEX record and, when design rationale changes, an ADR amendment.

### Initial audit entry

| Version | Action | Evidence status | Owner / reviewer |
|---|---|---|---|
| v1.0.0 research baseline | Establish `URL-001`–`URL-040` as open research residuals | No executed evidence claimed | Proposed authors; reviewer TBD |

## 14. Explicit leftovers of this registry itself

These `URR` items concern the *quality and operation of the registry* and must not be mistaken for completed resolutions of `URL` records.

| ID | Registry-level leftover |
|---|---|
| URR-001 | Verify one-to-one or many-to-many mapping against every local paper leftover |
| URR-002 | Confirm exact normative clauses in SPEC-001–006 for each URL |
| URR-003 | Establish stable machine-readable residual schema |
| URR-004 | Define mandatory evidence hashing and artifact retention |
| URR-005 | Name accountable owners and independent reviewers |
| URR-006 | Define version and date conventions across all registries |
| URR-007 | Automate broken-link and stale-reference checks |
| URR-008 | Publish controlled vocabularies for status, priority and domain |
| URR-009 | Resolve possible overlap among identity and evidence residuals |
| URR-010 | Formalize the threshold for qualified versus full closure |
| URR-011 | Require negative controls in every closure protocol |
| URR-012 | Define safe public disclosure of security-sensitive failures |
| URR-013 | Define privacy-preserving synthetic benchmark generation |
| URR-014 | Add cost and compute accounting templates |
| URR-015 | Pre-register prospective untargeted-task suites |
| URR-016 | Establish independent replication criteria by hypothesis type |
| URR-017 | Define adjudication for contradictory reviewers |
| URR-018 | Track residual dependencies in a machine-readable DAG |
| URR-019 | Specify how blocked dependencies affect downstream claims |
| URR-020 | Add regression test links for closed residuals |
| URR-021 | Document evidence decay and revalidation triggers |
| URR-022 | Record external-framework compatibility and version constraints |
| URR-023 | Design AQSI/UIERU relay packet interoperability tests |
| URR-024 | Periodically audit whether new research questions are genuinely novel |

All `URR-001`–`URR-024` are **open** at publication of this proposed v1.0.0 baseline.

## 15. Closing position

OCSRE proposes an object-centric route from representation and computation to reasoning, in-situ learning, constrained state evolution, and structural capability relay. Its most important unresolved work is not to produce more confident prose; it is to establish **typed semantic contracts, adversarial conformance, independent evidence, bounded demonstrations, and prospective tests of transfer and growth**. An explicit residual is a legitimate research result: it identifies the boundary of present knowledge and gives future contributors a testable next step.

**Current conclusion:** forty cross-cutting residuals are open; twenty-four registry-maintenance leftovers are open; eleven core hypotheses remain E0. No theorem, benchmark gain, deployment assurance, untargeted spillover, or scaling law is claimed validated by this registry.
