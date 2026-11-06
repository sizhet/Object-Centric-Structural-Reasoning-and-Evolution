# COUNTEREXAMPLE-REGISTRY — OCSRE Research Trace

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Version:** v1.0.0 — Research Framework and Contracts  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**Status:** Proposed adversarial and falsification registry; examples are synthetic, not executed findings  
**License:** Apache-2.0  
**Canonical location:** `research-trace/COUNTEREXAMPLE-REGISTRY.md`

## 1. Purpose and epistemic limits

This registry preserves counterexamples, near-misses, failure mechanisms, and disconfirming test designs for the OCSRE research program. It is a **challenge ledger**, not a catalog of observed production failures. Unless a record includes a verified evidence artifact, its scenario is a *synthetic, proposed test*. No counterexample below is claimed to have been executed, and no OCSH hypothesis is claimed confirmed or refuted. All eleven OCSH hypotheses remain **E0 — Proposed** under `HYPOTHESIS-REGISTRY.md`.

A counterexample to a **contract** shows a prohibited input, transition, or inference; a counterexample to a **hypothesis** requires a valid experimental setting and a disconfirming result. These are not interchangeable. A known bad behavior rejected by a system is positive evidence of conformance to a guardrail, not evidence that the research hypothesis is false.

## 2. Authority, conventions, and record lifecycle

- `SPEC-001`–`SPEC-006` govern their respective proposed normative interfaces; this registry cannot silently modify them. `DEFINITION-REGISTRY.md` provides term boundaries, and `HYPOTHESIS-REGISTRY.md` owns OCSH claims and evidence states.
- **IDs:** `CEX-001` onward are immutable registry identifiers. Case-local NEG IDs are not renumbered or equated with CEX IDs; they may be cross-referenced only after explicit fixture matching.
- **Statuses:** `P — Proposed`, `S — Specified fixture`, `R — Reproduced failure`, `G — Guardrail verified`, `X — Disconfirming evidence reviewed`, `C — Closed with documented scope`, `H — On hold`. Initial status for every entry here is `P`.
- **Severity:** illustrative risk priority (`Critical`, `High`, `Medium`) is not an observed incident rating or measured probability.
- **Evidence:** `none` until a reproducible test artifact, environment, timestamp, version, expected/observed output, and independent review are attached.
- **Lifecycle:** propose → specify fixture → freeze oracle → execute → independently review → decide impact → revise contract/hypothesis if warranted → retest regression → retain historical record.

### 2.1 Mandatory evidence packet

For promotion beyond `P`, record `fixture_id`, `dataset_or_program_version`, `contract_version`, `runner_environment`, `input`, `expected_result`, `observed_result`, `evidence_uri/hash`, `reproduction_steps`, `reviewer`, `date`, `hypothesis_impact`, `decision_id`, and `residual_ids`. Missing fields remain `TBD`; never invent test outcomes.

### 2.2 Threat model and boundaries

Threats include accidental modeling errors, stale or correlated evidence, adversarial inputs, unauthorized policy changes, misleading optimization, data leakage, and evaluation leakage. The examples are designed to expose invalid inference or governance gaps; they do not prescribe deanonymization or unauthorized surveillance. Transaction identities remain defeasible hypotheses, and privacy/security controls are first-class invariants.

## 3. Master counterexample index

| ID | Domain | Failure pattern | Linked OCSH | Status |
|---|---|---|---|---|
| CEX-001 | Identity | SQL row treated as a WE identity | OCSH-007 | P |
| CEX-002 | Identity | Display label used as identity | OCSH-006 | P |
| CEX-003 | Identity | Wallet address equated with real-world controller | OCSH-004 | P |
| CEX-004 | Identity | Composite actor merge without reversible provenance | OCSH-005 | P |
| CEX-005 | Reasoning | Invalid syllogism accepted as proof | OCSH-001 | P |
| CEX-006 | Reasoning | Deductive validity confused with factual truth | OCSH-001 | P |
| CEX-007 | Reasoning | Group property inherited by every member | OCSH-006 | P |
| CEX-008 | Reasoning | Individual property generalized to group | OCSH-006 | P |
| CEX-009 | Reasoning | Temporal state silently reused | OCSH-006 | P |
| CEX-010 | Metric | Unit mismatch produces a plausible differential | OCSH-002 | P |
| CEX-011 | Metric | Perspective mismatch masked by same metric name | OCSH-002 | P |
| CEX-012 | Metric | Missing observation interpreted as zero | OCSH-002 | P |
| CEX-013 | Metric | Score improvement treated as authorization | OCSH-005 | P |
| CEX-014 | SQL | NULL comparison converted to false | OCSH-007 | P |
| CEX-015 | SQL | Join multiplicity silently collapsed | OCSH-007 | P |
| CEX-016 | SQL | Aggregation grain changes denominator | OCSH-007 | P |
| CEX-017 | SQL | Snapshot mixing yields impossible state | OCSH-007 | P |
| CEX-018 | SQL | Row-level security bypassed during plugin relay | OCSH-007 | P |
| CEX-019 | CDE | Local feasibility mistaken for global feasibility | OCSH-005 | P |
| CEX-020 | CDE | Repeated delta creates search loop | OCSH-005 | P |
| CEX-021 | CDE | NoSubtree prunes a feasible branch | OCSH-005 | P |
| CEX-022 | CDE | Candidate state overwrites committed state | OCSH-005 | P |
| CEX-023 | Evidence | Correlated weak evidence double counted | OCSH-004 | P |
| CEX-024 | Evidence | Absence of observation interpreted as negative evidence | OCSH-004 | P |
| CEX-025 | Evidence | Hypothesis promoted to verified identity | OCSH-004 | P |
| CEX-026 | Relay | Plugin interface compatibility mistaken for semantic compatibility | OCSH-008 | P |
| CEX-027 | Relay | Success-only transfer accounting | OCSH-008 | P |
| CEX-028 | Relay | Agent consensus mistaken for independent validation | OCSH-008 | P |
| CEX-029 | Growth | Post-hoc task selection creates spillover illusion | OCSH-009 | P |
| CEX-030 | Growth | Artifact count presented as scaling law | OCSH-010 | P |
| CEX-031 | Policy | Self-modifying policy self-authorizes | OCSH-010 | P |
| CEX-032 | Code | Unchanged call graph masks semantic regression | OCSH-011 | P |
| CEX-033 | Code | Missing dynamic edge creates false safe impact boundary | OCSH-011 | P |
| CEX-034 | Code | Passing tests treated as deployment approval | OCSH-011 | P |

## 4. Detailed counterexample cards

Every card states a *proposed* minimal scenario, the prohibited failure, the expected guardrail or oracle, and traceability. A test must exercise the actual relevant contract, not merely recognize the scenario in prose.

### CEX-001 — SQL row treated as a WE identity

**Domain:** Identity  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** Two snapshots reuse a row identifier after a migration.  
**Failure to provoke:** An adapter binds both records to one stable actor.  
**Expected rejection / safe behavior:** Distinct identity lineage or explicit continuity proof is required.  
**Research linkage:** SPEC-001; CASE-002; OCSH-007; DEF-001–009.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-002 — Display label used as identity

**Domain:** Identity  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** Two students share a display name.  
**Failure to provoke:** Their observations and authorizations are merged.  
**Expected rejection / safe behavior:** ObjectRef and identity authority, not labels, determine sameness.  
**Research linkage:** SPEC-001; CASE-001; OCSH-006; DEF-003–009.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-003 — Wallet address equated with real-world controller

**Domain:** Identity  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** A custodial service aggregates deposits.  
**Failure to provoke:** A transaction cluster is promoted to a verified person.  
**Expected rejection / safe behavior:** Keep address, account, actor and composite-actor hypothesis distinct.  
**Research linkage:** CASE-004; SPEC-005; OCSH-004; DEF-001–009.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-004 — Composite actor merge without reversible provenance

**Domain:** Identity  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** Two weakly related wallets share timing patterns.  
**Failure to provoke:** A merge destroys the separate hypotheses.  
**Expected rejection / safe behavior:** Candidate merge must preserve source objects and split/rollback trace.  
**Research linkage:** CASE-004; SPEC-006; OCSH-005; DEF-037–045.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-005 — Invalid syllogism accepted as proof

**Domain:** Reasoning  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** All humans are mortal; Socrates is mortal.  
**Failure to provoke:** The system concludes Socrates is human.  
**Expected rejection / safe behavior:** Reject affirming the consequent; require valid derivation.  
**Research linkage:** SPEC-003; CASE-001; OCSH-001; DEF-028–036.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-006 — Deductive validity confused with factual truth

**Domain:** Reasoning  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** A well-formed proof uses an unverified premise.  
**Failure to provoke:** A valid conclusion is marked empirically confirmed.  
**Expected rejection / safe behavior:** Preserve proof validity and premise-evidence status separately.  
**Research linkage:** SPEC-003; EXT-001; OCSH-001; DEF-028–036.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-007 — Group property inherited by every member

**Domain:** Reasoning  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** Average route delay exceeds threshold.  
**Failure to provoke:** Every student is declared late.  
**Expected rejection / safe behavior:** Use declared aggregation and granularity contract.  
**Research linkage:** SPEC-003; CASE-003; OCSH-006; DEF-010–016.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-008 — Individual property generalized to group

**Domain:** Reasoning  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** One transaction is suspicious.  
**Failure to provoke:** Every wallet in a cluster is labeled suspicious.  
**Expected rejection / safe behavior:** Require quantifier, scope, and evidence-specific group inference.  
**Research linkage:** CASE-004; SPEC-003; OCSH-006; DEF-010–016.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-009 — Temporal state silently reused

**Domain:** Reasoning  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** A bus had capacity 40 last term.  
**Failure to provoke:** Current dispatch uses historical capacity as current fact.  
**Expected rejection / safe behavior:** Require effective-time and version alignment.  
**Research linkage:** SPEC-001; CASE-003; OCSH-006; DEF-010–016.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-010 — Unit mismatch produces a plausible differential

**Domain:** Metric  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** A load ratio of 0.8 is compared with 80 passengers.  
**Failure to provoke:** ODK returns a scalar difference.  
**Expected rejection / safe behavior:** Reject incompatible dimensions before comparison.  
**Research linkage:** SPEC-002; CASE-002; OCSH-002; DEF-017–027.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-011 — Perspective mismatch masked by same metric name

**Domain:** Metric  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** Passenger comfort and fleet efficiency both use score.  
**Failure to provoke:** Scores are ranked as commensurate.  
**Expected rejection / safe behavior:** Bind metric semantics and perspective in the comparator contract.  
**Research linkage:** SPEC-002; OCSRE-004; OCSH-002; DEF-010–027.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-012 — Missing observation interpreted as zero

**Domain:** Metric  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** A sensor has no reading.  
**Failure to provoke:** A plugin reports zero occupancy.  
**Expected rejection / safe behavior:** Preserve missingness and uncertainty; do not silently impute.  
**Research linkage:** SPEC-002; CASE-002; OCSH-002; DEF-017–027.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-013 — Score improvement treated as authorization

**Domain:** Metric  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** A new route improves a composite objective.  
**Failure to provoke:** The route is committed without safety review.  
**Expected rejection / safe behavior:** Separate candidate score, invariant conformance and approval.  
**Research linkage:** SPEC-006; CASE-003; OCSH-005; DEF-037–045.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-014 — NULL comparison converted to false

**Domain:** SQL  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** WHERE x = NULL is translated as x == null.  
**Failure to provoke:** Unknown SQL truth becomes ordinary false or true.  
**Expected rejection / safe behavior:** Preserve SQL three-valued logic under supported dialect.  
**Research linkage:** CASE-002; OCSRE-006; OCSH-007; DEF-017–027.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-015 — Join multiplicity silently collapsed

**Domain:** SQL  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** A student has two attendance records.  
**Failure to provoke:** A join is deduplicated and totals change.  
**Expected rejection / safe behavior:** Preserve bag semantics or document a contracted aggregation.  
**Research linkage:** CASE-002; SPEC-004; OCSH-007; DEF-017–027.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-016 — Aggregation grain changes denominator

**Domain:** SQL  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** A route average is computed from trip-level averages.  
**Failure to provoke:** Unequal trip sizes yield biased passenger average.  
**Expected rejection / safe behavior:** Require explicit weighting, grain and denominator.  
**Research linkage:** CASE-002; SPEC-001; OCSH-007; DEF-010–027.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-017 — Snapshot mixing yields impossible state

**Domain:** SQL  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** Assignments are read before a transaction and capacities after.  
**Failure to provoke:** The composite view was never true at one snapshot.  
**Expected rejection / safe behavior:** Use compatible snapshot/isolation semantics or flag inconsistency.  
**Research linkage:** CASE-002; SPEC-001; OCSH-007; DEF-010–016.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-018 — Row-level security bypassed during plugin relay

**Domain:** SQL  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** A cross-tenant adapter caches rows before policy filtering.  
**Failure to provoke:** A downstream plugin receives forbidden records.  
**Expected rejection / safe behavior:** Authorization must be enforced before and throughout relay.  
**Research linkage:** CASE-002; SPEC-004/005; OCSH-007; DEF-017–027.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-019 — Local feasibility mistaken for global feasibility

**Domain:** CDE  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** A trip reassign fits bus capacity.  
**Failure to provoke:** Driver hours or transfer times are violated.  
**Expected rejection / safe behavior:** Validate composite invariants on the full candidate state.  
**Research linkage:** CASE-003; SPEC-006; OCSH-005; DEF-037–045.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-020 — Repeated delta creates search loop

**Domain:** CDE  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** Two route swaps undo each other indefinitely.  
**Failure to provoke:** Search revisits identical state without progress.  
**Expected rejection / safe behavior:** Track path-specific delta use and state signatures; bound loops.  
**Research linkage:** OCSRE-008; SPEC-006; OCSH-005; DEF-037–045.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-021 — NoSubtree prunes a feasible branch

**Domain:** CDE  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** A heuristic rejects a partial route because of a stale bound.  
**Failure to provoke:** A valid solution is never considered.  
**Expected rejection / safe behavior:** Distinguish proved infeasibility from heuristic pruning and log scope.  
**Research linkage:** SPEC-006; CASE-003; OCSH-005; DEF-037–045.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-022 — Candidate state overwrites committed state

**Domain:** CDE  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** An agent tests a fleet merge.  
**Failure to provoke:** A failed proposal mutates the production schedule.  
**Expected rejection / safe behavior:** Isolate sandbox candidate from committed state; require rollback.  
**Research linkage:** SPEC-006; CASE-003; OCSH-005; DEF-037–045.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-023 — Correlated weak evidence double counted

**Domain:** Evidence  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** Two feeds repeat the same source claim.  
**Failure to provoke:** A composite-actor confidence score treats them as independent.  
**Expected rejection / safe behavior:** Track source lineage and dependence; test sensitivity.  
**Research linkage:** CASE-004; SPEC-005; OCSH-004; DEF-028–036.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-024 — Absence of observation interpreted as negative evidence

**Domain:** Evidence  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** A transaction lacks an IP field.  
**Failure to provoke:** The system infers a distinct operator.  
**Expected rejection / safe behavior:** Differentiate missing, inaccessible, and observed negative evidence.  
**Research linkage:** CASE-004; SPEC-005; OCSH-004; DEF-028–036.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-025 — Hypothesis promoted to verified identity

**Domain:** Evidence  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** Several weak directional features align.  
**Failure to provoke:** A real-world actor is declared identified.  
**Expected rejection / safe behavior:** Maintain hypothesis status and independent corroboration requirement.  
**Research linkage:** CASE-004; OCSRE-009; OCSH-004; DEF-028–036.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-026 — Plugin interface compatibility mistaken for semantic compatibility

**Domain:** Relay  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** Both domains expose utilization_ratio.  
**Failure to provoke:** A fleet occupancy plugin is applied to stock turnover.  
**Expected rejection / safe behavior:** Check denominators, units, time basis, and target contract.  
**Research linkage:** CASE-005; SPEC-004; OCSH-008; DEF-017–027.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-027 — Success-only transfer accounting

**Domain:** Relay  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** Five transfers fail and one succeeds.  
**Failure to provoke:** Report claims universal transfer from the one success.  
**Expected rejection / safe behavior:** Log all trials, failures, adaptation cost and negative transfer.  
**Research linkage:** CASE-005; EXT-005; OCSH-008; DEF-052–061.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-028 — Agent consensus mistaken for independent validation

**Domain:** Relay  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** Three agents share the same corrupted evidence feed.  
**Failure to provoke:** Their agreement is counted as three confirmations.  
**Expected rejection / safe behavior:** Assess independence and source overlap; require external checks.  
**Research linkage:** EXT-003; SPEC-005; OCSH-008; DEF-051–055.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-029 — Post-hoc task selection creates spillover illusion

**Domain:** Growth  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** A task is selected after observing a successful plugin.  
**Failure to provoke:** It is called an untargeted gain.  
**Expected rejection / safe behavior:** Freeze held-out tasks before exposure and record selection protocol.  
**Research linkage:** EXT-005; HYPOTHESIS-REGISTRY; OCSH-009; DEF-059–061.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-030 — Artifact count presented as scaling law

**Domain:** Growth  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** Registry grows from 10 to 100 plugins.  
**Failure to provoke:** The paper asserts intelligence scales by 10x.  
**Expected rejection / safe behavior:** Measure net validated utility, cost and longitudinal generalization.  
**Research linkage:** EXT-004/005; OCSRE-012; OCSH-010; DEF-056–061.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-031 — Self-modifying policy self-authorizes

**Domain:** Policy  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** An agent proposes a looser approval threshold.  
**Failure to provoke:** Its own new policy authorizes that change.  
**Expected rejection / safe behavior:** Separate proposal, evaluator and independent approval authority.  
**Research linkage:** EXT-004; SPEC-006; OCSH-010; DEF-045/058.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-032 — Unchanged call graph masks semantic regression

**Domain:** Code  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** A cache key omits tenant_id after AI refactor.  
**Failure to provoke:** Call edges stay constant while authorization leaks.  
**Expected rejection / safe behavior:** Check data/control/security semantics and adversarial tests.  
**Research linkage:** CASE-006; EXT-002; OCSH-011; DEF-062–065.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-033 — Missing dynamic edge creates false safe impact boundary

**Domain:** Code  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** Reflection invokes a handler absent from static call graph.  
**Failure to provoke:** Affected tests are skipped.  
**Expected rejection / safe behavior:** Record unresolved dynamic dependencies and use conservative fallback.  
**Research linkage:** CASE-006; OCSRE-010; OCSH-011; DEF-062–065.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

### CEX-034 — Passing tests treated as deployment approval

**Domain:** Code  
**Status:** P — Proposed; no execution evidence  
**Minimal synthetic fixture:** Unit tests pass but a privacy review is pending.  
**Failure to provoke:** Agent deploys the change.  
**Expected rejection / safe behavior:** Test evidence and governance authorization are separate.  
**Research linkage:** CASE-006; SPEC-005/006; OCSH-011; DEF-045/065.  
**Test design:** Construct a baseline with the problematic condition and a paired control without it. Assert a typed rejection, abstention, preserved distinction, or explicit non-authorization as appropriate. Log the object/perspective/state versions and the exact boundary that failed or held. If the implementation accepts the unsafe behavior, capture a minimized reproducer and assess whether this is a contract nonconformance or a hypothesis-level disconfirmation.  
**Evidence / owner / reviewer:** none / TBD / TBD.

## 5. Cross-hypothesis falsification matrix

| Hypothesis | Critical counterexample IDs | Experimental disconfirmation target |
|---|---|---|
| OCSH-001 | CEX-005, CEX-006 | Unsound entailment or failed preservation in declared fragment |
| OCSH-002 | CEX-010, CEX-011, CEX-012 | Unchanged ODK fails typed comparison or requires domain-specific core edits |
| OCSH-003 | Cross-cutting | Contracted plugins incur no net advantage or unacceptable defects |
| OCSH-004 | CEX-003, CEX-023, CEX-024, CEX-025 | Feedback/provenance workflow causes unjustified promotion or fails traceability |
| OCSH-005 | CEX-004, CEX-013, CEX-019, CEX-020, CEX-021, CEX-022 | Validated composite transition violates declared invariants |
| OCSH-006 | CEX-002, CEX-007, CEX-008, CEX-009 | Explicit granularity contracts do not reduce invalid inheritance |
| OCSH-007 | CEX-001, CEX-014, CEX-015, CEX-016, CEX-017, CEX-018 | SQL semantics or security not preserved for supported inputs |
| OCSH-008 | CEX-026, CEX-027, CEX-028 | Relay produces no validated transfer or hidden negative transfer |
| OCSH-009 | CEX-029 | Untargeted gains disappear under preregistered holdouts |
| OCSH-010 | CEX-030, CEX-031 | Longitudinal net utility fails to grow under resource accounting |
| OCSH-011 | CEX-032, CEX-033, CEX-034 | Impact localization misses dependencies or fails traceability baseline |

**Interpretation rule:** The table proposes tests; it does not claim that any hypothesis has failed. Some negative tests are primarily conformance checks rather than decisive empirical falsifiers. A hypothesis status change requires the evidence standard of `HYPOTHESIS-REGISTRY.md`.

## 6. Cross-case adversarial suites

### Suite A — Classical proof and multi-granularity reasoning

Start with the valid Socrates entailment from CASE-001; then change one premise, invert implication, replace identity with a display label, or project a group aggregate onto an individual. The reference prover is the oracle for the declared classical fragment; identity, time, and granularity contracts are separate oracles. **Acceptance:** valid entailments remain valid; invalid entailments are rejected; no unsupported fact promotion.

### Suite B — SQL-to-WE adaptation

Use CASE-002 synthetic schema with NULL, duplicate join rows, unequal aggregation denominators, snapshot skew, and tenant policy restrictions. Compare native SQL outputs with adapted WE outputs under a frozen dialect and authorization context. **Acceptance:** semantic equivalence where declared, explicit unsupported behavior elsewhere, and no unauthorized disclosure.

### Suite C — Composite scheduling and CDE

Begin with CASE-003 fixed trip intervals. Introduce driver-hour constraints, travel-time buffers, stale capacity, repeated inverse deltas, and heuristic pruning. **Acceptance:** candidate isolation, global feasibility checks, bounded search, rollback, and approval separation. A two-bus synthetic candidate is not evidence of real-world fleet savings.

### Suite D — Transaction and compositional identity

Begin with CASE-004 synthetic transaction graph; vary custody assumptions, source independence, time ordering, and missing fields. **Acceptance:** evidence lineage and alternative hypotheses persist; no forced real-world identity assertion or unwarranted certainty.

### Suite E — Relay and capability growth

Freeze CASE-005 domain adapters and EXT-005 held-out task sets before evaluation. Include semantically misleading metric names, failed transfers, unreported adaptation costs, and post-hoc task selection. **Acceptance:** conformance before promotion; all trials retained; no spillover or scaling claim without measured resource-accounted results.

### Suite F — AI-generated code governance

Use CASE-006 tenant-aware cache refactor; preserve call edges while changing cache-key semantics. Add dynamic dispatch, configuration dependencies, and tests that pass without security approval. **Acceptance:** multi-graph impact flags uncertainty; security checks detect tenant boundary violations; no autonomous deployment.

## 7. Proposed execution protocol and reporting

1. **Preregister** the fixture, threat, oracle, baseline, metric, seed, and stopping criteria; do not tailor the oracle after observing results.
2. **Run paired controls:** safe/unsafe variants and OCSRE/baseline under comparable budgets. Record true positives, false positives, false negatives, latency, and adaptation overhead where relevant.
3. **Minimize failures:** reduce the counterexample while retaining the failing behavior, without stripping relevant security, temporal, or perspective conditions.
4. **Assign failure class:** parser/adapter defect, identity alias, type error, inference unsoundness, evidence conflation, state-transition violation, authorization breach, relay incompatibility, or evaluation confound.
5. **Independent review:** distinguish a test-harness defect from a real contract failure; do not let the candidate-generating agent be the sole verifier.
6. **Update linked assets:** definition, specification, hypothesis, case, decision log, and unresolved residuals as necessary; never erase the original record.
7. **Regression gate:** any fix must pass the original counterexample, paired valid case, and relevant cross-domain suite before being marked guarded.

## 8. Conformance obligations (proposed)

| ID | Obligation | Primary surface |
|---|---|
| CER-001 | Identity continuity is not inferred from row keys or display labels | SPEC-001 |
| CER-002 | Composite identity hypotheses remain defeasible and reversible | SPEC-001/006 |
| CER-003 | Classical entailment preserves soundness in the declared fragment | SPEC-003 |
| CER-004 | Logical validity is separated from premise truth | SPEC-003/005 |
| CER-005 | Cross-granularity inheritance requires an explicit rule | SPEC-003 |
| CER-006 | Temporal and perspective binding is versioned | SPEC-001 |
| CER-007 | ODK rejects incompatible units and metric semantics | SPEC-002 |
| CER-008 | Missing observations are not silently zeroed | SPEC-002/005 |
| CER-009 | Candidate score cannot grant authorization | SPEC-006 |
| CER-010 | SQL NULL and bag semantics are preserved where supported | SPEC-004; CASE-002 |
| CER-011 | SQL aggregation grain and snapshot semantics are explicit | CASE-002 |
| CER-012 | Row-level security survives transformation and relay | SPEC-004/005 |
| CER-013 | Composite CDE invariants are checked globally | SPEC-006 |
| CER-014 | Loop, delta reuse and pruning reasons are traceable | SPEC-006 |
| CER-015 | Sandbox candidates cannot mutate committed state | SPEC-006 |
| CER-016 | Weak evidence provenance and dependence are tracked | SPEC-005 |
| CER-017 | Identity hypotheses cannot become verified actors by score alone | SPEC-005 |
| CER-018 | Relay requires target-domain semantic conformance | SPEC-004/006 |
| CER-019 | Independent validators assess shared-source dependence | EXT-003 |
| CER-020 | Untargeted task evaluation is preregistered | EXT-005 |
| CER-021 | Scaling claims include net utility and resource costs | EXT-005 |
| CER-022 | Policy evolution cannot self-authorize | EXT-004 |
| CER-023 | Code impact analysis includes non-call dependencies | CASE-006 |
| CER-024 | Test success is not deployment permission | CASE-006 |

These are proposed registry obligations, not executed or certified tests. A violation may be a safety or semantic failure even if the measured optimization objective improves.

## 9. Explicit leftovers and unresolved questions

| ID | Unresolved research residual |
|---|---|
| CXR-001 | Canonical executable fixture schema for all six cases |
| CXR-002 | Machine-readable linkage between CEX IDs and case-local NEG IDs |
| CXR-003 | Formal identity-continuity proof obligations across migrations |
| CXR-004 | Reference semantics for composite identity hypotheses |
| CXR-005 | Complete proof-fragment grammar and trusted entailment oracle |
| CXR-006 | Cross-granularity aggregation/inheritance type system |
| CXR-007 | Temporal bitemporality and late-arriving evidence policy |
| CXR-008 | Metric dimension algebra and normalization semantics |
| CXR-009 | Unknown versus missing versus censored observation model |
| CXR-010 | SQL dialect coverage and NULL-equivalence boundaries |
| CXR-011 | Snapshot isolation and streaming-consistency contract |
| CXR-012 | Tenant and field-level authorization propagation |
| CXR-013 | CDE path-memory equivalence and termination proofs |
| CXR-014 | NoSubtree soundness versus heuristic pruning semantics |
| CXR-015 | Global constraint oracle for real school transport |
| CXR-016 | Independent evidence-dependence estimation |
| CXR-017 | Ethical and privacy review of transaction evidence |
| CXR-018 | Quantified plugin semantic compatibility criteria |
| CXR-019 | Cross-domain transfer adaptation-cost accounting |
| CXR-020 | Independent multi-agent validation and collusion resistance |
| CXR-021 | Preregistered untargeted task suite and contamination checks |
| CXR-022 | Longitudinal structural scaling measurement and stopping rules |
| CXR-023 | Safe governance of policy-changing policy proposals |
| CXR-024 | Dynamic code dependency coverage and false-negative bounds |

Open residuals should be copied or cross-linked to `UNRESOLVED-RESIDUALS.md` when that file is created. The absence of a test harness or an unresolved semantics boundary must remain visible, not be reclassified as success.

## 10. Change governance and interoperability

- **Add:** allocate the next CEX ID; specify a minimal fixture and disconfirmation path; cross-link a hypothesis and a governing contract.
- **Revise:** keep the original failure mechanism and history; version changed oracles; record rationale in `DECISION-LOG.md`.
- **Close:** require an evidence packet, regression tests, an independent reviewer, and explicit scope. Closed does not mean universally solved.
- **Promote to empirical disconfirmation:** only through the hypothesis evidence process; update `HYPOTHESIS-REGISTRY.md` with the exact experiment and qualification.
- **Retain negative transfer:** unsuccessful or harmful relay attempts are first-class collective learning assets, not discarded outliers.

## 11. Research positioning

A useful counterexample registry is not an admission that OCSRE is defective; it is a mechanism for making its claims precise and its failures observable. The research program advances only when identity, inference, evidence, metrics, state evolution, capability relay, and authorization remain distinguishable under adversarial conditions. **Specifications/Contracts First; Conformance Before Runtime; Explicit Leftover.**
