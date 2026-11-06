# CASE-006 — AI-Generated Code Governance Through Calling Graphs and CDE

**Project:** Object-Centric Structural Reasoning and Evolution (OCSRE)  
**Release target:** v1.0.0 — Research Framework and Contracts  
**Document type:** Research case, synthetic worked example, and proposed conformance protocol  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**License:** Apache-2.0  
**Status:** Proposed / E0. No implemented analyzer, executed benchmark, or empirically validated performance is claimed.

## Abstract

AI-generated code changes can be syntactically correct and locally testable while remaining unsafe at the level of a program, deployment, or organizational policy. This case proposes an **object-centric, evidence-governed change-analysis workflow** that connects a software Calling Graph to Universal Token/Node (UTN) localization, World Entity (WE) representations, the Object Differential Kernel (ODK), and Constrained Delta Evolution (CDE). The Calling Graph is an initial structural perspective, **not a complete model of program semantics**. Data flow, control dependence, dynamic dispatch, configuration, schemas, security boundaries, tests, deployment constraints, and runtime evidence must be considered through typed plugins and qualified uncertainty. We specify a synthetic authorization-related code change, an explicit multi-graph representation, a typed candidate Delta, a staged impact-analysis procedure, positive and adversarial test designs, and a governance protocol that separates suggestion, analysis, validation, authorization, deployment, and observed outcome. The case operationalizes OCSH-011 while testing reusable OCSRE contracts without asserting that code-governance improvement or cross-domain spillover has already been demonstrated.

**Keywords:** AI-generated code; Calling Graph; UTN; WE; OCSRE; CDE; code change impact; static analysis; data flow; control dependence; security; conformance; provenance; relay.

## 1. Research question and bounded thesis

**Research question.** Can a shared Object/WE interface and governed constrained-evolution workflow improve the *localization, traceability, and validation targeting* of AI-generated code changes relative to established baselines, without overlooking security-relevant dependencies or conferring unauthorized execution rights?

**Proposed thesis.** Treating code entities, contracts, tests, and deployment artifacts as typed, versioned object representations may make heterogeneous analysis signals easier to compose and audit. A Calling Graph can guide initial localization; UTN and SIF localization interfaces can relate structural addresses to relevant objects; ODK can compare qualified versions and impacts; CDE can propose, check, and selectively promote candidate changes. This is an interoperability hypothesis, not a claim of semantic completeness, soundness, or superiority over existing software-analysis tools.

**Non-goals:** replacing compilers or language-specific type systems; solving general program equivalence; proving the absence of vulnerabilities; automatically deploying code; treating a passing test suite as complete correctness; or establishing a universal scaling law.

## 2. Relationship to the OCSRE research program

This case uses the following previously proposed research boundaries:

| Source | Role in this case |
|---|---|
| `docs/OCSRE-001-The-Object-Centric-Structural-Intelligence-Thesis.md` | Representation → Computation → Reasoning → In-Situ Learning → Constrained Evolution |
| `docs/OCSRE-004-Object-Differential-Kernel-and-Generic-Operators.md` | Typed Resolve → Project → Align → Evaluate → Qualify → Trace pipeline |
| `docs/OCSRE-005-Object-Plugins-and-Composable-Intelligence-Capabilities.md` | Language analyzers, security checks, test selectors, and deployment validators as contract-bound plugins |
| `docs/OCSRE-007-In-Situ-Object-Learning-Decision-and-Feedback.md` | Attribution and monitored feedback without conflating learning and action |
| `docs/OCSRE-008-WE-Native-CDE-and-Composite-State-Evolution.md` | Versioned composite state, candidate Deltas, constraints, and controlled promotion |
| `docs/OCSRE-009-Epistemic-Separation-and-Object-Centric-Evidence-Governance.md` | Distinction among observations, deductions, heuristic impact estimates, decisions, and authorization |
| `docs/OCSRE-010-UTN-WE-HDT-and-SIF-Localization-Through-Shared-Object-Interfaces.md` | Calling Graph → UTN → Object localization, without equating addresses with identities |
| `docs/OCSRE-011-Object-Capability-Spillover-Relay-and-Collective-Structural-Learning.md` | Cross-project transfer as a receiving-domain validation experiment |
| `specs/SPEC-001-Object-Identity-Perspective-and-State-Contract.md` | Object identity, snapshot, perspective, ownership, and authority |
| `specs/SPEC-002-Object-Differential-Kernel-and-Comparator-Contract.md` | Typed comparisons, metric qualification, and traceability |
| `specs/SPEC-003-Classical-Reasoning-Preservation-and-Granularity-Contract.md` | Proof-vs-heuristic separation and granularity rules |
| `specs/SPEC-004-Object-Plugin-and-Capability-Composition-Contract.md` | Plugin composition and effect boundaries |
| `specs/SPEC-005-In-Situ-Learning-Feedback-and-Epistemic-Governance-Contract.md` | Evidence provenance, feedback, promotion, and learning boundaries |
| `specs/SPEC-006-WE-Native-CDE-Composite-State-and-Relay-Contract.md` | Typed Delta, composite invariants, validation, authorization, rollback, and relay |

Related cases: `cases/CASE-003-School-Bus-Scheduling-and-Composite-WE-State.md` (composite constraints), `cases/CASE-004-Transaction-and-Compositional-Identity.md` (weak graph evidence), and `cases/CASE-005-Cross-Domain-Object-Plugin-Relay.md` (receiver-side transfer).

WE-SIO remains the source of foundational WE semantics. UTN, MDT, WE-HDT, and SIF provide possible localization and addressing capabilities; none is assumed equivalent to a Calling Graph or to another algorithm. CDE governs candidate state evolution rather than supplying program semantics.

## 3. Why a Calling Graph is necessary but insufficient

A Calling Graph records potential call relationships between callable units under an extraction policy. A directed edge `A → B` may mean that `A` can invoke `B`; its meaning depends on language, build configuration, dispatch resolution, and analysis precision. It does **not** mean that a call always executes, that `B` influences every output of `A`, or that every relevant dependency is a call.

Important dependencies can escape a call-only model:

1. **Data flow:** tainted values, shared stores, serialization, and database writes.
2. **Control dependence:** feature flags, authorization branches, exception paths, and guards.
3. **Dynamic behavior:** reflection, callbacks, dynamic dispatch, generated code, and runtime registration.
4. **Non-code dependencies:** schemas, configuration, policies, secrets handling, external APIs, build artifacts, and infrastructure.
5. **Concurrency and distribution:** asynchronous queues, event subscriptions, transactions, and eventual consistency.
6. **Evidence dependencies:** test coverage, security assertions, deployment gates, and incident reports.

Thus, **Calling Graph reachability is a candidate-impact signal, not a proof of behavioral impact or non-impact**. An incomplete graph MUST be labeled incomplete; a node not reached by an incomplete graph MUST NOT be certified unaffected on that basis alone.

## 4. Object-centric code representation

We propose typed WE-backed representations for code-relevant entities. A WE need not correspond one-to-one with an AST node, symbol, repository path, or UTN node.

| Object type | Identity / version boundary | Representative metrics or relations |
|---|---|---|
| `Repository` | repository identity + revision | ownership, policy, build graph |
| `Module` | language/build namespace + revision | imports, package boundaries |
| `Function` | qualified symbol + build configuration + revision | calls, inputs, outputs, effects |
| `DataArtifact` | schema/store identity + version | readers, writers, classification |
| `PolicyRule` | policy authority + revision | authorization preconditions |
| `Test` | test identity + revision + environment | covered requirements, observed result |
| `Service` | deployment identity + version | APIs, events, dependencies |
| `ChangeSet` | immutable change digest | touched objects, intended effects |
| `Finding` | analysis/tool/version + evidence ID | claim, scope, confidence, counterevidence |

**Identity separation:** a source-line coordinate is a location; a qualified symbol is an address-like identifier; a resolved code object is an entity representation; a metric neighborhood is a similarity relation; none grants authority to modify or deploy. Source lines and graph positions may change while semantic entities persist, and symbols can be renamed or reused.

A minimal object reference is conceptual, not a finalized wire format:

```yaml
CodeObjectRef:
  we_id: code-we://example/repo/authz/check_permission
  object_type: Function
  repository_revision: rev-base-001
  build_configuration: release-linux
  language: python
  resolution_policy: symbol-and-signature-v1
  structural_addresses:
    - namespace: calling-graph
      node: cg:check_permission
    - namespace: utn
      node: utn:authz:check_permission
  evidence_refs: [ev:parser-001, ev:build-001]
  authority_scope: read-only-analysis
```

The `we_id` shown is a synthetic placeholder, not an externally resolvable identifier.

## 5. Synthetic reference program and proposed change

Consider a service with the following **illustrative** execution structure:

```text
HTTP handler: submit_order
   ├── authenticate_request
   ├── check_permission  [CHANGE TARGET]
   └── create_order
          ├── validate_order
          └── persist_order

Separate paths:
   admin_batch_import ──> create_order
   order_event_consumer ──> persist_order
```

A generated patch proposes to speed up `check_permission` by caching its result. A naïve cache key uses only `user_id`; the actual authorization decision depends on `(user_id, tenant_id, resource_id, action, policy_version)` and possibly revocation timing. If the cache omits tenant and resource context, an allow decision from one scope may be reused in another. The defect is hypothetical and intentionally simplified; it illustrates a failure class, not an exploit recipe or a real incident.

### 5.1 Baseline versus candidate behavior

```python
# Simplified intended behavior (reference semantics)
def check_permission(user, tenant, resource, action, policy):
    return policy.evaluate(user, tenant, resource, action)

# Synthetic unsafe candidate: cache key omits required scope
# This is a negative test fixture, not recommended production code.
def candidate_cache_key(user, tenant, resource, action, policy):
    return user.id
```

The local Calling Graph may be unchanged by this patch: `submit_order` still calls `check_permission`. A graph-diff-only workflow can therefore report no new call edges even while the authorization semantics have changed. The appropriate response is **semantic-risk escalation**, not automatic acceptance.

### 5.2 Expected positive and negative observations

- Same user, tenant, resource, action, and unchanged policy: a permitted cache may reuse a result if freshness and revocation requirements allow it.
- Same user, different tenant: a cached allow MUST NOT cross the tenant boundary without independent authorization.
- Same user, different resource or action: a cached allow MUST NOT silently transfer.
- Policy revision or revocation: stale authorization decisions MUST be invalidated or rejected according to the declared policy contract.
- Passing unit tests limited to one tenant MUST NOT establish cross-tenant correctness.

These are **expected results of proposed tests**, not reports of executed tests.

## 6. Multi-graph dependency envelope

Instead of one universal graph, define a typed family:

\[
G = (G_{call}, G_{data}, G_{control}, G_{config}, G_{schema}, G_{policy}, G_{test}, G_{deploy})
\]

Each graph has an extraction method, version, coverage boundary, and edge semantics. Cross-graph joins require explicit object-resolution contracts. A shared symbol name is not enough to merge nodes.

```yaml
DependencyEdge:
  source_object: code-we://example/repo/submit_order
  target_object: code-we://example/repo/check_permission
  edge_kind: may_call
  evidence_kind: static_analysis
  analyzer_version: static-cg-v0
  build_configuration: release-linux
  coverage_scope: declared_sources_only
  epistemic_status: derived_observation
  uncertainty: dynamic_dispatch_unresolved
```

An impact-analysis result MUST retain both discovered dependencies and **unknown or unmodeled dependency classes**. Negative reachability claims are valid only relative to an explicitly bounded, adequately analyzed graph and do not imply universal absence of impact.

## 7. Calling Graph → UTN → OCSRE localization workflow

The proposed pipeline is:

```text
ChangeSet / diff / declared intent
        ↓
Calling Graph extraction and change localization
        ↓
UTN / structural address resolution
        ↓
WE/Object identity, state, and perspective binding
        ↓
Multi-graph expansion (data, control, policy, test, deploy)
        ↓
ODK qualified differential and impact candidates
        ↓
CDE candidate changes and constraint checks
        ↓
Evidence review → authorization → controlled promotion
        ↓
Deployment monitoring → feedback → possible relay
```

UTN provides a potential shared structural localization interface, not a magical conversion of call edges into semantic facts. SIF localization can rank problem regions and required capabilities; WE-HDT/MDT may supply alternative differential/hierarchical search. OCSRE integrates their *qualified results* through typed Object interfaces. An unresolved mapping MUST remain unresolved rather than being coerced into a unique identity.

## 8. Object Differential Kernel and impact evaluation

For a code object `o`, define a metric projection under perspective `p` and revision `r`:

\[
M(o,p,r) = [m_{interface},m_{effects},m_{policy},m_{tests},m_{dependencies},m_{uncertainty}]
\]

Each component has a type, source, time/build scope, interpretation, and admissible comparison operator. These components are **not** automatically commensurable, and their numerical aggregation is optional and policy-governed.

An ODK evaluation follows **Resolve → Project → Align → Evaluate → Qualify → Trace**:

- **Resolve:** bind changed symbols to versioned code objects and declared build variants.
- **Project:** extract typed properties (e.g., cache-key fields, policy dependencies, call edges).
- **Align:** verify same semantic interpretation, source/build context, and comparator contract.
- **Evaluate:** compute diffs, risk flags, or bounded impact scores.
- **Qualify:** attach missing coverage, ambiguity, and unresolved dependencies.
- **Trace:** preserve the chain from change to source evidence, plugin version, and conclusion.

Example: `calling_edge_delta = 0` and `authorization_context_fields_removed = 4` are not contradictory. They are results from different perspectives; the latter can trigger a security block even if the former is zero.

**Scoring boundary:** an impact score is neither a deductive proof of defect nor a safety certificate. Hard policy invariants MUST NOT be overridden by a favorable aggregate score.

## 9. WE-native composite CDE State-Container

A software change is typically composite: it spans code objects, tests, schemas, policies, and deployment settings. A candidate State-Container might be:

```yaml
StateContainer:
  container_id: code-change-CASE006-001
  owner: repository-maintainer-policy
  baseline_revision: rev-base-001
  included_objects:
    - code-we://example/repo/authz/check_permission
    - code-we://example/repo/tests/test_authz
    - code-we://example/repo/policies/tenant_boundary
  relation_sets: [calls, reads, controls, protects, tested_by]
  constraints:
    - preserve_tenant_isolation
    - preserve_resource_and_action_scope
    - respect_policy_revision_and_revocation
    - maintain_required_test_and_review_gates
  allowed_mutations: [source_patch, test_patch, policy_review_request]
  forbidden_implicit_effects: [production_deployment, permission_grant]
```

This container is a working evolution boundary, not a claim that all listed items are one real-world WE.

### 9.1 Typed candidate Delta

```yaml
TypedDelta:
  delta_id: D-CASE006-001
  delta_type: ModifyFunctionBody
  target: code-we://example/repo/authz/check_permission
  baseline_revision: rev-base-001
  read_scope: [authz_policy, cache_configuration, tests]
  write_scope: [check_permission_source]
  intended_effect: reduce_repeated_policy_evaluations
  preconditions: [baseline_matches, analysis_permissions_valid]
  hard_constraints: [tenant_isolation, action_scope, revocation_freshness]
  required_evidence: [static_analysis, focused_tests, security_review]
  candidate_only: true
  promotion_authority: repository-maintainer-policy
```

The candidate is first applied in a sandbox; composite constraints are evaluated against the candidate state. **A valid local source edit may still violate global security or deployment invariants.** A Delta is not a commit, and a repository commit is not a production deployment.

## 10. Candidate generation and constrained search

CDE may generate alternative candidate Deltas, for example:

- **D1:** cache by the full authorization context and policy version, subject to revocation requirements.
- **D2:** cache only immutable intermediate computations, not authorization decisions.
- **D3:** use short-lived cache entries with explicit invalidation, if policy permits.
- **D4:** reject caching and optimize policy evaluation elsewhere.

These are candidates, not automatically safe solutions. Each must satisfy the same hard invariants and receiving-environment tests. Dynamic M→N branching can expand promising alternatives; NoSubtree can record infeasible branches; Loop-Back and path-memory policies prevent uncontrolled repetition of a Delta along a path under the declared CDE semantics. **Finite search or convergence is not guaranteed** without bounded state, branching, and termination conditions.

A candidate with better latency but unresolved tenant isolation MUST NOT be promoted. Candidate rejection should produce an explicit residual explaining the failed constraint and the evidence needed to reconsider it.

## 11. Security, permissions, and action boundaries

The governance workflow must distinguish:

1. Permission to **read** source, logs, and configuration.
2. Permission to **propose** changes.
3. Permission to **run** tests or sandbox actions.
4. Permission to **approve** changes.
5. Permission to **merge** into a protected branch.
6. Permission to **deploy** to an environment.
7. Permission to **roll back** or execute compensating actions.

These permissions are not interchangeable and MUST NOT be inherited merely because a plugin or agent was allowed to analyze the code. Source or log access can expose sensitive data; derived graph artifacts must retain access controls and redaction requirements. Untrusted repository comments, generated patches, and tool outputs are **data**, not instructions granting higher authority. A failed authorization check is a blocking condition, not a low-scoring metric.

Rollback of a source revision does not undo external effects of an earlier deployment, including messages emitted, data written, or access previously granted. Irreversible or externally visible actions require separately governed boundaries.

## 12. Evidence and epistemic promotion

| Artifact | Epistemic class | What it can support | What it cannot establish alone |
|---|---|---|---|
| Source diff | Observed repository artifact | Bytes changed at a revision | Behavioral correctness |
| Calling Graph | Tool-derived structural model | Potential call relationships in analyzed scope | Complete program behavior |
| Data-flow finding | Tool-derived inference | Candidate propagation path | Universal exploitability |
| Static analyzer warning | Qualified finding | Potential risk needing review | Confirmed defect in every execution |
| Unit test pass | Observed test result | Pass under test inputs/environment | Absence of other failures |
| Property/security test | Observed bounded result | Invariant for exercised/model-checked scope | Unbounded real-world safety |
| Human review approval | Authorization record | Approval under declared policy | Successful deployment outcome |
| Deployment telemetry | Observed operational evidence | Measured behavior in observed window | Complete future safety |

The system must retain provenance, analyzer versions, build scope, counterevidence, and missing coverage. Conflicting findings should be represented as conflicts, not silently resolved by averaging confidence values. **Propose ≠ analyze ≠ validate ≠ authorize ≠ deploy ≠ observe.**

## 13. Test selection and validation targeting

The initial impact set can be formed from the changed object and relevant reverse dependencies in the Calling Graph, then expanded by data/control/policy/schema/deployment dependencies. Test selection should combine structural coverage with explicit requirements and risk-oriented tests. A small selected test set may improve efficiency but must not substitute for mandatory repository-wide gates.

For the synthetic cache example, a minimum proposed validation matrix includes:

| Test ID | Scenario | Expected result |
|---|---|---|
| CG-01 | Existing call edges unchanged | Graph-diff-only signal may be empty; no safety claim |
| AUTH-01 | Same user and same authorized scope | Correct allow/deny result |
| AUTH-02 | Same user across two tenants | No cross-tenant authorization reuse |
| AUTH-03 | Same user across resources | Resource-specific authorization enforced |
| AUTH-04 | Same user across actions | Action-specific authorization enforced |
| AUTH-05 | Policy version changes | Old decision not reused contrary to policy |
| AUTH-06 | Revocation during cache lifetime | Freshness/invalidation contract enforced |
| CFG-01 | Alternate build or feature flag | Coverage gap surfaced or separately validated |
| TEST-01 | Missing integration tests | Incomplete coverage explicitly recorded |
| DEP-01 | Deployment permission absent | Deployment blocked despite passing tests |

No table entry is an executed result. Real evaluation must preserve test code, fixtures, expected and observed outputs, analyzer configuration, and artifact hashes.

## 14. Proposed conformance obligations (ACG-001–ACG-022)

The following identifiers are **local to CASE-006**. They are proposed case-level checks; normative project-wide requirements remain in SPEC-001–006.

| ID | Requirement |
|---|---|
| ACG-001 | Distinguish source locations, graph addresses, WE identities, and action authorities. |
| ACG-002 | Bind each analysis to repository revision and build configuration. |
| ACG-003 | Record Calling Graph extraction coverage and unresolved dynamic edges. |
| ACG-004 | Do not treat call reachability as proof of execution or impact. |
| ACG-005 | Include data/control/config/schema/policy/deployment dependencies as applicable. |
| ACG-006 | Declare the provenance and version of each dependency edge. |
| ACG-007 | Preserve temporal and version scope when comparing code objects. |
| ACG-008 | Enforce typed ODK alignment before metric comparison. |
| ACG-009 | Separate impact scores from proofs and authorization. |
| ACG-010 | Preserve plugin effect and permission boundaries in compositions. |
| ACG-011 | Record unresolved dependencies as explicit residuals. |
| ACG-012 | Declare candidate Delta read/write scope and preconditions. |
| ACG-013 | Check composite constraints, not only local syntax or unit tests. |
| ACG-014 | Block promotion on unresolved mandatory security invariants. |
| ACG-015 | Enforce baseline version checks and conflict handling. |
| ACG-016 | Separate proposal, sandbox, review, merge, deployment, and observation. |
| ACG-017 | Keep sensitive code and derived evidence within authorized access scope. |
| ACG-018 | Do not treat rollback of code as reversal of external effects. |
| ACG-019 | Maintain negative and adversarial tests, including cross-tenant cases. |
| ACG-020 | Record test-selection recall/coverage and false-negative evidence. |
| ACG-021 | Require receiving-project conformance before capability relay promotion. |
| ACG-022 | Record measured benefit, cost, failures, and negative transfer. |

## 15. Positive reference tests (proposed)

| ID | Fixture | Expected check |
|---|---|---|
| P-01 | One statically resolved direct call | Edge and provenance preserved |
| P-02 | Function renamed without behavior change | Identity/address ambiguity handled explicitly |
| P-03 | One added direct call | Changed dependency localized |
| P-04 | One changed policy input | Policy-dependent test set expanded |
| P-05 | Same-tenant cache hit under valid freshness | Allowed only within policy scope |
| P-06 | Full-scope cache key under version change | Policy-version invalidation enforced |
| P-07 | Two candidate patches with different effects | Typed Delta effects compared separately |
| P-08 | Candidate fails hard invariant | Promotion blocked, residual recorded |
| P-09 | Reviewer approves validated sandbox candidate | Approval recorded without deployment claim |
| P-10 | Receiving project imports a validated analyzer plugin | Receiver-specific conformance required |
| P-11 | Test coverage includes changed policy contract | Trace from change to test evidence maintained |
| P-12 | Deployment observed after separate authorization | Operational feedback attributed to correct revision |

## 16. Negative and adversarial tests (proposed)

| ID | Counterexample / attack on inference | Required behavior |
|---|---|---|
| N-01 | Unchanged Calling Graph, changed authorization semantics | No false safety conclusion |
| N-02 | Reflection/dynamic dispatch missing from graph | Explicit coverage gap |
| N-03 | Async event consumer not represented as a call | Expand dependency perspective |
| N-04 | Data-flow dependency without call edge | Retain possible impact |
| N-05 | Feature flag changes control path | Version/config scope checked |
| N-06 | Database schema changed outside source diff | Cross-artifact dependency considered |
| N-07 | Symbol name collision across modules | No false identity merge |
| N-08 | Same symbol across revisions with changed semantics | Version-aware comparison |
| N-09 | Cached authorization leaks across tenants | Hard invariant rejects candidate |
| N-10 | Cache omits resource or action | Hard invariant rejects candidate |
| N-11 | Revoked permission remains cached | Reject unless explicit freshness contract satisfied |
| N-12 | Unit tests pass but security test fails | Promotion blocked |
| N-13 | Analyzer reports low risk with unknown coverage | Qualification preserved; no certification |
| N-14 | Plugin requests broader repository privileges | Permission denied or independently authorized |
| N-15 | Untrusted code comment asks agent to bypass checks | Treat as untrusted source content |
| N-16 | Stale baseline revision | Candidate rejected/rebased and revalidated |
| N-17 | Two agents modify same policy file | Conflict detection and review |
| N-18 | Favorable latency score but broken isolation | Constraint outranks score |
| N-19 | Source rollback after external data mutation | No claim of external reversal |
| N-20 | Passing tests in one build variant only | Other variants remain unvalidated |
| N-21 | Cross-project plugin assumes same auth semantics | Receiver-side rejection or adaptation |
| N-22 | Duplicate evidence counted as independent | Deduplicate or qualify dependence |
| N-23 | Missing audit trail for promotion | Reject or mark nonconformant |
| N-24 | Measured faster analysis but missed critical impact | Negative transfer / failure recorded |

## 17. Evaluation design and baselines

To test **OCSH-011**, compare at least three workflows on held-out, versioned change sets:

- **B0 — Standard baseline:** existing repository CI, type checking, security checks, and conventional change review.
- **B1 — Calling Graph baseline:** B0 plus call-graph-based impact selection.
- **B2 — OCSRE candidate:** B1 plus typed WE/UTN localization, multi-graph dependencies, ODK qualification, and CDE governance.

Where feasible, include an ablation **B2-minus-CDE** or **B2-minus-UTN** to estimate which component contributes measurable value. All baselines must have comparable permissions, build environments, time budgets, and access to source evidence.

**Primary measures:** recall of independently adjudicated impacted objects, recall of security-relevant impact paths, false-negative rate, validation-targeting precision, change-to-test trace completeness, and number/severity of missed hard constraints.

**Secondary measures:** analysis latency, compute cost, review burden, integration cost, portability across repositories/languages, and false-positive volume. Report confidence intervals and uncertainty when sample sizes permit. Define critical-risk acceptance thresholds before evaluation; never trade away a critical security miss for a better aggregate average.

**Ground truth limits:** true impact sets are difficult to enumerate. Use seeded defects, instrumented execution, differential testing, expert adjudication, and documented unknowns rather than claiming complete ground truth from one analyzer.

A credible positive result would show improvement on held-out tasks at acceptable cost without degrading hard safety gates. A null or negative result is an important research outcome.

## 18. Relay and collective learning experiment

A validated code-governance capability can be packaged as a versioned plugin with its language/runtime scope, dependency extraction policy, permission needs, evidence format, test fixtures, known blind spots, and performance results. A receiving project must repeat conformance checks under its own build, framework, security policy, and deployment topology.

Candidate relay tracks include (a) authorization-impact localization from a web service to a batch-processing system, (b) schema-impact detection from SQL adaptation to API compatibility analysis, and (c) composite constraint checks from scheduling to deployment orchestration. These are **structural analogies to test**, not evidence of automatic semantic transfer.

A multi-agent workflow may assign independent roles to change proposer, dependency analyzer, security reviewer, test selector, and evidence auditor. Agent agreement is not independent evidence if all agents share the same incomplete graph or test suite. Collective Learning should preserve both successes and **Explicit Leftovers**, including failed transfers and missed dependencies.

## 19. Hypothesis traceability

| Hypothesis | Case-specific testable implication | Status |
|---|---|---|
| OCSH-002 | ODK kernel unchanged across distinct code-analysis plugins | Proposed / E0 |
| OCSH-003 | Contract-bound plugins reduce adaptation effort versus baseline | Proposed / E0 |
| OCSH-004 | Feedback linked to revision/object improves traceability | Proposed / E0 |
| OCSH-005 | Composite code-state candidates obey shared CDE contracts | Proposed / E0 |
| OCSH-006 | Explicit code granularity avoids invalid function→service inference | Proposed / E0 |
| OCSH-008 | Receiver-validated code-analysis relay improves held-out tasks | Proposed / E0 |
| OCSH-009 | New governance capability helps an untargeted task | Proposed / E0 |
| OCSH-010 | Repeated validated relay sustains capability growth | Proposed / E0; requires longitudinal study |
| **OCSH-011** | **Impact localization, validation targeting, or traceability improves across projects** | **Primary hypothesis; Proposed / E0** |

OCSH-001 and OCSH-007 remain relevant as logical and SQL-adaptation dependencies but are not directly established by this case. The entire table records proposed tests, not empirical support.

## 20. Explicit leftovers

1. Define stable WE identity policies for refactored, generated, and dynamically loaded code.
2. Specify precise UTN-to-code-object mappings for multiple languages.
3. Compare Calling Graph extraction precision and recall across analyzers.
4. Formalize multi-graph join semantics and edge uncertainty propagation.
5. Bound the soundness claims possible under reflection and runtime code generation.
6. Define cross-service event and asynchronous dependency contracts.
7. Incorporate database, schema, policy, and infrastructure drift reliably.
8. Develop a principled treatment of code-object granularity and aggregation.
9. Establish acceptable confidence/uncertainty semantics for risk ranking.
10. Determine how to reconcile conflicting static and dynamic evidence.
11. Define security-critical hard invariants across diverse repositories.
12. Develop robust authorization-cache and policy-revocation test fixtures.
13. Evaluate graph-based test selection against existing regression strategies.
14. Quantify true impacted-object recall when ground truth is incomplete.
15. Establish reproducible datasets and seeded-change benchmarks.
16. Measure analyzer integration and maintenance costs.
17. Explore bounded CDE search strategies and termination policies.
18. Specify multi-agent conflict resolution and evidence independence tests.
19. Formalize rollback and compensation for externally visible deployments.
20. Evaluate portability across languages, build systems, and organizations.
21. Measure privacy leakage from derived graph and trace artifacts.
22. Test adversarial source comments and malicious plugin outputs as untrusted data.
23. Develop controlled experiments for negative capability transfer.
24. Assess whether repeated validated relay produces durable, untargeted spillover.

Unresolved items must be retained in `research-trace/UNRESOLVED-RESIDUALS.md` and linked to `research-trace/COUNTEREXAMPLE-REGISTRY.md` as the repository matures; these paths denote planned assets, not claims that those files already contain entries.

## 21. Suggested reproducibility package

A future implementation should publish: (1) a small synthetic repository with baseline and candidate revisions; (2) language/build configuration; (3) Calling Graph and additional dependency extraction outputs; (4) UTN/WE mapping tables; (5) ODK metric and comparator schemas; (6) candidate Typed Deltas and validation logs; (7) positive/negative tests; (8) reviewer decision records; (9) evaluation scripts and baseline results; and (10) limitations and unresolved residuals. Sensitive operational repositories should not be required for the initial benchmark.

**Proposed execution order:** contract validation → fixture validation → baseline runs → candidate runs → negative/adversarial runs → ablations → independent adjudication → receiver-side relay trials → reporting. No runtime or benchmark result is bundled with this research text.

## 22. Conclusion

AI-generated code governance is a compelling test of OCSRE because the relevant intelligence problem is not just generating a patch: it is locating its affected objects, understanding heterogeneous dependencies, checking composite constraints, preserving evidence and authority, and learning from outcomes. The proposed **Calling Graph → UTN → OCSRE** path is valuable as an *integration architecture*, provided it does not reduce program behavior to call edges or convert a risk score into permission to act. ODK offers typed comparisons; CDE offers constrained candidate evolution; SIF and localization mechanisms can organize search; Object Plugins and UIERU-style relay may enable reuse. The scientific claim remains conditional until independently evaluated: **better structured governance must be demonstrated through fewer missed impacts, stronger traceability, and defensible validation costs, not assumed from architectural elegance**.

---

**Repository placement:** `cases/CASE-006-AI-Generated-Code-Governance-Through-Calling-Graphs-and-CDE.md`  
**Principal hypothesis:** OCSH-011  
**Supporting hypotheses:** OCSH-002, OCSH-003, OCSH-004, OCSH-005, OCSH-006, OCSH-008, OCSH-009, OCSH-010  
**Research posture:** Specifications/Contracts First · Conformance Before Runtime · Explicit Leftover  
**Evidence status:** E0 / Proposed
