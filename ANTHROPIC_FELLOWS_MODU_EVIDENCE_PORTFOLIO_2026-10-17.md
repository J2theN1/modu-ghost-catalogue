# MODU — Independent AI Research & Engineering Portfolio
Date: 2026-10-17
Purpose: Evidence-grounded support for Anthropic AI Safety & Security Fellows and adjacent programs.
Status: Draft for applicant review; not an application submitted to Anthropic. Public copy: deployment identifiers, receipt details, and network-exposure status redacted; the private source document is unchanged.

## Applicant and operating context

Founder directing MODU, an independent local-first, AI-assisted agent/research/engineering ecosystem spanning multiple years, while operating real businesses and developing real-world AI workflows. Applicant reports approximately two years of independent work and substantial weekly time commitment. The contribution is architectural direction, interdisciplinary systems design, operational diagnosis, managing AI coding agents, defining outcomes, judging evidence, prioritizing repairs and supervising deployment. **Not fluent in Python and does not claim to have manually authored most code.**

MODU spans procedural language/cognition, distributed agents, persistent memory, typed capabilities, independent task verification, desktop and phone control, mathematical discovery, scientific computing, radio/embedded experimentation, games/simulation and business operations. This breadth is an opportunity for cross-domain testing, but does **not** imply all projects are live, independently evaluated or novel.

## Thesis suitable for a fellowship

AI coding agents and autonomous workflows often mistake their own proximal progress signals (compiled artifact, successful tool response, service health, model-completion label) for verified achievement of the intended task. MODU's repeated cross-domain failures motivated stronger separation between intent, authorization, execution, independent observation, validated outcome, and evidence-informed learning. A useful empirical project could study the prevalence and mitigation of these failure classes in realistic long-horizon workflows.

## Case 1 — Agent false-completion correction

Historical Creator Loop v2 completed missions after generic code drafts compiled. Dated recovery documents describe an actual correction of five missions from `done` to `ready_review`, with observed post-state. Follow-up metrics still showed 16.67% validation-rule coverage and 20 completed missions without explicit validation rules. Thus a truthful case includes both successful reclassification **and remaining systemic validation debt**.

Evidence:
- [Legacy false-done correction](https://github.com/J2theN1/pc-github-index/blob/main/audits/pcore/PCORE_LEGACY_FALSE_DONE_CORRECTION_2026-08-30.md)
- [Legacy Autopilot/Creator handoff](https://github.com/J2theN1/pc-github-index/blob/main/audits/pcore/PCORE_LEGACY_AUTOPILOT_MEMORY_AND_CREATOR_HANDOFF_2026-08-30.md)

Candidate evaluation: replay a fixed task corpus under three acceptance policies: model self-report; compile/process exit check; independently declared semantic postconditions. Measure false-success rate, missed success, human review cost, and repeat-action error rates.

## Case 2 — Persistent multi-agent coordination

July 2026 owner-stack and hive audits recorded competing workers/queues, duplicate work, identity drift and service readiness misalignment. Later source documents define a canonical execution authority, idempotent resource leases/fencing, and terminal receipts. One should not claim every end-to-end workflow is now flawless or contemporaneously deployed.

Evidence:
- [Hive live audit addendum](https://github.com/J2theN1/modu-agent-workspace/blob/main/docs/superpowers/specs/2026-07-27-ai-team-worker-control-layer-live-audit-addendum.md)
- [Current workspace authority boundary](https://github.com/J2theN1/modu-agent-workspace/blob/main/README.md)
- [Canonical state snapshot](https://github.com/J2theN1/pc-github-index/blob/main/docs/architecture/MODU_CURRENT_CANONICAL_STATE_20260929.md)

Candidate evaluation: controlled overlapping agent workloads on shared resources, with crash/replay and competing-client conditions; compare naive queuing, worker-local coordination and canonical leased task control against duplicate side effects and verified completions.

## Case 3 — Separate model failures from surrounding infrastructure

July 30 historical quality-log investigation examined 11,750 records and filtered 85 non-benchmark/non-probe failures (73 distinct prompts). Of those distinct prompts, 44 failed within 0.5s (consistent with upstream errors) and 29 took longer (model participation plausible but not proven as cause). The log did not retain responses, so it could not support naïve DPO chosen/rejected mining. A GRPO prototype was smoke-tested but full GRPO run not performed.

Evidence:
- [GRPO design and production-log investigation](https://github.com/J2theN1/modu-agent-v2/blob/main/docs/superpowers/specs/2026-07-30-grpo-weight-retrain-design.md)

Candidate evaluation: trace-classify failures across interface, tools, execution, verification and model decisions; compare interventions at each level, with explicit false-attribution and contamination measurements.

## Additional independent directions

1. Grounded procedural language (L0–L3), referents, operations and language-use traces: [procedural language theory](https://github.com/J2theN1/modu-pkg-jason/blob/main/docs/MODU_PROCEDURAL_LANGUAGE.md). Distinguish vision from demonstrated autonomous language learning.
2. Exact mathematical/computational verification: [automata lab](https://github.com/J2theN1/pc-github-index/blob/main/docs/math-vm/AUTOMATA_DISCOVERY_LAB.md) reports all 256 elementary rules matched fixed scalar/Torch CPU/CUDA trajectories, with corrupt-backend negative test; not a universal CUDA performance claim.
3. Mathematical historical archive: [math refinery](https://github.com/J2theN1/pc-github-index/blob/main/research/math-discovery/LEGACY_MATH_REFINERY_20260810.md) safely grades 260 historical inventions; historical perfect scores are not mathematical novelty.
4. Deterministic capability invention: [P-Core Fabric](https://github.com/J2theN1/pcore-fabric) composes tested primitives and matches gaps to known-answer-verified worker templates; example-input execution alone does not prove general mathematical correctness.
5. Simulated agent worlds: [WW2 Poland 1939](https://github.com/J2theN1/ww2_poland_1939) includes NPC/faction/morale/squad systems and a USS character adapter, with documented recovery tests. Integration and generalization need independent tests.
6. Physical systems and sensing: [RF lab](https://github.com/J2theN1/modu-rf-lab), [Muse Athena lab](https://github.com/J2theN1/muse-athena-lab); evidence varies from source tools and bounded query-only probes to pending live commissioning.
7. Business testbeds: procurement accounts, supplier offers, executive secretary and paper trading; real operational context is useful for studying dependable agents, but commercial success or financial profitability must be evidenced separately. Do not disclose personal or customer secrets.

## Why this is not a standard novice application

This applicant has spent substantial time directing an operationally grounded, multi-generation AI-assisted engineering/research effort. The work generated real failure cases, corrections, persistent infrastructure, empirical records and cross-domain hypotheses, while the applicant's conventional code-writing proficiency remains limited. The contribution to evaluate is methodological and systems judgment, not falsely asserted traditional code authorship.

## Fellowship constraints (verified against the Oct 17, 2026 listing)

- [Anthropic Fellows Program application](https://job-boards.greenhouse.io/anthropic/jobs/5183044008): January cohort deadline Oct 18, 2026; 4 months full-time; Canadian remote eligible; Python fluency explicitly required; apply even if not meeting every qualification is encouraged.
- Fit hypotheses: scalable oversight, agent control and AI security evaluation. Do not imply research area assignment or acceptance.
- Human applicant must make truthful availability, work-authorization, coding proficiency and reference disclosures.

## Source/claims policy

Never turn design-only work into deployed functionality; reported receipts into independently inspected receipts; GitHub metadata into first invention dates; commercial activity into revenue; or AI-generated code into manually authored code. Separate incident, observation, implemented intervention, acceptance test, and current live state.

## Next documentary priorities

Recover exact dates of earliest NOVA/MODU work, independently assess receipts for recent deployments, locate original project decision records, identify three fully replayable controls/case study fixture sets, and prepare a privacy-reviewed public excerpt rather than publish internal business/account details.

## Critical submission correction — verified 2026-10-17

Anthropic's official Greenhouse posting states: **Complete the Constellation application form; submitting the Greenhouse job form is not necessary and does not count as a complete application.** Official posting: https://job-boards.greenhouse.io/anthropic/jobs/5183044008 . Its `apply here by October 18` link goes through `https://bit.ly/afpsafety` and redirects to Constellation's Airtable form: https://airtable.com/appceerp9YQRlwDhU/pagW63dilE5oV7cPY/form . Tool browser could not open the form directly, so its internal fields, present accessibility and submission state are **not inspected or confirmed**. The applicant must complete that form. The official page also states 4-month full-time commitment, Python fluency, remote participation in Canada, and case-by-case consideration of availability constraints. Do not misstate that a portfolio document constitutes submitting the application.

## Supplemental candidate case study — persistent-world simulation as bounded agent evaluation

Cross-repository inspection located the actual legacy WW2 simulation test functions `test_encounter_receipts_reload_after_restart` and `test_encounter_cascades_casualty_into_medical_morale_history_and_retreat` in `J2theN1/ww2_poland_1939/tests/test_tactical_encounter_system.py`, and `test_repeated_suppression_uses_current_morale_to_trigger_retreat` in `tests/test_combat_suppression_retreat.py`. Together these source fixtures make it possible to design tests where an agent's actions cause durable changes to health, morale, unit relationships and simulation state, including recovery after restart. USS character mapping also exists in `game/mechanics/uss_character_representation.py` but degrades gracefully if the USS engine is absent; integrated USS cognition is not yet established by these fixtures. **We inspected repository code/test names but did not rerun these tests this session.**

An attractive fourth research study: compare agent self-reported completion with deterministic world-state postconditions, then introduce restarts, conflicting actors and corrupted/missing observations. Measure discrepancy between narrated success and stable downstream state. This is a proposal, not an existing published benchmark. Keep distinct from commercial release of the game.

## Form-access check 2026-10-17

Attempted direct read of the official Constellation Airtable page via a JavaScript-aware page extractor; it returned `empty_content`. The internal form questions remain unknown. Do not invent field labels, imply they were completed, or assume submission. The applicant can use the official Constellation link from Anthropic's listing.

## Case 5 — Failure Intelligence Fabric: evidence-bounded operational learning

`J2theN1/modu-agent-workspace/docs/failure-intelligence-v1.md` documents a deterministic Failure Intelligence Fabric supporting separate execution phases (preflight/startup/work/semantic receipt/persistence/readback/shutdown), conservative normalized signatures, and evidence-tiered lifecycle `unclassified -> under_investigation -> root_cause_proven -> remedy_proven`. Similarity matches are advisory only; exact, proven failures may be blocked by policy. Receipt semantics explicitly allow task outcome success and later shutdown failure to coexist. Historical Aug 18 census: 11,659 mined events, 6,745 failure signatures, 77 success signatures (6,822 unique); 12 roots, eight resolved, four unresolved, five truncated. Acceptance evidence cites run 32097981856 and receipt SHA-256 `9094fce0d9796dcaa9fa083dd0eb152dbd115873407933e71679b7f5b4fc0a55` testing replay idempotence, known-bad blocking, material-change reopen, known-good retrieval and cleanliness. Acceptance is **source-documented**, not newly rerun in this study.

Research direction: test whether an evidence-tiered procedural memory prevents expensive repeated failures more effectively than LLM summarization/vector retrieval alone, without false blocking after environmental changes. Evaluate recurrence, execution cost, overblocking, recoverability and regression.

## Distinct owner/institution interface research

`J2theN1/modu-agent-v2/docs/architecture/PRINCIPAL_FIRST_INSTITUTIONAL_INVERSION_20261012.md` documents a bounded legal-institutional access preflight prototype separating *owner-side authorization* from *issuer-side authority*. Its October 12 correction refuses self-asserted issuer grants, mandates independently trusted issuer proof, and reports no connected government credential or executor. This is an additional domain to the project estate, but **not proof of elevated government access**. Source should remain separate from fellowship core examples unless discussing authorization confusion.

## Current form accessibility

A second JavaScript-rendered extraction attempt at the Constellation Airtable link returned empty content. Exact questions and submission remain unknown; no form submitted.


## October 17 verified source-to-production case: P-Core lexicon correction

A bounded causal-chain example with current, inspected evidence: mistaken phrase-to-intent auto-learning (documented 2026-10-11 examples `what cpu temperature -> get_weather`, `start minute timer -> run_ui_steps`) led to route-plausibility controls and regression fixtures. Later source audit identified stale cache on overlay rollback, deletion, path switch and equal-mtime replacement. [PR #414](https://github.com/J2theN1/modu-pkg-jason/pull/414) introduced canonical and extracted loader changes and six new regression scenarios, passed Clean Python Build + full CI, and was **squash-merged** into `4.x` as `11023a920f30eea94332af6ea10e7e9b6e1edb85`. MODU native `source.generation.sync` succeeded (Task Control task id redacted in this public copy) with artifact confirming clean exact-SHA source_root; `source.runtime.reconcile` task (id redacted in this public copy) succeeded, artifact verified `promoted=true`, `source_head` exact, `service_active=true`, `health_ok=true`, `deployment_identity_exact=true`, release under an immutable versioned release path (path redacted in this public copy). Deployment receipt digest redacted in this public copy. This is strong evidence of governed repair and runtime deployment, **not** proof of post-deploy live temporary-overlay behavior, generalized self-correction, or scientific causality. Verifier network-exposure details are not disclosed in this public copy. Dirty Gitea checkout was left unchanged.

## Current applications and alternative programs checked October 17

- **Anthropic AI Safety & Security Fellows**: official [posting](https://job-boards.greenhouse.io/anthropic/jobs/5183044008) confirms **October 18, 2026** January-cohort consideration deadline, four months full-time, Canada/US/UK remote eligibility with local work authorization, Python fluency requirement, CAD 4,300 weekly stipend, approximately USD 15,000 per month compute support. **The Constellation application form, not the regular Greenhouse application, is mandatory.** No submission has been verified or performed. Appropriate opening thesis: reliability of long-horizon autonomous agents, false-success versus verified result, memory-promotion contamination, crash/replay and auditability.
- **Apart Research**: [programs](https://apartresearch.com/programs) list AI Collusion Research Sprint Oct 23-25, Swarm Alignment Hackathon Nov 6-8, AI x Epistemics Sprint Nov 13-15, Agent Attribution Nov 27-29, 2026. Sprints are remote-friendly and open to all; standout submissions may progress to Studio then funded research fellowship; **partnered direct fellowship currently has no open applications**. Project-specific fit: persistent multi-agent commitments, resource leases, and measured false completion. [Fellowships overview](https://apartresearch.com/fellowships).
- **OpenAI Safety Fellowship**: [2026 program](https://openai.com/index/introducing-openai-safety-fellowship/) had **May 3, 2026 deadline**, Sept 14, 2026–Feb 5, 2027 program; not presently an open route for this intake. [OpenAI Residency](https://openai.com/residency/) says 2026 applications closed; monitor future round.
- **Google DeepMind multi-agent safety funding call**: [announcement](https://deepmind.google/blog/investing-in-multi-agent-ai-safety-research/) aligns with MODU testbeds, agent networks, commitments and oversight but Aug 8, 2026 application cutoff has passed. Preserve as an exact-fit research-priority signal rather than presenting it as an open grant.
- **Anthropic STEM Fellow**: separate posting requires PhD and US work authorization, so do not confuse with this Anthropic AI Safety & Security Fellows opportunity.

Position the application around one bounded empirical investigation, not a list of dozens of systems. Do not claim applicant self-authored all code: describe direction of AI-assisted implementation, deterministic test design, investigative debugging and evidence-based decisions accurately.
