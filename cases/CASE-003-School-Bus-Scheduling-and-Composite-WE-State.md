# CASE-003 — School-Bus Scheduling and Composite WE State

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Artifact type:** Research case, synthetic reference fixture, and proposed conformance suite  
**Target release:** v1.0.0 — Research Framework and Contracts  
**Authors:** Sizhe Tan & GPT-Obot  
**License:** Apache-2.0  
**Status:** Research proposal / E0. Worked examples are synthetic and arithmetically specified; no solver implementation, deployment, or empirical improvement is claimed.

## Abstract

School-bus scheduling is a useful, bounded laboratory for object-centric structural reasoning and constrained state evolution. Its primary operational objective can be to reduce the number of vehicles required, subject to student coverage, vehicle capacity, time-window, travel-time, ride-duration, compatibility, and safety constraints. Unlike a single-object attribute edit, a scheduling change affects a composite state of students, stops, trips, routes, buses, drivers, times, and shared resources. This case defines a World Entity (WE)-native `StateContainer`, typed candidate Deltas, a reproducible miniature scheduling fixture, global feasibility checks, an Object Differential Kernel (ODK) evaluation envelope, and a proposed CDE search-and-feedback loop. It distinguishes a computationally feasible plan from an authorized operational plan, and a simulated outcome from observed service. The case is intended to probe OCSH-005, OCSH-006, and related reuse, learning, and relay hypotheses. It is a conformance design, not a report of measured results.

**Keywords:** school-bus scheduling; World Entity; composite state; CDE; typed Delta; constraint satisfaction; vehicle minimization; ride time; ODK; multi-agent relay; conformance.

## 1. Research question and operational objective

**Question.** Can one shared object interface represent a heterogeneous transportation schedule, expose legal and illegal candidate edits, evaluate tradeoffs, and govern state promotion without conflating the identities, permissions, and constraints of its constituent objects?

A plausible optimization objective is **lexicographic**:

1. Enforce all hard safety, coverage, eligibility, and operational constraints.
2. Minimize the number of buses used in the scheduled service period.
3. Among equally sized feasible fleets, minimize student ride burden, excess waiting, deadhead distance, and operating cost according to declared policy.
4. Preserve robustness to uncertainty and service disruptions.

The ordering is a **proposed policy**, not a universal district preference. A district may instead impose strict maximum ride-time limits and use a weighted or Pareto objective for secondary metrics. An infeasible plan is never made feasible by a favorable score.

**Non-goals:** designing a certified vehicle-routing solver, replacing district dispatch authority, inferring actual student needs from a synthetic dataset, claiming that vehicle minimization is the only legitimate objective, or proving convergence of generic CDE search.

## 2. Companion contracts and boundaries

- [OCSRE-003 — Dynamic, Relational, and Multi-Granular Reasoning](../docs/OCSRE-003-Dynamic-Relational-and-Multi-Granular-Reasoning.md): temporal and granularity reasoning.
- [OCSRE-004 — Object Differential Kernel and Generic Operators](../docs/OCSRE-004-Object-Differential-Kernel-and-Generic-Operators.md): typed comparison and evaluation.
- [OCSRE-006 — SQL-to-Object Attribute Transformation and Semantic Alignment](../docs/OCSRE-006-SQL-to-Object-Attribute-Transformation-and-Semantic-Alignment.md): relational data adaptation.
- [OCSRE-007 — In-Situ Object Learning, Decision, and Feedback](../docs/OCSRE-007-In-Situ-Object-Learning-Decision-and-Feedback.md): feedback and learning separation.
- [OCSRE-008 — WE-Native CDE and Composite State Evolution](../docs/OCSRE-008-WE-Native-CDE-and-Composite-State-Evolution.md): constrained state evolution.
- [OCSRE-009 — Epistemic Separation and Object-Centric Evidence Governance](../docs/OCSRE-009-Epistemic-Separation-and-Object-Centric-Evidence-Governance.md): provenance and evidence gates.
- [SPEC-001 — Object Identity, Perspective, and State Contract](../specs/SPEC-001-Object-Identity-Perspective-and-State-Contract.md).
- [SPEC-002 — Object Differential Kernel and Comparator Contract](../specs/SPEC-002-Object-Differential-Kernel-and-Comparator-Contract.md).
- [SPEC-003 — Classical Reasoning Preservation and Granularity Contract](../specs/SPEC-003-Classical-Reasoning-Preservation-and-Granularity-Contract.md).
- [SPEC-004 — Object Plugin and Capability Composition Contract](../specs/SPEC-004-Object-Plugin-and-Capability-Composition-Contract.md).
- [SPEC-005 — In-Situ Learning, Feedback, and Epistemic Governance Contract](../specs/SPEC-005-In-Situ-Learning-Feedback-and-Epistemic-Governance-Contract.md).
- [SPEC-006 — WE-Native CDE, Composite State, and Relay Contract](../specs/SPEC-006-WE-Native-CDE-Composite-State-and-Relay-Contract.md).
- [CASE-002 — SQL-Native Object Adaptation](CASE-002-SQL-Native-Object-Adaptation.md): a **separate** SQL fixture for load-ratio semantics; its assignments A1–A3 are not presumed to be the trips in this case.

WE-SIO supplies foundational WE semantics. OCSRE defines a common interoperability surface; CDE supplies constrained candidate evolution. UTN/WE-HDT/SIF can help locate relevant constraints or state components, but their search algorithms are not asserted equivalent. MLIU/UIERU can organize experiments and relay, subject to receiver-side validation.

## 3. Entity model: the composite is not one undifferentiated object

| WE / typed component | Identity and representative state | Typical constraint or evidence |
|---|---|---|
| `Student` | Stable student reference, eligibility, assigned stop and service needs | One authorized service assignment per required trip; privacy |
| `Stop` | Stop identity, geolocation or network node, access rules | Authorized pickup and drop-off |
| `Trip` | Trip identity, service date, stop sequence, departure/arrival | Time windows, rider set, travel time |
| `Bus` | Vehicle identity, seat capacity, accessibility features | No simultaneous trips; inspection and capacity |
| `Driver` | Authorized operator identity and qualification | Duty limits, qualification and availability |
| `RoutePlan` | Versioned assignment of trips and sequences | Sequence feasibility and coverage |
| `Fleet` | Composite membership and operational resource pool | Distinct active buses and availability |
| `ScheduleState` | Bounded, versioned CDE container over these references | Global invariants and authority |

The `ScheduleState` may be a composite **container** without acquiring an independent real-world WE identity. A bus can appear in several trips over a day but cannot operate overlapping trips. A student can have multiple legitimate trip requirements across a day; uniqueness is per required service instance, not a global one-trip rule.

### 3.1 Identity, address, state, and perspective

A source database key, a resolved `WEIdentity`, a UTN address, a vehicle's current state, and a planner's scoring perspective are separate. Metric similarity between two routes is not evidence that they are the same route. A scheduling agent may hold an optimization perspective but not the district's authority to dispatch buses.

## 4. Composite State-Container proposal

The following YAML is a **conceptual contract illustration**, not an executable schema:

```yaml
StateContainer:
  container_id: school-service-2026-11-06-AM
  schema_version: ocsre-case003-v1
  owner_ref: district-dispatch-authority
  baseline_state_ref: schedule-v1
  temporal_scope: 2026-11-06-AM
  membership:
    we_refs: [bus:B1, bus:B2, bus:B3, trip:T1, trip:T2, trip:T3]
    relation_refs: [trip-assignment, trip-precedence, vehicle-availability]
  perspectives: [hard-feasibility, fleet-minimization, student-ride-burden]
  constraint_set_ref: constraints-v1
  metric_policy_ref: objective-lexicographic-v1
  permitted_mutations: [reassign-trip, resequence-trip, merge-compatible-duty]
  evidence_ref: synthetic-fixture-v1
  promotion_policy_ref: human-dispatch-review
```

Every candidate must bind to the baseline version and a declared read/write set. Membership alone confers neither write authority nor access to protected student data. Real deployments would use pseudonymous references, access-controlled data, and auditable consent/legal bases as applicable.

## 5. A fully specified synthetic miniature fixture

To make arithmetic and feasibility independently checkable, this fixture models **three indivisible morning trips**, not individual stop-by-stop vehicle routing. Each trip already covers a distinct authorized rider set. All buses are identical, have 40 seats, are available from 07:00 to 09:00, and start from a common depot. Each trip's time interval below **includes its required setup, movement, and return-to-ready time**. A bus may perform consecutive trips when the first interval ends at or before the second begins. There are no driver constraints in this deliberately narrow fixture; a real validation profile must add them before operational promotion.

| Trip | Required interval (local) | Riders | Seats required | Assigned bus in baseline |
|---|---|---:|---:|---|
| T1 | 07:00–07:40 | 30 | 30 | B1 |
| T2 | 07:20–08:00 | 18 | 18 | B2 |
| T3 | 08:05–08:45 | 25 | 25 | B3 |

All intervals are half-open `[start, end)`. All three rider sets are distinct. Synthetic per-student ride durations are fixed at 25, 30, and 28 minutes for T1, T2, and T3 respectively; they are **stipulated inputs**, not inferred from the 40-minute resource intervals. The illustrative ride-time ceiling is 45 minutes. There are no stop-order changes in this first fixture.

**Baseline:** three buses are used, each with one trip. **Candidate:** assign T3 to B1 after T1, leaving T2 on B2; B3 becomes unused. Since 07:40 ≤ 08:05, B1's two trips do not overlap. The proposed schedule uses two buses. The reduction is **one bus (3 → 2) within the fixture**, not a measured fleet saving in a district.

### 5.1 Capacity and coverage checks

- T1: `30 <= 40` seats; T2: `18 <= 40`; T3: `25 <= 40`.
- Each of the three required trips remains assigned exactly once.
- T1 and T2 overlap between 07:20 and 07:40, so **at least two buses** are required in this fixture. The two-bus candidate is therefore optimal for this *restricted interval-assignment model*, by an elementary overlap lower bound. This does **not** establish optimality for a real bus-routing problem with different trips, stop sequences, or driver constraints.
- Each stipulated student ride duration is at most 45 minutes; none changes in this candidate.

### 5.2 Explicit metric projections

`Object[metricIndices]` can project `fleet_used_count`, `trip_coverage_fraction`, `max_stipulated_ride_minutes`, and `overlap_violations`, provided that every projection carries its grain, time window, unit, provenance, and perspective. For this synthetic fixture:

| Metric | Baseline | Candidate | Semantics |
|---|---:|---:|---|
| Active buses | 3 | 2 | Distinct buses with assigned trips in AM window |
| Trip coverage | 3/3 | 3/3 | Required trip instances assigned |
| Max stipulated ride duration | 30 min | 30 min | Per-student value assumed constant here |
| Overlap violations | 0 | 0 | Pairwise bus-trip interval conflicts |
| Capacity violations | 0 | 0 | Riders exceed seats on any trip |

An ODK differential can report `Δ active buses = -1`; it cannot by itself certify that driver qualification, school arrival deadlines, or real-world traffic requirements have been satisfied.

## 6. Optimization model and its declared limitations

Let `T` be trips and `B` be buses. Define binary `x[t,b]` for assigning trip `t` to bus `b`, and `y[b]` for whether bus `b` is used. For the restricted interval model:

\[
\min \sum_{b\in B} y_b
\]

subject to

\[
\sum_{b\in B} x_{t,b}=1 \quad \forall t\in T,
\qquad x_{t,b}\le y_b,
\]

and, for any pair of overlapping trips `t,u`,

\[
x_{t,b}+x_{u,b}\le 1 \quad \forall b\in B.
\]

Additional eligibility and capacity constraints can prohibit infeasible assignments. This compact model is intentionally **not** a full vehicle-routing formulation: it assumes fixed trip intervals and prevalidated trip contents. General scheduling requires travel-time matrices, stop sequencing, student-specific pickup/drop-off and accessibility constraints, driver resources, and robust time-window checks. Those additions alter the feasible set and possibly the optimum.

## 7. Typed Delta catalog

| Delta kind | Example | Read scope | Write scope | Required validation |
|---|---|---|---|---|
| `ReassignTrip` | T3: B3 → B1 | T3, B1/B3 duty sequences | Assignment and vehicle duty | No overlap; capacity; eligibility; authority |
| `ResequenceTrips` | Change trip order on B1 | B1 trips and travel times | B1 sequence | Temporal feasibility and service windows |
| `MergeDuties` | Combine two compatible bus duties | Both duties and resource availability | Duty membership | Full composite consistency |
| `SplitDuty` | Split infeasible combined duty | Existing duty and candidate resources | Duty assignment | Coverage and available vehicles |
| `AdjustStopSequence` | Swap pickup order | Students, stops, road-time data | Trip stop sequence | Ride time, accessibility, pickup windows |
| `ChangeMetricPolicy` | Adjust secondary cost weights | Policy version and authority | Proposed policy version | Review and authorization; not physical dispatch |

**Typed Delta example:**

```yaml
TypedDelta:
  delta_id: delta-reassign-T3-to-B1
  kind: ReassignTrip
  target_ref: trip:T3
  baseline_state_ref: schedule-v1
  read_scope: [trip:T1, trip:T3, bus:B1, bus:B3, fleet:AM]
  write_scope: [assignment:T3, duty:B1, duty:B3]
  preconditions:
    - T3 currently assigned to B3
    - B1 and B3 available under schedule-v1
  proposed_effect:
    - T3 assigned to B1 after T1
    - B3 unassigned in AM window
  required_checks:
    - trip coverage and uniqueness
    - bus interval nonoverlap
    - capacity and eligibility
    - composite global invariants
    - permission and version freshness
  status: proposed
```

The proposed effect must not be written to an operational schedule until promotion gates succeed. A state update can be represented transactionally, but external dispatch instructions require separate execution and confirmation.

## 8. Local validity versus global validity

A reassignment may look valid for the target trip while creating a conflict elsewhere. For example, assigning T2 to B1 would violate the overlap rule because T1 and T2 share 07:20–07:40. An apparently harmless stop-order edit might cause one student's ride to exceed a ceiling, or violate a school arrival window. A local capacity check does not imply global feasibility.

The validator therefore computes an **impact closure** across resource-sharing edges and declared constraints. If that closure cannot be established reliably, it must conservatively validate the relevant full composite state or return `unknown`. In safety-sensitive profiles, `unknown` must not be promoted as `pass`.

## 9. CDE candidate generation and search memory

A proposed search node carries `(container version, candidate schedule, path history, residuals, constraint results, evaluation policy, budget)`. Candidate generators may propose reassignments, merges, splits, and resequencing. Search may branch dynamically M→N, with branching determined by the current residuals and admissible Delta classes.

A path-dependent non-reuse policy should record at least `(kind, target, parameters, pre-state fingerprint, semantic fingerprint)`. Repeating the same Delta kind in a changed state may be legitimate; forbidding it universally could remove valid solutions. Likewise, a `NoSubtree` decision must distinguish **proven infeasibility**, **sound dominance pruning**, and **heuristic rejection**. Only the first two, under their declared assumptions, justify strong pruning claims.

Loop-back controls may use canonical schedule fingerprints, path budgets, and explicit cycle policies. For a finite fixed-trip assignment fixture, exhaustive enumeration is possible in principle; no such guarantee is asserted for general, dynamic, real-world scheduling.

## 10. ODK evaluation is not feasibility or authorization

The ODK comparison pipeline is `Resolve → Project → Align → Evaluate → Qualify → Trace`. Its output must identify:

- the exact baseline and candidate versions;
- metric grain (trip, student, bus duty, or fleet) and time scope;
- units and aggregation rules;
- hard-constraint status separately from optimization score;
- missing/uncertain travel and ride-time inputs;
- provenance and permission qualification.

A lower fleet-count score is not a feasibility certificate. A feasible simulated candidate is not an approved district schedule. An approved schedule is not evidence that the trip was actually completed.

## 11. State promotion and operational governance

A proposed lifecycle is:

1. **Acquire:** load authorized, versioned baseline inputs.
2. **Resolve:** bind source keys to WE references and identify uncertainties.
3. **Generate:** produce a typed Delta and affected-scope declaration.
4. **Sandbox:** apply the Delta to an isolated candidate container.
5. **Validate:** check all hard invariants, including transitive impacts.
6. **Evaluate:** compute qualified ODK comparisons and tradeoffs.
7. **Review:** challenge assumptions, permissions, and uncertainty.
8. **Authorize:** obtain approval from the responsible operational authority.
9. **Commit:** atomically update the authorized planning representation, with version checks.
10. **Execute/Observe:** issue separately authorized real-world dispatch actions and record outcomes.
11. **Learn:** attribute deviations and update evidence or proposals, not retroactive facts.

Optimistic concurrency failures require revalidation against the latest baseline. A database rollback cannot undo a bus departure or student pickup; real-world compensation must be separately defined.

## 12. SQL-to-WE bridge

The database adaptation described in [CASE-002](CASE-002-SQL-Native-Object-Adaptation.md) may supply buses, service trips, and boarding observations. However, this case's fixed-trip fixture is **not** a reinterpretation of CASE-002's A1/A2/A3 rows. A production adapter must resolve identity, select consistent snapshots, preserve `NULL` and three-valued logic, avoid join multiplication, enforce row/column-level permissions, and retain source lineage. `Bucketize` or `Normalize` may support metrics but must not silently change service eligibility or safety rules.

## 13. In-situ learning and feedback

After service, observed arrival times, rider counts, and ride durations may differ from the plan. Learning updates should distinguish:

- **Evidence attachment:** add signed observations without overwriting the planned state.
- **Epistemic revision:** revise uncertain travel-time estimates with provenance.
- **Metric calibration:** update prediction-error distributions, retaining versioned baselines.
- **Policy proposal:** suggest revised ride-time penalties or robustness buffers.
- **Capability proposal:** suggest a new candidate-generation plugin.

Feedback must be attributed to service date, trip, bus duty, route conditions, observation method, and relevant interventions. Correlation between a schedule change and a better outcome is not, by itself, causal proof. No learning update grants dispatch authority.

## 14. Multi-agent and collective structural learning

Different agents may propose vehicle reassignments, audit student ride-time constraints, evaluate uncertainty, or independently verify candidate schedules. A shared Object interface can let these agents exchange typed candidate artifacts, validation traces, and counterexamples. The coordinator must not treat agent agreement as independent evidence if the agents share the same unverified input or scoring model.

A relay from bus scheduling to inventory routing or staff allocation would transfer a **candidate generator or constraint-checking capability**, not student data, operational authority, or an assertion of semantic equivalence. Receiver-side contracts, held-out tasks, and negative-transfer tracking are mandatory for a credible OCSH-008 test.

## 15. Proposed conformance obligations

The following `SBS-` identifiers are local to CASE-003 and do not replace `WCR-` requirements in SPEC-006.

| ID | Proposed obligation | Expected evidence |
|---|---|---|
| SBS-001 | Distinguish WE identity from source keys and locations | Identity mapping trace |
| SBS-002 | Bind every schedule to immutable baseline version | Versioned fixture |
| SBS-003 | Declare composite membership and typed relations | Container manifest |
| SBS-004 | Enforce exact coverage of required trip instances | Coverage validator |
| SBS-005 | Enforce seat capacity at trip grain | Capacity trace |
| SBS-006 | Enforce vehicle nonoverlap and availability | Interval conflict report |
| SBS-007 | Validate student-specific constraints where applicable | Ride-time and eligibility report |
| SBS-008 | Preserve temporal, metric, and granularity scope | Metric envelope |
| SBS-009 | Declare Delta read/write/impact scopes | Delta manifest |
| SBS-010 | Check cross-object/global constraints | Impact-closure validation |
| SBS-011 | Reject stale-baseline promotion | Version-conflict test |
| SBS-012 | Separate ODK score from feasibility | Distinct output fields |
| SBS-013 | Separate proposal, validation, authorization, and commit | Promotion audit |
| SBS-014 | Do not equate representation rollback with real-world reversal | Compensation boundary |
| SBS-015 | Preserve missingness, uncertainty, and provenance | Evidence envelope |
| SBS-016 | Enforce access-control restrictions across plugins | Permission-negative test |
| SBS-017 | Record search-path Delta fingerprints and loop policy | Search trace |
| SBS-018 | Distinguish sound pruning from heuristic rejection | Pruning reason code |
| SBS-019 | Attribute observed outcomes to relevant contexts | Feedback linkage |
| SBS-020 | Require receiver-side validation for relayed capabilities | Transfer report |
| SBS-021 | Report negative transfer and integration cost | Held-out evaluation |
| SBS-022 | Preserve explicit unresolved residuals | Residual registry |

## 16. Positive reference tests (proposed, not executed)

| Test | Setup | Expected result |
|---|---|---|
| P-01 | Baseline T1/B1, T2/B2, T3/B3 | Three assigned trips; three buses |
| P-02 | Reassign T3 to B1 after T1 | Feasible in restricted fixture; two buses |
| P-03 | Validate capacity of each trip | All pass: 30, 18, 25 ≤ 40 |
| P-04 | Check fixed ride durations | All pass under stipulated 45-minute ceiling |
| P-05 | Compute maximum simultaneous overlap | Two trips, hence two-bus lower bound |
| P-06 | ODK compare baseline vs candidate | Qualified `Δ fleet_used_count = -1` |
| P-07 | Candidate sandbox validation | Candidate state remains uncommitted |
| P-08 | Human review with correct version | Candidate eligible for authorization, not auto-dispatch |
| P-09 | Attach simulated service observation | Evidence event distinct from planned state |
| P-10 | Export generic nonoverlap validator | Receiver must still validate domain semantics |

These are test **specifications with expected outcomes**; no automated test runner has been executed.

## 17. Negative and adversarial tests (proposed)

| Test | Counterexample | Required outcome |
|---|---|---|
| N-01 | Assign T2 to B1 while T1 remains on B1 | Reject: interval overlap |
| N-02 | Assign T3 to both B1 and B3 | Reject: duplicate trip assignment |
| N-03 | Remove T2 without replacement | Reject: coverage failure |
| N-04 | Change T1 rider count to 41 on 40-seat bus | Reject: capacity failure |
| N-05 | Treat bus source key as proven WE identity | Reject/qualify identity mapping |
| N-06 | Aggregate trip-level ride times as individual proof | Reject invalid granularity inference |
| N-07 | Ignore `NULL` travel-time estimate | Return unknown; no unsafe promotion |
| N-08 | Promote after baseline version changes | Reject stale-state commit |
| N-09 | Score lower fleet count despite a safety violation | Reject feasibility; preserve score only as qualified diagnostic |
| N-10 | Plugin requests unauthorized student attributes | Deny and audit |
| N-11 | Two agents copy same erroneous travel-time source | Do not count as independent corroboration |
| N-12 | Heuristic branch rejection labeled proven infeasible | Reject misleading proof status |
| N-13 | Repeated Delta cycle without budget or cycle policy | Reject/stop search under declared profile |
| N-14 | Undo committed plan after bus already departed | Require external compensation; no fictional rollback |
| N-15 | Dispatch from an unapproved sandbox candidate | Deny external action |
| N-16 | Transfer bus-specific capacity rule to inventory pallets | Require semantic revalidation |
| N-17 | Join observations multiplies student/trip rows | Reject or correct cardinality |
| N-18 | Candidate removes accessible bus from eligible service | Reject accessibility constraint violation |
| N-19 | Student ride exceeds declared maximum | Reject, even if fewer buses used |
| N-20 | Concurrent agent commits conflicting vehicle assignment | Detect conflict and revalidate |

## 18. Evaluation design and baselines

A future experiment should compare: (A) an exact or established scheduling solver for small fixed instances; (B) a conventional domain-specific heuristic; and (C) a CDE candidate generator using the same problem data and constraint checker. For larger realistic cases, report computational budget and solver timeouts rather than assuming global optimality.

**Primary outcomes:** hard-constraint violations (target zero), fleet size among feasible schedules, fraction of required services covered, maximum and distributional ride times, robustness under travel-time perturbations, and planning latency. **Structural outcomes:** ODK kernel modifications required, number of reusable validators, plugin adaptation effort, provenance completeness, invalid-Delta rejection rate, and negative-transfer frequency. Report confidence intervals where sampling is meaningful and distinguish synthetic, simulated, and real observations.

**Ablations:** remove typed Delta scopes, cross-object impact closure, version checks, or receiver-side conformance one at a time to quantify their contribution. No empirical effect size is currently known.

## 19. Hypothesis mapping

| Hypothesis | Proposed test in this case | Current status |
|---|---|---|
| OCSH-002 | Reuse ODK without modifying kernel between trip and fleet metrics | E0 / proposed |
| OCSH-003 | Compare plugin adaptation cost against domain-specific implementation | E0 / proposed |
| OCSH-004 | Test whether contextual feedback improves traceability or prediction calibration | E0 / proposed |
| **OCSH-005** | Validate single-WE and composite State-Container transitions under shared contracts | **E0 / primary** |
| **OCSH-006** | Reject invalid trip→student and fleet→bus inferences | **E0 / primary** |
| OCSH-007 | Verify SQL-to-WE mapping semantics and permission preservation | E0 / proposed |
| OCSH-008 | Validate a scheduling capability in a different receiving domain | E0 / proposed |
| OCSH-009 | Measure untargeted gains only on held-out tasks | E0 / proposed |
| OCSH-010 | Longitudinal accumulation and relay study; no scaling claim | E0 / proposed |

OCSH-001 (classical deduction) is primarily tested in CASE-001; OCSH-011 (code governance) is primarily tested in CASE-006. This case may reuse their contracts without claiming to validate those hypotheses.

## 20. Counterexample-driven research implications

The fixture demonstrates why the **unit of optimization is often a composite**, even when the unit of explanation is an individual object. A bus's local availability, a trip's capacity, and a student's ride limit each live at different grains. The correct intervention may require an impact closure through several relation types. This is an argument for shared object interfaces and explicit granularity contracts—not proof that object-centric search is computationally superior to existing vehicle-routing methods.

The miniature example also illustrates a disciplined separation: a candidate can be mathematically feasible under stipulated assumptions, structurally valid under a declared schema, and still unfit for operational use because omitted driver, road, school, or legal constraints remain unresolved.

## 21. Explicit leftovers and open questions

1. How should student-specific pickup and drop-off windows be represented across heterogeneous schools?
2. Which composite boundaries minimize validation cost without hiding global conflicts?
3. How should accessibility, special-needs transport, and vehicle compatibility be formalized?
4. What constitutes a stable WE identity for a recurring trip versus a dated trip instance?
5. How should live traffic and travel-time uncertainty alter hard feasibility checks?
6. Which robust or chance-constrained formulations are appropriate under different risk policies?
7. How can driver duty and qualification constraints be integrated without privilege leakage?
8. How should multi-depot deadhead and repositioning time enter the state model?
9. What is the correct equivalence notion for repeated path Deltas?
10. Which `NoSubtree` pruning rules are provably sound for each restricted problem class?
11. How should a CDE policy handle cyclic but productive local search?
12. Can impact closure be incremental without missing indirect resource constraints?
13. When is a full composite revalidation mandatory?
14. How should vehicle maintenance and unexpected breakdowns be incorporated?
15. Which fairness metrics capture disproportionate student ride burden?
16. How can objectives be compared without collapsing different stakeholder perspectives?
17. What evidence threshold should be required before autonomous dispatch is even considered?
18. How should source database snapshots be synchronized with operational dispatch systems?
19. How should post-dispatch cancellation and external compensation be modeled?
20. What is the integration cost of generic ODK versus a purpose-built evaluator?
21. How should transfer to inventory or staff scheduling measure negative transfer?
22. Can multi-agent candidate generation outperform controlled baselines at equal compute budget?
23. How should student privacy be preserved in cross-agent validation traces?
24. What conditions permit a justified generalization from synthetic tests to field trials?

All leftovers are research tasks, not silently satisfied assumptions.

## 22. Conclusion

School-bus scheduling exposes the central promise and difficulty of WE-native constrained evolution: a shared Object interface can make heterogeneous resources, relations, constraints, evidence, and candidate changes explicitly addressable, but it does not eliminate the need for domain-specific feasibility rules or operational authority. The restricted synthetic example shows how a two-bus candidate can be justified from three fixed trips, while deliberately withholding claims about realistic routing or solver performance. The next step is to implement the proposed contracts and test them against exact small-instance baselines, adversarial cases, and held-out operationally realistic datasets. **Specifications and conformance precede runtime claims; unresolved residuals remain explicit.**

---

**Repository placement:** `cases/CASE-003-School-Bus-Scheduling-and-Composite-WE-State.md`  
**Research status:** E0 — conceptual case and proposed tests only.  
**Related planned figure:** [`../figures/Fig-007-WE-Native-CDE-and-Composite-State-Evolution.png`](../figures/Fig-007-WE-Native-CDE-and-Composite-State-Evolution.png) (planned asset; not required to read this case).
