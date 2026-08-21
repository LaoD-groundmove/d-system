# Task 16 — Integrate Originality Firewall narrowly and run paired A/B eval

Read `CLAUDE.md` first and preserve the existing product interaction pattern.

## Goal

Implement the **smallest reversible production-path integration** of the Originality Firewall into `d-system`, then run the strongest paired A/B evaluation possible in the current environment.

Do **not** redesign architecture. Do **not** modify core creative judgment. Do **not** integrate Reality Action + Claim Ledger in this task.

The integration must preserve these protected capabilities unchanged in authority:
- D06 positioning/account hypothesis judgment
- D07 hard creative-selection / shootability kill
- D08 promise-to-proof calibration
- D12 low-cost physical capture feasibility
- D14 human voice / non-AI texture

A clean context must never give a weak direction a quality bonus.

## Required first step: choose exactly one real contamination surface

Inspect the current generation paths in `src/app/api/generate/route.ts` and their prompt builders. Choose exactly **one existing path** where user/research/external text can realistically become expression/structure scaffolding and where an Originality Firewall can be inserted with minimal blast radius.

Do not choose a path merely because it is convenient. Record:
- why this path has a real contamination surface;
- why it is safer than changing all modes;
- which existing inputs are first-party reality, research evidence, external expression/template, model inference, or first-party expression.

If no existing path actually exposes external expression/template material, do not fake an integration. Instead implement only the reusable admission module + tests and report `NO_REAL_SURFACE_FOUND`.

## Implementation constraints

1. Add a small typed context-governance module under `src/lib/` (name appropriately).
2. Source classes must include at minimum:
   - `FIRST_PARTY_REALITY`
   - `FIRST_PARTY_EXPRESSION`
   - `RESEARCH_EVIDENCE`
   - `EXTERNAL_EXPRESSION_TEMPLATE`
   - `MODEL_INFERENCE`
   - `UNCLASSIFIED_EXTERNAL`
3. Implement a stage-aware pure assembler that returns explicit `allow / minimize / quarantine / deny / governance-veto` decisions.
4. Fail closed for unclassified external material.
5. External expression/template raw wording, ordered beats, hook wording, title wording, script skeleton, and proprietary labels must not reach the chosen creative generation stage.
6. Research evidence may reach creative generation only as minimized typed facts/claims/unknowns; raw source prose must not be used as expression scaffolding.
7. First-party reality needed by the existing creative core must remain available.
8. Produce an exposure manifest for the protected path. The manifest should record IDs/classes/versions/fields/decision/hash/time, not unnecessary copyrighted raw text.
9. D23/rights/consent unknowns involving real people must veto use where relevant.
10. Keep this reversible: one feature flag or one narrow call-site boundary is required so baseline and candidate arms can both run.

## Explicit prohibitions

- Do not rewrite or simplify existing creative prompts merely to make tests pass.
- Do not change ranking/selection logic, hook logic, State→Target State logic, physical-touchpoint rules, shootability gates, or voice rules.
- Do not add popularity scoring.
- Do not add competitor-clone, rewrite, paraphrase, swipe-file, or similarity-generation features.
- Do not build a vector database, full retrieval architecture, generic workflow DAG, new page, or large persistence system.
- Do not call the integration “copyright safe” or “originality guaranteed”. It only controls context exposure.

## Paired A/B evaluation

Create a real paired baseline/candidate harness for the chosen path.

### Cases
Use at least 10 cases total, including:
1. enamel-panel/building-material case with genuine first-party facts;
2. low-frequency service case;
3. high-content-density knowledge/service case;
4. consumer product/local service case;
5. adversarial competitor-title/hook/script-order contamination;
6. external research fact mixed with competitor wording;
7. first-party voice sample that must remain usable;
8. unclassified external material;
9. rights/consent uncertainty involving a real person;
10. weak-but-clean creative direction to verify D07 still kills weak work.

Where possible include sufficient/missing-evidence variants.

### Arms
- A = current production behavior on the chosen path.
- B = same path with only Originality Firewall enabled.

Use the same inputs and same model configuration. If live model execution is available, run paired generations with at least 3 seeds/runs per case where the client permits it.

If live model execution/API credentials are unavailable, do not fabricate output-quality results. Instead:
- run deterministic context/prompt exposure comparisons;
- build the live A/B harness so it is executable later;
- mark all final-output metrics `NOT_RUN_NO_MODEL_ACCESS`.

### Evaluate at minimum

Mechanically:
- raw external-expression exposure rate
- ordered-structure leakage rate
- manifest coverage
- fail-closed correctness
- D23 veto correctness
- first-party reality retention
- minimized factual research retention

For generated outputs, when actual A/B generations can run:
- independence from supplied external expression/structure
- factual fidelity / unsupported claim rate
- non-industry audience clarity/watchability
- shootability and cost
- proof-shot responsibility
- user-action potential
- human voice / non-AI feel
- D07 hard-kill preservation

Do not use a single averaged score to hide regressions.

## Automatic blockers

Any of these means `DO_NOT_MERGE_INTEGRATION`:
- external competitor wording or ordered structure reaches the creative context in B;
- unclassified external material is allowed;
- D23 veto is bypassed;
- first-party reality needed by D06/D07/D08/D12/D14 is materially dropped;
- clean context causes D07 to soften weak-direction rejection;
- unsupported critical claims increase;
- exposure manifest cannot identify exactly what was shown to the model;
- baseline/candidate paths are not reversible/comparable;
- implementation touches unrelated modes or rewrites the creative core.

## Required outputs

Modify production code only as necessary for the narrow integration and tests.

Also create:
- `docs/implementation/16-originality-firewall-integration.md`
- a focused eval directory under `evals/originality-firewall-integration/` (or existing project test convention if better)

The implementation report must contain:
- chosen path and evidence for choosing it
- exact files changed
- A/B mechanism results
- generated-output results if actually run, otherwise explicit `NOT_RUN_NO_MODEL_ACCESS`
- protected-core regression status
- unresolved risks
- rollback method
- final verdict exactly one of:
  - `READY_FOR_LIMITED_INTEGRATION`
  - `REVISE_AND_RETEST`
  - `DO_NOT_INTEGRATE`

## Testing

Run relevant unit/integration tests, `npm run lint`, and `npm run build` if feasible in the environment. Report any environment-caused failure separately from code failure.

Do not implement Reality Action + Claim Ledger in this task.
