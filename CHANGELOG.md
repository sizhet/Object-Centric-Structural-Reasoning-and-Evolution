# Changelog — Object-Centric Structural Reasoning and Evolution (OCSRE)

**Repository:** `Object-Centric-Structural-Reasoning-and-Evolution`  
**Release track:** `v1.0.0 — Research Framework and Contracts`  
**Authors (proposed):** Sizhe Tan & GPT-Obot  
**License:** Apache-2.0 (repository licensing to be checked at release)  
**Document status:** Draft release history; **no GitHub release, DOI, Zenodo deposit, implementation, or validation is asserted by this document**.  
**Last updated:** 2026-11-23 (document preparation; not a release timestamp)

This changelog records the **research assets and conceptual baseline** prepared for the first OCSRE repository release. It distinguishes *authored*, *planned*, *released*, and *validated* work. A filename listed here denotes a proposed or drafted research artifact, not an executable implementation or empirical result.

## Version policy and evidence semantics

- **`[Unreleased]`** tracks material being prepared or reviewed. Until an actual tagged release exists, the v1.0.0 contents below are a **release candidate**, not a published release.
- **`v1.0.0`** is intended to identify a stable **research framework and contracts** baseline; it is not a claim of production readiness, API stability across future implementations, or experimental confirmation.
- **Documentation status** and **hypothesis evidence status** are independent. A completed specification or test plan does not promote a hypothesis beyond **E0 — Proposed**.
- Later changes should be recorded under **Added**, **Changed**, **Clarified**, **Deprecated**, **Removed**, **Fixed**, **Security**, and **Evidence** as applicable. Do not silently rewrite past release entries.
- Dates of future releases, repository tags, Zenodo records, and DOIs must be populated from actual publication records, not estimated.

## [Unreleased] — v1.0.0 research-framework candidate

### Added — foundational research papers (`docs/`)

Twelve papers define the proposed architecture and its boundaries:

1. [`OCSRE-001`](docs/OCSRE-001-The-Object-Centric-Structural-Intelligence-Thesis.md) — the object-centric structural intelligence thesis and its relationship to representation, computation, reasoning, learning, and evolution.
2. [`OCSRE-002`](docs/OCSRE-002-From-Classical-Syllogism-to-Object-Centric-Structural-Reasoning.md) — a bounded route from classical syllogism to typed object-centric inference, without claiming unrestricted logical equivalence.
3. [`OCSRE-003`](docs/OCSRE-003-Dynamic-Relational-and-Multi-Granular-Reasoning.md) — perspectives, time, relation types, and granularity-aware reasoning.
4. [`OCSRE-004`](docs/OCSRE-004-Object-Differential-Kernel-and-Generic-Operators.md) — a proposed domain-neutral Object Differential Kernel (ODK) and comparator/operator surfaces.
5. [`OCSRE-005`](docs/OCSRE-005-Object-Plugins-and-Composable-Intelligence-Capabilities.md) — contract-governed plugin composition and compatibility.
6. [`OCSRE-006`](docs/OCSRE-006-SQL-to-Object-Attribute-Transformation-and-Semantic-Alignment.md) — SQL-to-WE semantic adaptation, including grain, NULL, provenance, and authorization boundaries.
7. [`OCSRE-007`](docs/OCSRE-007-In-Situ-Object-Learning-Decision-and-Feedback.md) — object-local learning and feedback with evidence traceability.
8. [`OCSRE-008`](docs/OCSRE-008-WE-Native-CDE-and-Composite-State-Evolution.md) — WE-native Constrained Delta Evolution (CDE), typed deltas, and composite State-Containers.
9. [`OCSRE-009`](docs/OCSRE-009-Epistemic-Separation-and-Object-Centric-Evidence-Governance.md) — explicit separation of observation, inference, score, decision, and action authorization.
10. [`OCSRE-010`](docs/OCSRE-010-UTN-WE-HDT-and-SIF-Localization-Through-Shared-Object-Interfaces.md) — typed interfaces among UTN, WE-HDT, and SIF localization mechanisms.
11. [`OCSRE-011`](docs/OCSRE-011-Object-Capability-Spillover-Relay-and-Collective-Structural-Learning.md) — capability relay, structural spillover, and collective learning as hypotheses requiring target-domain evidence.
12. [`OCSRE-012`](docs/OCSRE-012-Open-Ended-Object-Centric-Structural-Intelligence.md) — open-ended metric, plugin, policy, and capability evolution; scaling remains unproven.

### Added — specification baseline (`specs/`)

Six proposed, scope-limited research contracts:

- [`SPEC-001`](specs/SPEC-001-Object-Identity-Perspective-and-State-Contract.md) — identity, perspective, state, and reference semantics.
- [`SPEC-002`](specs/SPEC-002-Object-Differential-Kernel-and-Comparator-Contract.md) — ODK comparators, typed metrics, and rejection behavior.
- [`SPEC-003`](specs/SPEC-003-Classical-Reasoning-Preservation-and-Granularity-Contract.md) — restricted deductive preservation and cross-granularity safeguards.
- [`SPEC-004`](specs/SPEC-004-Object-Plugin-and-Capability-Composition-Contract.md) — plugin contracts and capability composition.
- [`SPEC-005`](specs/SPEC-005-In-Situ-Learning-Feedback-and-Epistemic-Governance-Contract.md) — feedback, evidence, and epistemic governance.
- [`SPEC-006`](specs/SPEC-006-WE-Native-CDE-Composite-State-and-Relay-Contract.md) — composite-state transitions, CDE, and relay obligations.

**Normative scope:** these are proposed contracts for OCSRE; they do not certify third-party systems or supersede the semantics of WE-SIO, UTN, MDT, WE-HDT, SIF, CDE, or UIERU.

### Added — bounded application and adversarial cases (`cases/`)

- [`CASE-001`](cases/CASE-001-Person-and-Classical-Reasoning.md) — person/classical inference and restricted reasoning.
- [`CASE-002`](cases/CASE-002-SQL-Native-Object-Adaptation.md) — relational data and object adaptation.
- [`CASE-003`](cases/CASE-003-School-Bus-Scheduling-and-Composite-WE-State.md) — school-bus scheduling and globally constrained composite states.
- [`CASE-004`](cases/CASE-004-Transaction-and-Compositional-Identity.md) — transaction traces and compositional identity as uncertain inference.
- [`CASE-005`](cases/CASE-005-Cross-Domain-Object-Plugin-Relay.md) — target-domain conformance for cross-domain plugin relay.
- [`CASE-006`](cases/CASE-006-AI-Generated-Code-Governance-Through-Calling-Graphs-and-CDE.md) — Calling Graph → UTN → OCSRE, change-impact analysis, and governed candidate evolution.

These cases are **illustrative research fixtures**, not records of deployed systems, successful experiments, security certification, or real-world identity attribution.

### Added — research extensions (`extensions/`)

- [`EXT-001`](extensions/EXT-001-Object-Centric-Reasoning-and-the-History-of-Logic.md) — historical and formal-logic connections.
- [`EXT-002`](extensions/EXT-002-Object-Centric-SIF-Localization-and-Addressing.md) — referential versus evolutionary localization, including CDE's proposed SIF role.
- [`EXT-003`](extensions/EXT-003-Multi-Agent-Object-Intelligence-and-Relay.md) — multi-agent coordination and evidence independence.
- [`EXT-004`](extensions/EXT-004-Open-Ended-Metric-Plugin-and-Policy-Evolution.md) — separately governed evolution of metrics, plugins, and policies.
- [`EXT-005`](extensions/EXT-005-Structural-Capability-Spillover-and-Scaling-Hypotheses.md) — testable spillover and scaling hypotheses, without asserting a Scaling Law.

### Added — research-trace governance (`research-trace/`)

- [`HYPOTHESIS-REGISTRY.md`](research-trace/HYPOTHESIS-REGISTRY.md) — **OCSH-001–OCSH-011**, all **E0 — Proposed**.
- [`DEFINITION-REGISTRY.md`](research-trace/DEFINITION-REGISTRY.md) — stable definitions and non-equivalence boundaries.
- [`COUNTEREXAMPLE-REGISTRY.md`](research-trace/COUNTEREXAMPLE-REGISTRY.md) — negative and adversarial fixtures.
- [`DECISION-LOG.md`](research-trace/DECISION-LOG.md) — architecture decisions and reconsideration triggers.
- [`UNRESOLVED-RESIDUALS.md`](research-trace/UNRESOLVED-RESIDUALS.md) — explicit research gaps and proposed closure conditions.

### Added — eight conceptual figures (`figures/`)

- `Fig-001-OCSRE-Grand-Architecture.png`
- `Fig-002-From-Classical-Syllogism-to-Object-Centric-Reasoning.png`
- `Fig-003-Object-Metric-Perspective-and-State.png`
- `Fig-004-Object-Differential-Kernel-and-Plugin-Interfaces.png`
- `Fig-005-SQL-to-WE-Attribute-Transformation.png`
- `Fig-006-In-Situ-Object-Intelligence-Loop.png`
- `Fig-007-WE-Native-CDE-and-Composite-State-Evolution.png`
- `Fig-008-Object-Capability-Spillover-Relay-and-Collective-Learning.png`

See [`FIGURE-INDEX.md`](FIGURE-INDEX.md) for insertion guidance. The figures are conceptual aids, **not** experimental evidence.

### Added — reader navigation and future research

- [`README.md`](README.md), [`START-HERE.md`](START-HERE.md), [`CONTENTS.md`](CONTENTS.md) — thesis, reading routes, and repository inventory.
- [`GLOSSARY.md`](GLOSSARY.md), [`FIGURE-INDEX.md`](FIGURE-INDEX.md) — reader-facing terminology and figure navigation.
- [`FUTURE-DIRECTIONS.md`](FUTURE-DIRECTIONS.md), [`OPEN-QUESTIONS.md`](OPEN-QUESTIONS.md) — proposed research agenda and open questions.
- [`TESTABLE-HYPOTHESES.md`](TESTABLE-HYPOTHESES.md), [`VALIDATION-ROADMAP.md`](VALIDATION-ROADMAP.md) — falsifiable protocols, staged conformance gates, and evidence-promotion requirements.
- `CHANGELOG.md` — this release-history draft.

### Clarified — architectural boundaries

- **Object identity is not storage-key equality, representation similarity, or a proven actor identity.**
- **ODK differential is not a CDE typed state delta.** Comparisons and executable transition proposals have different semantics.
- **Classical inference preservation is scoped to a restricted fragment**, not unrestricted nonmonotonic, probabilistic, or temporal reasoning.
- **SQL-to-WE adaptation is not row wrapping**; NULL/three-valued logic, aggregation grain, provenance, and access policy require explicit treatment.
- **A CDE candidate is not a committed or authorized action**; global State-Container constraints and independent authorization remain necessary.
- **SIF referential localization and CDE evolutionary localization are complementary**, not interchangeable search procedures.
- **Multi-agent agreement is not independent validation**; relay requires receiving-domain conformance and negative-transfer accounting.
- **Capability reuse, transfer, spillover, and scaling are separate claims.** A conceptual growth mechanism does not establish a scaling law.
- **Calling Graph localization alone is insufficient for AI-generated-code governance**; data/control flows, contracts, effects, and authorization must also be considered.

### Evidence — current baseline

| Item | Status at this draft |
|---|---|
| Core hypotheses OCSH-001–OCSH-011 | **E0 — Proposed** |
| Formal conformance proofs | Not claimed |
| Executed benchmark studies | Not claimed |
| Independent replications | Not claimed |
| Deployed ODK / CDE / plugin runtime | Not claimed |
| Verified cross-domain capability spillover | Not claimed |
| Sustained structural Scaling Law | Not claimed |
| Published GitHub v1.0.0 release | To be verified at publication |
| Zenodo DOI | To be assigned, if deposited |

### Pending — publication metadata and release assets

The following are **not marked completed by this changelog** until their files and contents are checked:

- `CITATION.cff` — author identity, repository URL, version, and optional DOI after assignment.
- `.zenodo.json` — deposit metadata consistent with `CITATION.cff` and the actual release.
- `LICENSE` — complete Apache-2.0 license text and any needed notices.
- `release/GitHub-Release-Notes-v1.0.0.md` — actual release-facing summary and evidence limitations.
- `release/ResearchGate-Description.txt` and `release/OCSRE-v1.0.0-ResearchGate-Overview.pdf` — public descriptions and verified links.

## Release acceptance checklist — v1.0.0

- [ ] Assemble `docs/`, `specs/`, `cases/`, `extensions/`, `research-trace/`, `figures/`, and `release/` under the canonical directory names.
- [ ] Verify every relative Markdown link and all eight image paths against the assembled repository.
- [ ] Confirm stable identifiers (OCSRE, SPEC, CASE, EXT, OCSH, definitions, ADRs, and residuals) and terminology across files.
- [ ] Resolve or explicitly record conflicting contract statements; do not conceal them by changing a summary.
- [ ] Confirm that conceptual diagrams are legible and are not represented as measurements.
- [ ] Verify author credits, repository URL, license, citation metadata, and Zenodo metadata.
- [ ] Check that no unpublished DOI, release date, validation result, benchmark, or implementation is asserted as fact.
- [ ] Complete release notes and publication descriptions after metadata checks.
- [ ] Create the actual Git tag / GitHub release; record its verified date and URL in a subsequent changelog update.
- [ ] Record the DOI only after a successful deposit; check that it resolves to the intended version.

## Future changelog entry template

```markdown
## [vX.Y.Z] — YYYY-MM-DD

**Release URL:** <verified link>
**DOI:** <verified DOI or 'not assigned'>

### Added
- <new research artifacts or contracts>

### Changed
- <scope and compatibility impacts>

### Clarified
- <semantic boundary or interpretation>

### Fixed
- <documented correction with affected files>

### Evidence
- <executed studies, artifacts, replication and bounded claim changes>

### Known limitations / Explicit leftovers
- <unresolved items and cross-references>
```

**History integrity rule:** Future releases should preserve this original research baseline and link material revisions to [`research-trace/DECISION-LOG.md`](research-trace/DECISION-LOG.md), [`research-trace/HYPOTHESIS-REGISTRY.md`](research-trace/HYPOTHESIS-REGISTRY.md), and [`research-trace/UNRESOLVED-RESIDUALS.md`](research-trace/UNRESOLVED-RESIDUALS.md). A revision to a hypothesis's evidence status requires actual evidence; a revision to an interface contract requires explicit compatibility analysis.
