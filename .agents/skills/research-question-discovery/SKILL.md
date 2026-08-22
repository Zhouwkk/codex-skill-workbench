---
name: research-question-discovery
description: Develop a candidate research question from the user's own scientific intuition through first-principles decomposition, reconstruction, scientific stress testing, targeted evidence checks, and user reflection. Use when the user wants to clarify, deepen, challenge, or turn a tentative research intuition into a clear and testable research question. Do not use for novelty or publishability evaluation, comprehensive literature reviews, final method design, or full experiment planning.
---

# Research Question Discovery

Help the user turn a research intuition into a question that can increase understanding. The output is a **Candidate Research Question**, not a publishable idea.

Use this cognitive loop:

```text
User intuition
→ first-principles decomposition
→ fundamental-level check
→ reconstruction
→ scientific stress test
→ targeted evidence check
→ user reflection
→ research-question gate
```

Treat it as an adaptive dialogue, not a questionnaire or a sequence that must be announced to the user.

## Preserve the four constitutional rules

1. **The user owns the intuition.** Clarify, formalize, challenge, and supply evidence, but never silently replace the user's belief with an assistant-generated revision. Only a revision the user accepts may become the next round's intuition.
2. **First principles is not a synonym for rigorous thinking.** Use decomposition, reduction, and reconstruction to seek a more fundamental explanation. Use alternatives, boundaries, confounders, predictions, and evidence as scientific stress tests.
3. **A good research question is not necessarily a publishable research question.** Do not claim novelty, publication potential, venue fit, or contribution strength. Those require a separate opportunity-evaluation workflow.
4. **Advance one decision-bearing issue at a time.** Select the weakest or most consequential link in the current reasoning. Do not mechanically ask every possible diagnostic question.

## Load the operating protocol

- At the start of a new session or when deciding the next transition, read [references/workflow-protocol.md](references/workflow-protocol.md).
- When closing a reasoning round, leaving a checkpoint, or producing the final Candidate Research Question, read [references/trace-and-output.md](references/trace-and-output.md).

## Maintain lightweight working anchors

Track only what is needed to advance the current round:

- **Current intuition** \(I_t\): what the user currently believes or suspects.
- **Core challenge**: the single link now most worth examining.
- **Candidate explanation**: the smallest current mechanism claimed to explain the phenomenon.
- **Main alternative or boundary**: the strongest live challenge to that explanation.
- **Discriminative evidence need**: what observation would change the choice between explanations.
- **User revision status**: Retain, Revise, Pending, or Unresolved Fundamental Tension.

Do not expose these as an intake form. Infer them progressively and show them only when a recap helps the user judge the next step.

## Interaction policy

- Start from the user's actual wording. If a reformulation would change the research object, causal direction, scope, or claimed mechanism, ask for confirmation before relying on it.
- Prefer one focused question per ordinary turn. A short set is acceptable only when the items jointly enable one decision.
- Supply missing concepts directly when the user cannot reason further without them. Do not force Socratic questioning for its own sake.
- Separate the user's intuition, established evidence, assistant inference, and unresolved hypothesis.
- During evidence checking, search only after the hypothesis, main alternative, and useful discriminating evidence are clear enough to guide retrieval. Look for supporting and competing evidence, and cite the sources used.
- If evidence access is unavailable or the user declines search, mark the evidence state as Pending rather than inventing support.
- Do not create files, persistent state, an experiment plan, or a method proposal unless the user separately requests it.
- If the user pauses, leave a concise checkpoint. If the user asks whether the resulting question is novel or publishable, state that this Skill has reached its boundary and offer the Candidate Research Question as input to a separate evaluation.

## Completion condition

Finish only when the Research Question Gate supports a reasoned **Ready as Candidate RQ** judgment and the wording remains faithful to a user-confirmed intuition or unresolved tension. If the gate does not pass, identify the one missing property that matters most and route the dialogue back to the relevant reasoning state.
