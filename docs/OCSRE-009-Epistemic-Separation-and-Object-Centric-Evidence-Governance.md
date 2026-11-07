# OCSRE-009 — Epistemic Separation and Object-Centric Evidence Governance

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Release track:** v1.0.0 — Research Framework and Contracts  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**Status:** Research proposal; proposed contracts and hypotheses are E0 (unvalidated)  
**License:** Apache-2.0

## Abstract

Object-centric structural intelligence requires more than a shared object representation and reusable computation. It requires a disciplined account of *what is known, how it is known, who asserts it, and which consequences an assertion is permitted to trigger*. This paper proposes **epistemic separation** as a foundational governance requirement for OCSRE: observations, source records, derived measurements, logical conclusions, probabilistic inferences, hypotheses, evaluations, decisions, authorized actions, and verified outcomes must remain distinguishable across object identity, perspective, temporal scope, and state version. We propose an evidence-envelope interface, typed derivation and promotion rules, a provenance graph, explicit contradiction and uncertainty handling, and conformance tests for evidence-consuming plugins and WE-native CDE. The proposal connects Object Differential Kernel (ODK) calculations, dynamic reasoning, in-situ learning, SQL adaptation, multi-agent relay, and AI-generated-code governance without treating scores as proofs or candidate changes as authorized actions. It is a specification-first research design, not a demonstrated epistemic calculus or production assurance system.

**Keywords:** epistemic separation; evidence provenance; World Entity; object-centric reasoning; perspective; uncertainty; ODK; CDE; conformance; structural relay; AI code governance.

## 1. The epistemic problem in object-centric intelligence

OCSRE-001 through OCSRE-008 establish a progression from object-centric representation through computation, reasoning, learning, and constrained evolution. Each stage can introduce a dangerous category error. A database row can be mistaken for an entity; a metric score for a fact; a statistical association for a deductive conclusion; a model recommendation for an authorized decision; and a simulated state transition for an observed real-world outcome. Errors compound when outputs become inputs to plugins, agents, or downstream learning systems.

The central thesis is therefore: **shared object interfaces must preserve epistemic distinctions at least as rigorously as they preserve data types.** An object is a semantic anchor for claims, not a warrant that all attached claims are true. An evidence graph records the lineage and scope of assertions; it does not guarantee the reliability of its sources.

This paper proposes contracts for these distinctions. It does not claim that one universal confidence scale, inference engine, or ontology can resolve every domain's uncertainty.

## 2. Scope, architectural ownership, and non-goals

- **WE-SIO** supplies World Entity (WE) identity, state, perspective, and evidence semantics. OCSRE references these semantics and proposes interoperable governance interfaces rather than redefining WE identity.
- **OCSRE-002 and OCSRE-003** distinguish deductive validity from richer relational, temporal, cross-granularity, and perspective-dependent reasoning.
- **OCSRE-004 (ODK)** provides typed comparison and qualification; it does not certify truth or confer action authority.
- **OCSRE-005 and OCSRE-006** introduce plugin and SQL transformations whose provenance, permissions, and semantic alignment must survive composition.
- **OCSRE-007** defines learning feedback with explicit observation, prediction, decision, and outcome distinctions.
- **OCSRE-008 / CDE** defines candidate typed Deltas, validation, promotion, and external-action boundaries.
- **UTN / MDT / WE-HDT / SIF** may locate relevant object, evidence, or code-graph nodes; localization is not proof.
- **MLIU / UIERU / ISGFTR** motivate collective learning and relay, but transfer requires new-domain validation.

Non-goals include a claim of universal truth discovery, a complete probabilistic logic, an automatic trust oracle, or a security guarantee from provenance metadata alone.

## 3. Epistemic classes and forbidden collapses

A proposed minimal classification is:

| Class | Meaning | Example | Must not silently become |
|---|---|---|---|
| `SOURCE_RECORD` | Imported artifact or data entry | SQL transaction row | Verified real-world entity identity |
| `OBSERVATION` | Reported measurement with instrument/context | GPS position at time *t* | Timeless ground truth |
| `DERIVED_MEASURE` | Result of declared transformation | Normalized travel time | Proof of a causal claim |
| `DEDUCTIVE_CONCLUSION` | Conclusion from premises and a specified valid rule | Subtype inheritance in a restricted logic | Universal conclusion outside rule scope |
| `STATISTICAL_INFERENCE` | Model- or sample-based estimate | Probability of route delay | Certain fact |
| `HYPOTHESIS` | Tentative explanatory proposition | Two addresses share an operator | Established identity |
| `EVALUATION` | Preference/score under declared objective | Route score | Permission to dispatch |
| `DECISION_PROPOSAL` | Suggested choice | Reassign bus | Approved instruction |
| `AUTHORIZED_ACTION` | Action approved within authority boundary | Commit approved schedule | Verified execution success |
| `VERIFIED_OUTCOME` | Observed result with validation evidence | Confirmed route execution | Proof of all intended effects |

Classes may be refined per domain. They are not a total ordering of certainty: a formally valid deduction from false premises is not automatically more reliable than a direct, calibrated observation. A source may contain both raw data and an author's inference; ingestion must separate these when feasible.

## 4. Evidence envelopes: a proposed interface

An evidence-bearing claim can be modeled schematically as:

```text
EvidenceEnvelope {
  claim_id, subject_we_ref, subject_state_version,
  predicate_or_metric, value_or_proposition,
  epistemic_class, assertion_time, valid_time,
  perspective_id, asserting_actor, source_refs,
  derivation_rule_or_model, transformation_chain,
  confidence_descriptor, assumptions, limitations,
  access_policy, retention_policy, integrity_reference,
  review_status, supersedes_refs, residual_refs
}
```

This is an interface proposal, not a mandatory storage layout. `subject_we_ref` may be unresolved or provisional; it must never be manufactured from a row key without an identity contract. `valid_time` and `assertion_time` differ: a report filed today may describe last month's state. `confidence_descriptor` must declare its interpretation (e.g., calibrated probability, interval, qualitative grade, or *not assessed*); scores from incompatible methods cannot be averaged by default.

**Minimum invariant:** an assertion can be reproduced or challenged at the level of its source, transformation, rule, object scope, and perspective—or explicitly marked as lacking one or more of these elements.

## 5. Object, perspective, and state anchoring

Let a claim be indexed by `(WE, state_version, perspective, time_scope, assertion_id)`. This tuple does not establish truth; it makes incompatible or evolving claims addressable. A WE's enduring identity is distinct from a snapshot and from an observer's representation of that snapshot. Multiple perspectives may legitimately attach different evaluations to the same event; contradictory empirical claims require reconciliation or unresolved status, not silent averaging.

A composite WE state needs additional membership, aggregation, and ownership contracts. Evidence about a member cannot be promoted to a group claim without a valid quantifier or aggregation rule. Conversely, group-level statistics do not establish every member's properties. This extends the granularity safeguards of OCSRE-003 and anticipated SPEC-003.

## 6. Provenance as a typed derivation graph

Model evidence lineage as a directed graph `G_E = (V_E, E_E)`, where vertices represent records, observations, assertions, transformations, and reviews. Edges are typed (`observed_from`, `derived_by`, `supports`, `contradicts`, `supersedes`, `evaluated_under`, `approved_by`, `validated_against`). Cycles in a source-support graph require special treatment: mutually citing claims do not create independent corroboration.

A derived claim should record a rule and its required premises. A rule may be deterministic, deductive, statistical, heuristic, or human-reviewed; the rule type must be explicit. For deductive claims, validity applies only to the specified formal system and its premises. For statistical claims, provenance should include model/version, population or sampling scope, calibration status where available, and known distribution-shift limitations.

**Evidence dependency is not causal dependency.** A provenance edge saying that a model used a feature does not establish that the feature caused the observed outcome.

## 7. Qualified inference and promotion gates

A useful generic pattern is:

```text
Acquire -> Type -> Scope -> Derive -> Qualify -> Challenge
        -> Review -> Promote (to a specified epistemic tier)
```

Promotion is never a generic operation called `make_true`. It must name the target tier and a governing rule: for example, a tentative hypothesis may become a *validated operational hypothesis under a stated test protocol*, not an unconditional fact. A decision proposal may be approved for a specific action without upgrading the empirical certainty of its supporting claims.

For a proposed transition `S' = Apply(S, delta)` in WE-native CDE, epistemic checks are part of, but not a substitute for, constraints and authorization:

```text
eligible(delta) = type_ok AND scope_ok AND permission_ok
                  AND evidence_gate_ok AND constraint_ok
                  AND validation_ok
```

The conjunction is conceptual: individual predicates can return `pass`, `fail`, or `unknown`. Unknown must not be coerced into pass, especially at external irreversible-action boundaries. Different risk classes require different gates.

## 8. ODK outputs are evidence-bearing measurements, not proofs

An ODK comparison may return a score, signed difference, partial ordering, similarity measure, or explanation. Each result requires metric definitions, units, comparator semantics, alignment rules, scope, and uncertainty qualifiers. An `Object[metricIndices]` projection is meaningful only under the corresponding metric contract.

A high similarity between two transaction clusters may justify investigation; it does not establish common ownership. A high score for a bus route may support ranking; it does not prove feasibility. A change-impact estimate on a calling graph may identify likely tests; it does not prove absence of unmodeled runtime behavior. ODK's `Resolve -> Project -> Align -> Evaluate -> Qualify -> Trace` discipline should therefore emit evidence envelopes, not bare numbers, at governance boundaries.

## 9. SQL adaptation and source-semantic preservation

SQL-to-WE transformation must preserve source lineage, permissions, NULL semantics, temporal scope, join cardinality, aggregation grain, and the identity distinction between rows and world entities. `Bucketize`, `Normalize`, `Combine`, `Encode`, and `Derive` can generate useful attributes but can also obscure original uncertainty or change interpretation.

Examples of forbidden inference include treating `NULL` as false, counting duplicated join rows as independent evidence, converting a bucket label into an ordinal measurement without justification, and deriving an entity identity from an unstable surrogate key. A transformation plugin should declare input/output schemas, information loss, access restrictions, and whether reverse reconstruction is possible.

## 10. Learning, feedback, and evidence revision

In-situ learning must distinguish prediction, chosen intervention, observed outcome, and attribution. A feedback event can revise a belief or metric calibration without rewriting the historical observation that motivated it. Corrections should create versioned supersession edges and preserve the prior claim for audit where policy allows.

A learning system may update policies, representations, or capability rankings, but every update should identify its supporting evidence and evaluation protocol. Positive reward is not sufficient proof of causal effectiveness; reward hacking, confounding, missing counterfactuals, and distribution shift are explicit residuals. Learning updates are distinct from CDE state Deltas and from actual external actions.

## 11. Contradiction, uncertainty, and abstention

Contradictions must be typed. Two observations may disagree because of time, measurement uncertainty, differing perspectives, source errors, or genuinely incompatible propositions. A contradiction registry should retain both assertions, their provenance, the proposed reconciliation, and any remaining uncertainty.

When evidence is insufficient, the permitted outcomes include `unknown`, `contested`, `out_of_scope`, `not_authorized`, and `requires_review`. An abstention is a valid governance result. Absence of evidence is not automatically evidence of absence; a negative conclusion requires a declared observation or coverage model.

## 12. Multi-agent evidence and relay governance

Collective learning can improve coverage and discover alternative explanations, but many agents repeating the same source do not create independent evidence. Relay packages should include the claim and its provenance, interface and plugin versions, source dependency graph, conformance outcomes, negative-transfer history, access restrictions, and unresolved residuals.

A receiving domain must revalidate semantics, granularity, and performance. The ability to execute a plugin is not equivalent to successful transfer of its epistemic guarantees. Cross-domain capability spillover is therefore an empirical hypothesis, not an automatic property of shared object interfaces.

## 13. AI-generated code governance: calling graphs to UTN to OCSRE

A calling graph is a useful *perspective* on software change. UTN-style localization can address affected nodes and dependencies; OCSRE can attach evidence and governance envelopes to code objects, functions, tests, contracts, and candidate patches. But calling graphs alone do not capture data flow, control flow, dynamic dispatch, security policy, runtime configuration, or emergent side effects.

A proposed code-change evidence package includes: repository revision, generated patch, changed object/function identities, call/data/control dependencies, inferred impact set, test-selection rationale, static-analysis results, security checks, executed regression evidence, reviewer authority, and residual untested risks. `Test passed` means the specified test passed in the recorded environment; it does not mean the software is universally correct or safe. Deployment remains a separately authorized action.

This interface is developed further in `CASE-006-AI-Generated-Code-Governance-Through-Calling-Graphs-and-CDE.md` and is relevant to **OCSH-011**.

## 14. Illustrative scenarios

### 14.1 School-bus scheduling

A school-bus optimizer observes route durations, derives normalized travel-time metrics, proposes a lower-fleet-count schedule, and evaluates its score. Before promotion, the system must verify capacity, time windows, assignment uniqueness, and other cross-object constraints. Historical travel-time samples, predicted travel times, proposed schedules, authorized dispatch, and executed outcomes are distinct evidence classes. See `CASE-003-School-Bus-Scheduling-and-Composite-WE-State.md`.

### 14.2 Transaction and compositional identity

Shared network metadata or public keys may be useful evidence of a possible relationship, subject to lawful access and domain-specific interpretation. Shared indicators do not necessarily prove a shared human or organizational controller. Preserve alternative explanations, confidence limitations, temporal scope, and privacy constraints. See `CASE-004-Transaction-and-Compositional-Identity.md`.

### 14.3 SQL-native object adaptation

A joined transaction table yields an apparent surge in events. A provenance-aware adapter identifies duplicated rows due to one-to-many joins and refuses to treat the inflated count as independent evidence. See `CASE-002-SQL-Native-Object-Adaptation.md`.

### 14.4 AI-generated code changes

A patch changes a helper called by several services. A calling-graph differential identifies candidate impact nodes; data/control-flow analysis expands the affected set; selected tests pass, but an untested dynamic path remains. Governance records partial validation and blocks unconditional promotion. See `CASE-006-AI-Generated-Code-Governance-Through-Calling-Graphs-and-CDE.md`.

## 15. Proposed conformance obligations

The following **EPI** identifiers are local paper-level obligations, intended for consolidation in `SPEC-001`, `SPEC-003`, `SPEC-005`, and `SPEC-006`. They are proposed tests, not completed certification.

| ID | Obligation | Example failure condition |
|---|---|---|
| EPI-001 | Preserve source record versus WE identity | Row key asserted as verified identity |
| EPI-002 | Tag epistemic class on consequential claims | Score labeled as fact |
| EPI-003 | Preserve assertion time and valid time | Stale observation treated as current |
| EPI-004 | Preserve perspective and actor | Subjective rating merged as objective fact |
| EPI-005 | Record derivation and source lineage | Derived metric has no source chain |
| EPI-006 | Qualify confidence semantics | Uncalibrated score interpreted as probability |
| EPI-007 | Enforce typed inference rules | Invalid relation transitivity |
| EPI-008 | Enforce cross-granularity contracts | Group average attributed to every member |
| EPI-009 | Preserve SQL null/join/permission semantics | Join duplicates count as independent evidence |
| EPI-010 | Record contradictions and supersessions | Conflicting assertions silently overwritten |
| EPI-011 | Distinguish recommendation from authorization | High-ranked proposal automatically executed |
| EPI-012 | Distinguish simulated state from verified outcome | Candidate CDE state labeled deployed |
| EPI-013 | Respect evidence access policy through plugins | Restricted source leaked through derived output |
| EPI-014 | Retain agent/source dependency information | Copied evidence counted as independent support |
| EPI-015 | Preserve explicit unknown/abstain status | Missing evidence coerced to pass |
| EPI-016 | Require risk-sensitive promotion gates | Irreversible action approved by score alone |
| EPI-017 | Record model, rule, and plugin versions | Unreproducible inference after plugin update |
| EPI-018 | Trace code-governance claims to tests and gaps | Passing unit test claimed to prove full safety |

**P0:** EPI-001–013, EPI-015–016 for semantic and action safety. **P1:** EPI-014, EPI-017–018 for relay and auditability. Runtime optimization is P2 and does not waive P0 requirements.

## 16. Counterexamples and adversarial tests

1. **Identity conflation:** two source systems reuse the same row ID for different entities.
2. **Time collapse:** yesterday's GPS observation is used as a live location assertion.
3. **Confidence laundering:** cosine similarity `0.93` is displayed as `93% probability` without calibration.
4. **Circular corroboration:** three agents cite the same original report as three independent confirmations.
5. **Granularity leakage:** a fleet average is asserted as each vehicle's measured value.
6. **False transitivity:** `related_to(A,B)` and `related_to(B,C)` imply `related_to(A,C)` without a valid rule.
7. **SQL duplication:** a join multiplies event counts and falsely strengthens evidence.
8. **NULL collapse:** missing measurement becomes a measured zero.
9. **Perspective collapse:** a stakeholder preference is presented as a physical property.
10. **Action laundering:** a CDE candidate is dispatched before constraint checks and approval.
11. **Feedback misattribution:** a route improvement is credited to a plugin despite a concurrent policy change.
12. **Security leak:** a derived metric reveals restricted source data to an unauthorized plugin.
13. **Evidence erasure:** a model update overwrites an earlier contradictory result without audit trace.
14. **Calling-graph incompleteness:** an unmodeled dynamic invocation invalidates a “no impact” claim.
15. **Negative transfer:** a validated metric from one domain is reused with incompatible units and populations.
16. **Unverified execution:** a successful test or simulation is misreported as real-world deployment success.

Each counterexample should have a negative fixture, expected abstention/rejection/qualification behavior, and regression assertion in the future validation suite.

## 17. Evaluation protocol and falsifiable hypotheses

The initial evaluation is **contract conformance**, not a claim of improved intelligence. Construct fixtures for identity, provenance, perspective, time, granularity, permissions, and action gating. Compare a baseline pipeline that emits unqualified scores or claims with an envelope-aware pipeline under identical workloads.

Candidate metrics include: epistemic-class confusion rate; provenance completeness; invalid promotion rate; contradiction detection recall; abstention appropriateness; permission-violation count; audit reconstruction success; false corroboration rate; and cost/latency overhead. Report both safety gains and overhead. Evaluate on held-out scenarios and adversarial fixtures, with predeclared thresholds where possible.

**Hypothesis connections (all E0):**

| Registry ID | Evidence-governance relevance |
|---|---|
| OCSH-001 | Restricted classical inference must preserve declared deductive validity |
| OCSH-002 | Reusable ODK requires qualified outputs and traceable comparators |
| OCSH-003 | Contract-based plugins may lower adaptation cost without erasing provenance |
| OCSH-004 | In-situ learning may improve feedback traceability |
| OCSH-005 | WE-native CDE must distinguish candidates, validation, and authorized transitions |
| OCSH-006 | Cross-granularity contracts may reduce invalid inheritance |
| OCSH-007 | SQL-to-WE transformations must preserve source semantics and permissions |
| OCSH-008 | Relay requires independently validated transfer evidence |
| OCSH-009 | Untargeted spillover gains require held-out evaluation |
| OCSH-010 | Sustained capability growth remains unproven and requires longitudinal evidence |
| OCSH-011 | Code-governance traceability may improve with object-centric evidence |

A negative result, including governance overhead exceeding benefit, should be recorded rather than hidden.

## 18. Interfaces to repository artifacts

| Artifact | Intended interface |
|---|---|
| `SPEC-001-Object-Identity-Perspective-and-State-Contract.md` | Object/perspective/time anchoring and identity safeguards |
| `SPEC-002-Object-Differential-Kernel-and-Comparator-Contract.md` | Qualified metrics, comparator lineage, and uncertainty |
| `SPEC-003-Classical-Reasoning-Preservation-and-Granularity-Contract.md` | Deductive validity and cross-granularity proof obligations |
| `SPEC-004-Object-Plugin-and-Capability-Composition-Contract.md` | Plugin provenance, permissions, and versioned composition |
| `SPEC-005-In-Situ-Learning-Feedback-and-Epistemic-Governance-Contract.md` | Primary normative home for EPI obligations and feedback revision |
| `SPEC-006-WE-Native-CDE-Composite-State-and-Relay-Contract.md` | Candidate/evidence/action promotion and relay governance |
| `research-trace/HYPOTHESIS-REGISTRY.md` | E0 hypothesis status and evaluation history |
| `research-trace/COUNTEREXAMPLE-REGISTRY.md` | Negative fixtures and discovered failures |
| `research-trace/UNRESOLVED-RESIDUALS.md` | Uncertainty, blocked promotions, and open anomalies |
| `VALIDATION-ROADMAP.md` | Planned conformance and empirical test phases |

The figure `Fig-006-In-Situ-Object-Intelligence-Loop.png` is relevant to evidence revision, while `Fig-007-WE-Native-CDE-and-Composite-State-Evolution.png` is relevant to promotion gates. No additional figure is claimed as completed here.

## 19. Explicit leftovers and open questions

1. Can a compact epistemic type system remain expressive across scientific, operational, and social domains?
2. Which epistemic classes should be mandatory versus domain-specific?
3. How should heterogeneous confidence descriptors be compared without false numerical equivalence?
4. What is a rigorous, implementable calculus for contradiction under changing time and perspectives?
5. How can provenance remain inspectable while honoring privacy, confidentiality, and retention policies?
6. How should an evidence graph handle cycles, shared sources, and correlated agents at scale?
7. Which proofs are feasible for restricted classical reasoning and which require runtime checks?
8. How should uncertain entity resolution propagate to dependent conclusions?
9. How can SQL transformation information loss be represented and tested automatically?
10. What evidence threshold is appropriate for low-risk versus irreversible external actions?
11. How should human review be represented without treating reviewer authority as empirical truth?
12. How can learning systems revise beliefs while preserving legally required deletion or correction rights?
13. Which metrics best distinguish appropriate abstention from excessive conservatism?
14. What are the latency, storage, and integration costs of full evidence envelopes?
15. How can relay packages prove independence of supporting evidence across organizations?
16. How should dynamic code paths and external dependencies be included in AI code-governance assurance?
17. Can negative-transfer signals be used to improve plugin selection without overfitting benchmark cases?
18. What longitudinal study could test sustained structural capability spillover without claiming a universal scaling law?

These are research obligations, not defects concealed by a claim of completeness.

## 20. Conclusion

OCSRE's object-centered architecture is only as trustworthy as the boundaries between its claims and its actions. A WE reference gives assertions a common anchor, but neither identity nor shared interfaces establish truth. The proposed epistemic discipline preserves source records, observations, derivations, deductions, hypotheses, evaluations, decisions, actions, and verified outcomes as separately traceable objects of governance. It makes uncertainty and disagreement explicit, places promotion behind typed and risk-sensitive gates, and requires evidence to survive plugin composition, learning, CDE evolution, and relay. The next step is to turn these proposals into executable contracts, counterexample suites, and measured evaluations. Until then, epistemic separation is a falsifiable architectural thesis, not a validated guarantee.

---

**Research status:** E0 / proposed. No formal correctness proof, deployment, empirical benchmark, or scaling law is asserted.  
**Primary companion:** `SPEC-005-In-Situ-Learning-Feedback-and-Epistemic-Governance-Contract.md`.  
**Next core paper:** `OCSRE-010-UTN-WE-HDT-and-SIF-Localization-Through-Shared-Object-Interfaces.md`.
