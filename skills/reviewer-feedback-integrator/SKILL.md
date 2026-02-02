---
name: reviewer-feedback-integrator
description: Integrate reviewer feedback into a paper/repo by turning comments into an action matrix, concrete manuscript/experiment edits, and a polished response-to-reviewers (rebuttal, shepherding, or camera-ready revision). Use when you have reviewer notes, a meta-review, or shepherd requests and need systematic, traceable changes and responses.
---

# Reviewer Feedback Integrator

## Goal

Turn reviewer feedback into (1) a response matrix, (2) prioritized edits/experiments, (3) updated manuscript changes, and (4) a venue-appropriate response letter.

## Inputs (ask for these up front)

- Reviewer text (all reviews + meta-review) exactly as received.
- Venue + phase: rebuttal, shepherding, or camera-ready revision (and any format limits).
- Current artifact(s): paper source (LaTeX/Word/Markdown) and any relevant repo/scripts.
- Constraints: what can/can’t change (new experiments allowed? additional pages? new baselines?).

## Outputs (recommended files)

- `reviewer_response_matrix.md` (one row per atomic issue; source-of-truth tracker).
- `change_log.md` (section-by-section diff summary).
- `response_to_reviewers.md` (final response letter).

Templates: `assets/templates/` (copy and adapt).

## Workflow

### 1) Normalize feedback into atomic issues

- Split each review into **atomic**, independently addressable items (1 claim/concern/request per row).
- Preserve provenance: keep reviewer ID, quoted snippet, and any referenced section/figure/table.
- Avoid “mega-items” like “evaluation is weak” without decomposing into missing baseline / missing sensitivity / missing ablation / unclear setup.

### 2) Classify each issue (so you can choose the right response)

For each row, fill:
- **Type**: correctness / clarity / novelty / evaluation / realism / related work / presentation.
- **Severity**: must-fix (blocks acceptance) / important / nice-to-have.
- **Ask**: add experiment / add baseline / add analysis / rewrite for clarity / add limitation / rebut.
- **Evidence needed**: what concrete artifact will convince a skeptical reviewer (numbers, plots, citations, proof, implementation detail).

Reference: `references/triage-playbook.md`.

### 3) Decide the response strategy per issue

Choose one primary strategy (avoid mixing):
- **Fix**: change the paper/code/experiments so the concern is no longer true.
- **Clarify**: concern is caused by ambiguity; add missing definitions, scope, or derivations.
- **Constrain**: add a limitation / threat / boundary condition (and ensure claims match).
- **Rebut**: only when you can point to clear existing evidence; still improve wording if readers missed it.
- **Defer**: rare; only for non-core “future work” asks and only if it doesn’t weaken claims.

Rule of thumb: if a reviewer **could be right**, treat it as “Fix/Constrain”, not “Rebut”.

### 4) Build the response matrix (source of truth)

- Start from `assets/templates/reviewer_response_matrix.md`.
- Ensure every row has: action, location of change (file/section), and a 1–3 sentence “response text” draft.
- Add an “Owner/ETA” column if multiple people are working.

### 5) Implement changes (paper first, then response letter)

- Make the smallest change that truly resolves the concern, then update nearby text so the narrative stays coherent.
- When adding new results: update **claims**, **figures/tables**, **threats**, and **limitations** so everything stays consistent.
- Keep responses falsifiable: point to exact section/figure/table numbers and summarize what changed.

### 6) Quality bar (do this before finalizing)

- Coverage: every reviewer item has a response (no silent drops).
- Traceability: each response points to a concrete change or concrete existing evidence.
- Tone: appreciative, factual, non-defensive; never blame the reviewer for misunderstanding.
- Risk control: new text does not introduce unsupported claims or new confusion.

## Notes for systems-style reviewers (common failure modes)

- If the critique is “validity/realism”: add an explicit scope statement + sensitivity analysis + threat section updates.
- If the critique is “evaluation is weak”: add at least one **meaningful** baseline and one **stress** scenario; justify why other baselines are out of scope.
- If the critique is “metric/label is wrong”: define the operational semantics, show robustness checks, and quantify impact.

Keep this section high-level; use `references/triage-playbook.md` for detailed tactics.
