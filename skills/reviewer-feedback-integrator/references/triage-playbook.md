# Reviewer Feedback Triage Playbook

## Objective

Convert unstructured reviewer text into a small set of **atomic issues** that are each:
- independently addressable
- traceable to a manuscript change or an explicit rebuttal
- verifiable (numbers, citations, clarified assumptions, or new experiments)

## Step 1: Split into atomic issues

Split along “and / also / moreover / additionally”, and separate:
- missing baseline vs. missing realism vs. unclear setup
- “metric is wrong” vs. “metric is undefined” vs. “metric is not justified”
- “threats section weak” into specific threats that need to be named and bounded

Aim for **1–3 sentences per issue** in your response matrix.

## Step 2: Tag each issue (so you pick the right fix)

Use these tags:
- **Type**: correctness | clarity | novelty | evaluation | realism | scope | related work | presentation
- **Severity**:
  - **must-fix**: blocks acceptance / undermines a core claim
  - **important**: materially strengthens paper but not fatal alone
  - **nice-to-have**: polish
- **Ask**: add experiment | add baseline | add analysis | rewrite | add definition | add limitation | rebut

## Step 3: Choose a response strategy

Pick exactly one primary strategy per issue:

1) **Fix** (preferred)
- Add the missing evidence (experiment/analysis/baseline), or correct the mistake.

2) **Clarify**
- Keep the underlying method, but rewrite so the reader cannot misinterpret the claim/setup.
- Add definitions, operational semantics, and the “what exactly is measured” paragraph.

3) **Constrain**
- Narrow claims to what the data supports.
- Add a limitation + update threats-to-validity + update conclusions so everything matches.

4) **Rebut**
- Use only when the paper already contains the evidence and the reviewer likely missed it.
- Still improve signposting (“See §X, Fig. Y”) to prevent repeat confusion.

5) **Defer**
- Use rarely. Only for clearly out-of-scope asks that do not affect core claims.

## Step 4: Define “evidence that convinces”

For each issue, explicitly write what would convince a skeptical reader:
- A plot/table with a clear comparison and confidence/uncertainty (if applicable)
- A sensitivity analysis showing robustness to key assumptions
- A baseline that represents the strongest plausible alternative
- A citation to authoritative prior work (and a sentence stating how your work differs)

If you cannot articulate the convincing evidence, the response is not ready.

## Step 5: Systems-reviewer specific patterns (common and credible fixes)

### Validity / “realism”
Credible fixes usually include:
- explicit scope statement (“we study X; not Y”)
- sensitivity analysis over the criticized parameter/assumption
- a threats subsection that quantifies impact directionally (best-case/worst-case)

### Evaluation is weak
Credible fixes usually include:
- at least one strong baseline + justification for exclusions
- at least one stress / tail / corner scenario
- an ablation that isolates the claimed mechanism

### Metric / label is wrong
Credible fixes usually include:
- operational definition (what the system/user cares about)
- robustness check: conclusions hold under alternative labels/metrics
- error analysis: when labels disagree, what happens and why

## Step 6: Response-writing constraints

Keep each response:
- appreciative and non-defensive
- 1–3 short paragraphs
- anchored to concrete changes (“We updated §X and added Fig. Y showing …”)

Avoid:
- introducing new claims not backed by the paper
- arguing taste (“we believe this is fine”) instead of evidence

