# CASE-004 — Transaction and Compositional Identity

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Artifact type:** Research case, synthetic reference fixture, and proposed conformance suite  
**Target release:** v1.0.0 — Research Framework and Contracts  
**Authors:** Sizhe Tan & GPT-Obot  
**License:** Apache-2.0  
**Status:** Research proposal / E0. All identities, transactions, and scores in this case are synthetic. No real-world attribution, deployed detector, or empirical performance is claimed.

## Abstract

A transaction ledger records observable transfers, but the entities that control, coordinate, or benefit from those transfers may be composite, time-varying, and only partially observable. An account, wallet, public key, transaction, device, or network endpoint is not automatically a human or organizational identity. This case develops an object-centric method for representing transaction evidence and **compositional identity hypotheses** without collapsing weak correlations into proven control. It defines typed World Entities (WEs), temporally scoped relationships, candidate actor-group hypotheses, provenance-aware evidence, an Object Differential Kernel (ODK) evaluation path, and WE-native Constrained Delta Evolution (CDE) for revising the *analytical hypothesis state*. A fully synthetic ledger fixture supports reproducible reasoning about flow conservation, temporal feasibility, and ambiguity. Proposed conformance tests cover false attribution, correlated evidence, key reuse, change of control, privacy, adversarial manipulation, and governance boundaries. The intended result is a disciplined research interface, not an identity deanonymization service or a claim that blockchain transparency proves who acted.

**Keywords:** OCSRE; WE; compositional identity; transaction graph; weak evidence; temporal inference; ODK; CDE; provenance; uncertainty; collective learning; conformance.

## 1. Research question and scope

**Research question.** Can a common Object interface represent transactions, accounts, keys, actors, organizations, and uncertain coordination hypotheses; support constrained candidate revisions; and preserve the distinction between observed transfers and inferred identity?

The case focuses on **analytical state evolution**: constructing, challenging, and revising hypotheses about relations among observed entities. It does **not** authorize transaction execution, account intervention, identification of real persons, or sanctions. It does not claim that one transfer path uniquely identifies a controlling actor.

The motivating distinction is:

> A transaction graph is observable evidence about transfers; a compositional identity graph is a defeasible hypothesis about control, coordination, or common agency.

The two graphs may overlap but must never be silently equated.

## 2. Companion papers, specifications, and hypotheses

- [OCSRE-003](../docs/OCSRE-003-Dynamic-Relational-and-Multi-Granular-Reasoning.md): typed, temporal, relational, and cross-granularity inference.
- [OCSRE-004](../docs/OCSRE-004-Object-Differential-Kernel-and-Generic-Operators.md): metric projections and typed comparison.
- [OCSRE-007](../docs/OCSRE-007-In-Situ-Object-Learning-Decision-and-Feedback.md): feedback attribution and traceable revision.
- [OCSRE-008](../docs/OCSRE-008-WE-Native-CDE-and-Composite-State-Evolution.md): composite state and typed Delta.
- [OCSRE-009](../docs/OCSRE-009-Epistemic-Separation-and-Object-Centric-Evidence-Governance.md): epistemic status and evidence promotion.
- [OCSRE-010](../docs/OCSRE-010-UTN-WE-HDT-and-SIF-Localization-Through-Shared-Object-Interfaces.md): localization is not identity resolution.
- [OCSRE-011](../docs/OCSRE-011-Object-Capability-Spillover-Relay-and-Collective-Structural-Learning.md): independently validated capability relay.
- [SPEC-001](../specs/SPEC-001-Object-Identity-Perspective-and-State-Contract.md): object identity, perspective, and version.
- [SPEC-002](../specs/SPEC-002-Object-Differential-Kernel-and-Comparator-Contract.md): comparator contracts.
- [SPEC-003](../specs/SPEC-003-Classical-Reasoning-Preservation-and-Granularity-Contract.md): valid relational and cross-granularity inference.
- [SPEC-004](../specs/SPEC-004-Object-Plugin-and-Capability-Composition-Contract.md): typed plugin composition.
- [SPEC-005](../specs/SPEC-005-In-Situ-Learning-Feedback-and-Epistemic-Governance-Contract.md): feedback and evidence governance.
- [SPEC-006](../specs/SPEC-006-WE-Native-CDE-Composite-State-and-Relay-Contract.md): candidate evolution, global validation, and relay.

**Primary hypotheses:** OCSH-005 (single and composite WE-native CDE), OCSH-006 (cross-granularity contracts), and OCSH-004 (traceable in-situ revision). **Secondary:** OCSH-002, OCSH-003, OCSH-008, and OCSH-011, where applicable. All remain E0; these references are traceability targets, not results.

## 3. Epistemic layers

A compliant analysis must preserve the following layers:

| Layer | Example | Permitted claim | Not permitted without more evidence |
|---|---|---|---|
| Raw record | Signed transaction `tx-01` | A specified ledger event was recorded | The signer is a named person |
| Derived observation | Funds moved from A to B | A transfer edge exists in a stated snapshot | A and B share a controller |
| Metric | Timing proximity score | Two events are close under a declared rule | Coordination is proven |
| Hypothesis | A and C may share operational control | Candidate grouping, with uncertainty | Definitive common ownership |
| Evaluation | Hypothesis H fits selected observations | Fit under declared model and assumptions | H is uniquely true |
| Decision | Request independent review | Proposed analytical action | Permission to freeze funds or expose identities |
| Validation | Independent evidence supports/refutes H | Scoped revision of confidence | Universal attribution certainty |

**Logical implication, statistical association, causal explanation, and authorization are different types of claim.**

## 4. WE types and object boundaries

Illustrative WE types include `Transaction`, `Account`, `Wallet`, `Key`, `Address`, `Asset`, `Block`, `Service`, `DeviceObservation`, `NetworkObservation`, `ActorHypothesis`, and `CompositeActorHypothesis`. These are not interchangeable:

- `Transaction` identifies an event; `Address` identifies a ledger identifier under a chain-specific namespace.
- `Key` represents cryptographic material or a public-key identifier; key possession at one time does not prove enduring human identity.
- `Wallet` is a software or custody construct and may contain multiple accounts or signers.
- `ActorHypothesis` is an explicitly **hypothetical** model of agency, not a verified person.
- `CompositeActorHypothesis` models several actors, roles, services, or controlled accounts under a versioned relational explanation.

Every WE carries typed identity, namespace, state version, temporal scope, provenance, epistemic status, visibility policy, and authority context. Source database keys and UTN/WE-HDT addresses are locators, not ontological identity proofs.

## 5. Typed relational vocabulary

Use explicit relations such as `transferred_to`, `signed_by_key`, `observed_at`, `custodied_by` (only if evidenced), `possibly_controls`, `possibly_coordinates_with`, `belongs_to_hypothesis`, and `contradicts_hypothesis`.

Each relation must specify domain/range types, direction, validity interval, provenance, confidence semantics if any, and admissible inference rules. `transferred_to` is not necessarily transitive as a statement of control; `possibly_controls` is not equivalent to `controls`; and co-occurrence is not proof of a shared actor. Chain-specific contract calls, bridges, custodians, and mixers can alter what a visible edge means.

## 6. Synthetic transaction fixture

Consider a fictional ledger with a single asset `TOK`, integer unit accounting, no fees, and the following records. All addresses are artificial labels.

| Event | Time (UTC) | Source | Destination | Amount TOK |
|---|---|---|---|---:|
| tx-01 | 09:00 | A | B | 40 |
| tx-02 | 09:03 | A | C | 30 |
| tx-03 | 09:08 | B | D | 25 |
| tx-04 | 09:11 | C | D | 20 |
| tx-05 | 09:16 | D | E | 35 |
| tx-06 | 09:22 | D | F | 10 |

For this restricted example, A has 100 TOK initially; B, C, D, E, and F have zero. There are no other events. Final balances are A=30, B=15, C=10, D=0, E=35, F=10, totaling 100 TOK. This arithmetic is an **illustrative invariant**, not evidence of common control.

A and B/C exhibit a split; B/C and D exhibit a convergence. Such patterns can motivate candidate questions but cannot distinguish, without additional evidence, between one actor, multiple actors, a payment processor, an exchange, or ordinary independent transfers.

## 7. Three competing identity hypotheses

- **H1 — Common controller:** A, B, and C are under one controller during the fixture interval.
- **H2 — Independent recipients:** B and C are distinct recipients that independently pay D.
- **H3 — Service-mediated pattern:** B, C, or D represent custodial or routing services acting for several users.

The ledger fixture alone does not identify a unique winner. A conformant system must retain all plausible hypotheses or an explicit `underdetermined` result. A grouping of accounts must be stored as a *hypothesis object* with membership rationale, not as an irreversible rewrite of WE identities.

## 8. Compositional identity model

Define a candidate composite hypothesis state:

```text
CompositeActorHypothesis {
  hypothesis_id, version, time_interval,
  members: [WEReference],
  typed_roles: [RoleAssertion],
  relations: [EvidenceBackedRelation],
  assumptions: [Assumption],
  supporting_evidence: [EvidenceReference],
  contradicting_evidence: [EvidenceReference],
  uncertainty: UncertaintyEnvelope,
  review_status, provenance, permissions
}
```

Membership may be probabilistic or unresolved; it must not force a partition of all accounts. An entity may appear in multiple competing hypotheses. A hypothesis may include a service role rather than a human identity. Changes of control require interval-specific relations, not a single permanent label.

## 9. Object[metricIndices] and ODK comparison

Candidate metrics include temporal proximity, flow consistency, amount patterns, graph topology, contract-call similarity, independent infrastructure observations, and contradictory evidence. Each projection has a unit, scope, normalization policy, missingness semantics, source reliability assessment, and permission label.

Illustrative pipeline:

```text
Resolve(WE references, snapshot, permissions)
  -> Project(metric indices, perspective)
  -> Align(time, asset units, chain, granularity)
  -> Evaluate(typed comparator, candidate hypotheses)
  -> Qualify(uncertainty, missingness, alternatives)
  -> Trace(evidence, operator versions, residuals)
```

A graph-distance score and a public-key match are not interchangeable metrics. A comparator may be asymmetric or nonmetric; its output must declare this. No score threshold by itself may promote a candidate actor hypothesis to verified identity.

## 10. Directional weak evidence and dependency

Suppose a candidate H is supported by a transfer-timing pattern and a graph-topology pattern. Both may arise from the *same transactions*. Treating them as independent evidence exaggerates confidence. A provenance graph must link each derived metric to source records and shared assumptions.

Independent evidence could, in principle, include lawfully obtained service attestations or authorized operational records; its provenance, relevance, retention, and permission constraints still require validation. IP addresses, device fingerprints, and public keys can be shared, rotated, spoofed, proxied, or service-mediated. They are neither inherently unique persons nor automatically lawful to correlate. The case specifies no procedure for obtaining private identifying data.

## 11. WE-native CDE: evolve hypotheses, not the ledger

A CDE `StateContainer` may include the transaction WEs, typed relations, candidate composite hypotheses, evidence graph, scoring policy, and unresolved residuals. The ledger snapshot is treated as immutable source evidence; **candidate Deltas modify the analytical model**.

Proposed typed Delta classes:

| Delta | Intended effect | Key validation |
|---|---|---|
| `AddHypothesis` | Introduce H4 | Nonduplicative ID, evidence scope |
| `AddCandidateMember` | Attach account to H | Membership is hypothetical and time-scoped |
| `RemoveCandidateMember` | Revise membership | Preserve prior version and rationale |
| `SplitHypothesis` | Separate incompatible roles | No evidence silently discarded |
| `MergeHypotheses` | Propose shared agency | No forced identity equivalence |
| `AttachEvidence` | Link source to assertion | Provenance, permission, dependency |
| `ChallengeHypothesis` | Register contradiction | Contradiction remains visible |
| `ReviseComparator` | Change scoring policy | Versioning, held-out regression |

Every Delta requires a precondition, read/write scope, expected version, constraint checks, audit trace, and authorization for promotion. Rejected proposals remain visible as research residuals.

## 12. Composite constraints and state invariants

Hard constraints include: transaction conservation under the stated fixture model; chain and asset compatibility; event chronology; no mutation of source ledger records; no promotion of inferred identity to verified identity without qualifying evidence; no use of evidence outside permission scope; and no erasure of contradictory observations. Where real ledgers have fees, minting, burning, cross-chain bridges, or reorgs, those features must be explicitly modeled before conservation is applied.

Global validation is necessary: a locally plausible `MergeHypotheses` Delta can conflict with time-scoped control, role exclusivity, or another hypothesis's evidence. The framework must permit multiple unresolved alternatives rather than imposing one globally coherent but unsupported story.

## 13. Dynamic candidate search and loop-back

CDE can generate M→N candidate branches: split, merge, relabel role, revise time scope, or request independent evidence. Path-specific Delta reuse rules and NoSubtree annotations help avoid redundant cycles, but cannot by themselves prove termination in an unbounded hypothesis space. A bounded research run should declare maximum depth, budget, version semantics, stopping conditions, and the scope of deduplication.

A candidate search must not optimize solely for a high similarity score: doing so may reward fabricated overfitting. A defensible objective combines constraint validity, explanatory coverage, calibration, contradiction penalties, model complexity, and cost of further evidence. These weights are perspective- and policy-dependent.

## 14. Learning and feedback

In-situ learning can revise evidence weights, comparator calibration, hypothesis priors, or candidate-generation policies. Feedback may include newly confirmed service roles, newly falsified assumptions, or held-out transaction patterns. Every update must retain its prior version, attribution limits, and regression evidence.

**Outcome feedback is not automatically causal feedback.** A later observation consistent with H1 does not establish that H1 caused it. Likewise, a successful explanation on one chain does not demonstrate portability to another chain or custody model.

## 15. Multi-agent and collective relay

A generator agent may propose hypotheses; a constraint agent may test ledger arithmetic and chronology; an evidence auditor may challenge provenance and independence; a reviewer may assess authorization and downstream impact. Their outputs must be independently traceable, not counted as separate evidence merely because multiple agents repeated the same source.

Relay candidates include reusable transaction-WE adapters, temporal alignment operators, evidence-dependency checkers, composite-state validators, and counterexample fixtures. Transfer to school-bus scheduling is **structural** (composite constraints and typed Deltas), not a claim that bus trips and financial transfers share domain semantics.

## 16. Cross-case transfer with CASE-003

Both [CASE-003](CASE-003-School-Bus-Scheduling-and-Composite-WE-State.md) and this case involve composite WEs and globally constrained revisions. However:

| Dimension | School-bus scheduling | Transaction analysis |
|---|---|---|
| Primary state | Proposed operational schedule | Analytical hypotheses about observations |
| Delta target | Trips, assignments, duties | Membership, evidence, interpretations |
| Hard constraints | Capacity, time, coverage | Provenance, chronology, identity separation |
| Evaluation | Feasibility and fleet/ride metrics | Explanatory fit and uncertainty |
| Promotion | Operational authorization required | Analytical review required |
| External risk | Unsafe dispatch | False attribution and privacy harm |

Reuse must be proven at the contract level, with domain-specific validators retained.

## 17. Governance and misuse boundaries

False attribution can create severe legal, financial, and reputational harm. Therefore, the research profile requires: purpose limitation; access control; minimization of identifying information; explicit evidence provenance; human review for consequential decisions; appeal/correction paths where appropriate; and clear retention rules. A candidate group must not be displayed as a verified person or organization.

No automated freezing, account targeting, disclosure of private identifiers, or punitive action follows from ODK scores or CDE candidate promotion. External actions require separate lawful authority, independent checks, and domain-specific controls. Public ledger data does not remove privacy or governance obligations.

## 18. Positive reference tests (proposed)

| ID | Test | Expected result |
|---|---|---|
| TCI-P01 | Sum synthetic final balances | 100 TOK |
| TCI-P02 | Verify A outgoing | 70 TOK |
| TCI-P03 | Verify D incoming/outgoing | 45 / 45 TOK |
| TCI-P04 | Resolve `tx-03` as event WE | Distinct from B or D actor identity |
| TCI-P05 | Create H1 and H2 concurrently | Both retained as alternatives |
| TCI-P06 | Attach same source to two metrics | Shared dependency flagged |
| TCI-P07 | Split H1 into time-scoped variants | Prior version preserved |
| TCI-P08 | Add contradictory evidence | Confidence qualified; contradiction visible |
| TCI-P09 | Compare temporal proximity | Time window and unit declared |
| TCI-P10 | Export a relay candidate | Recipient-side conformance required |

These are expected outcomes of a future implementation, not executed test results.

## 19. Negative and adversarial tests (proposed)

| ID | Failure scenario | Required behavior |
|---|---|---|
| TCI-N01 | Same address assumed to equal same person forever | Reject identity shortcut |
| TCI-N02 | Shared public key assumed to prove common human controller | Require scoped alternative explanations |
| TCI-N03 | IP co-occurrence asserted as identity | Reject unsupported inference |
| TCI-N04 | Device fingerprint treated as unique and permanent | Qualify and challenge |
| TCI-N05 | Two derived scores from one transaction counted independently | Detect source dependence |
| TCI-N06 | Temporal order reversed | Reject invalid causal/flow narrative |
| TCI-N07 | Token amounts compared across incompatible assets | Require conversion contract or reject |
| TCI-N08 | Fees ignored in nonzero-fee ledger | Reject conservation claim |
| TCI-N09 | Custodial service account equated with end user | Preserve role separation |
| TCI-N10 | Missing records treated as proof of absence | Mark incompleteness |
| TCI-N11 | Hypothesis merge silently overwrites dissenting evidence | Reject Delta |
| TCI-N12 | Candidate grouping displayed as verified identity | Block promotion |
| TCI-N13 | Unauthorized private observation joined to public graph | Deny access and trace |
| TCI-N14 | Contradictory observation dropped to improve score | Reject evidence erasure |
| TCI-N15 | Model trained and tested on same transactions | Flag leakage |
| TCI-N16 | Multi-agent repetition treated as independent corroboration | Deduplicate provenance |
| TCI-N17 | Chain reorganization ignored | Require snapshot/finality semantics |
| TCI-N18 | Unbounded split/merge loop | Enforce budget and loop control |
| TCI-N19 | High similarity score authorizes external intervention | Reject unauthorized action |
| TCI-N20 | Cross-domain plugin reused without semantic mapping | Fail receiving conformance |

## 20. Conformance obligations

The following requirements are **proposed**, not yet satisfied by a runtime:

1. **TCI-001:** Preserve typed WE identity separately from addresses, keys, and actor hypotheses.
2. **TCI-002:** Version source snapshots and analytical states independently.
3. **TCI-003:** Attach temporal scope to control and coordination assertions.
4. **TCI-004:** Distinguish observed transfers from inferred agency.
5. **TCI-005:** Represent alternative composite hypotheses without forced partitioning.
6. **TCI-006:** Preserve provenance of every derived metric and assertion.
7. **TCI-007:** Record dependence among apparently distinct evidence items.
8. **TCI-008:** Enforce asset, unit, chain, and temporal alignment before comparison.
9. **TCI-009:** Qualify missing data and uncertainty explicitly.
10. **TCI-010:** Prevent metric scores from becoming deductive proofs or identity facts.
11. **TCI-011:** Require typed, versioned Deltas for hypothesis revisions.
12. **TCI-012:** Preserve contradictory evidence through candidate evolution.
13. **TCI-013:** Validate composite constraints after local changes.
14. **TCI-014:** Bound search, Delta reuse, and loop-back according to declared policy.
15. **TCI-015:** Separate analytical promotion from external authorization.
16. **TCI-016:** Enforce permissions on evidence access, joins, exports, and relay.
17. **TCI-017:** Maintain an auditable history of feedback and policy revisions.
18. **TCI-018:** Require independent receiving-domain validation for capability transfer.
19. **TCI-019:** Record negative transfer, false positives, and unresolved cases.
20. **TCI-020:** Compare performance with explicit baselines and held-out fixtures.
21. **TCI-021:** Provide human review for consequential identity claims.
22. **TCI-022:** Keep all unvalidated research claims labeled E0.

**Priority:** TCI-001–016 and TCI-021 are P0 semantic/evolution safety gates; TCI-017–020 are P1 learning and transfer evidence; TCI-022 is a release-wide reporting requirement. No conformance certification is claimed.

## 21. Validation roadmap and measurement

**Stage A — Static semantics:** machine-readable WE types, relationship schemas, epistemic labels, and synthetic fixtures; check conservation and chronology under explicit assumptions.

**Stage B — Contract harness:** execute positive and negative tests with failure traces, permission-denial cases, and reproducible versions.

**Stage C — Hypothesis quality:** use independently labeled, synthetic or properly authorized datasets; measure precision, recall, calibration, abstention quality, and harm-weighted false attribution. Report prevalence and uncertainty intervals.

**Stage D — Comparative baselines:** compare graph-only heuristics, domain-specific analysis, and OCSRE+ODK+CDE under equal data access and compute budgets. Measure runtime, validation cost, analyst effort, and traceability.

**Stage E — Relay:** attempt reuse of a typed evidence-dependency checker or composite-state validator in a second domain; record adapter work, semantic failures, negative transfer, and marginal net benefit.

No stage implies production deployment or a generalizable performance gain. Controlled results would still need external replication.

## 22. Explicit leftovers and open research questions

1. What is the correct ontological boundary between account, key, custodian, service, and actor?
2. How should a composite identity represent changing control over time?
3. Which observations are independent enough to count as corroboration?
4. Can source-dependency graphs prevent confidence inflation in practice?
5. How should privacy-preserving evidence linkage be implemented?
6. What confidence semantics remain calibrated under adversarial behavior?
7. How should multi-chain bridges, fees, reorgs, and asset wrappers be modeled?
8. When should a hypothesis be split instead of qualified?
9. Can competing hypotheses be maintained efficiently at scale?
10. What role should abstention play in consequential attribution?
11. How should adversarial counterexamples be generated without contaminating evaluation?
12. What are appropriate base rates for rare coordinated behaviors?
13. How should provenance survive SQL-to-WE transformations?
14. Can ODK remain unchanged across materially different ledger semantics?
15. What parts of CDE search improve over simpler beam or branch-and-bound baselines?
16. How can loop-back constraints remain meaningful under revised evidence?
17. How should irreversible external actions be separated from reversible analytical revisions?
18. What independent reviewer evidence is sufficient for hypothesis promotion?
19. How can agent disagreement improve exploration without false evidence multiplication?
20. Which components transfer to scheduling, code governance, or inventory without semantic loss?
21. How should negative transfer and integration overhead be measured?
22. What governance mechanisms prevent harmful false identification?
23. What dataset permissions and retention policies are needed for credible replication?
24. What empirical evidence would falsify OCSH-005 or OCSH-006 in this domain?

All leftovers remain open. Proposed examples and tests do not constitute experimental validation.

## Conclusion

Transaction analysis illustrates why compositional identity must be modeled as a versioned, evidence-backed hypothesis rather than inferred directly from ledger adjacency, public keys, or similarity scores. OCSRE supplies a candidate common language for observable transaction WEs, differential evaluation, typed relational inference, in-situ revision, and WE-native CDE over analytical state. Its value remains a testable proposition: the synthetic fixture demonstrates specification clarity, not attribution accuracy or operational benefit. Future work must prioritize semantic safety, independent validation, calibrated abstention, privacy, and negative-transfer reporting before any stronger claim about structural intelligence or capability spillover is justified.

---

**Repository placement:** `cases/CASE-004-Transaction-and-Compositional-Identity.md`  
**Research status:** E0 — conceptual case, synthetic fixture, and proposed conformance tests only.  
**Related cases:** [CASE-003](CASE-003-School-Bus-Scheduling-and-Composite-WE-State.md), [CASE-005](CASE-005-Cross-Domain-Object-Plugin-Relay.md) (planned).  
**Figure context:** [`../figures/Fig-007-WE-Native-CDE-and-Composite-State-Evolution.png`](../figures/Fig-007-WE-Native-CDE-and-Composite-State-Evolution.png) (planned asset).
