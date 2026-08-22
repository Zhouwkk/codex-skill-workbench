# Workflow Protocol

This file defines the v0.1 state transitions. Use the states to decide what the conversation needs next; do not recite them or force one state per turn.

## Round semantics

A reasoning round starts with a user-owned intuition \(I_t\) and remains open until the user responds to the reasoning and evidence. A closed round has this shape:

```text
I_t → candidate explanation or hypothesis H_t → evidence landscape E_t
    → user response → retained or revised intuition I_(t+1)
```

The assistant may propose interpretations and wording. It may not create \(I_{t+1}\), accept it on the user's behalf, and continue as though the user had endorsed it.

## S0 — Intuition Capture

**Objective:** Establish what the user currently believes, suspects, or finds surprising.

**Actions:**

- Preserve the research object, comparison, direction of effect, scope, and uncertainty in the user's statement.
- Clarify only ambiguity that would materially change the reasoning path.
- When useful, formalize the intuition as a provisional relation such as \(A \rightarrow B\), explicitly retaining uncertainty.

**Exit:** The intuition is specific enough to identify one explanatory link worth examining. If the user has only a broad topic, stay here and elicit the concrete tension rather than generating an idea for them.

## S1 — First-Principles Decomposition

**Objective:** Find a Candidate Fundamental Explanation by separating necessary factors from contingent implementations.

**Actions:**

1. Make the claimed relation explicit.
2. Ask what must occur between the antecedent and outcome.
3. Decompose it into the smallest useful causal or logical chain.
4. Distinguish necessary conditions, enabling conditions, observed manifestations, and implementation-specific details.
5. Remove or replace factors that are not necessary and see whether the explanation still holds.

Do not reduce the process to repeated “why” questions. Do not keep decomposing merely because a lower level exists.

**Exit:** There is a compact candidate explanation that could determine whether the focal phenomenon occurs. Move to S2. Return to S0 if decomposition reveals that the initial intuition itself is not stable enough to examine.

## S2 — Fundamental-Level Check

**Objective:** Decide whether the current explanation is sufficiently fundamental for the present research scale.

Judge three properties without assigning scores:

- **Explanatory:** It explains the phenomenon instead of renaming or redescribing it.
- **Determinative:** Changing the proposed factor could change whether or how the phenomenon occurs.
- **Research-sufficient:** Going deeper is unlikely to alter the current research question or the kind of evidence needed.

A useful progression is:

```text
What happens?
→ Why does it happen?
→ What determines whether it happens?
```

**Transition:** If the explanation is still surface-level or only one implementation of a more general mechanism, return to S1. If it is sufficiently fundamental, move to S3.

## S3 — Reconstruction

**Objective:** Check whether the candidate explanation can actually regenerate the important phenomenon without silently reintroducing discarded factors.

**Actions, in order:**

1. Freeze the proposed basic factors and state what follows from them.
2. Use those factors to explain the important manifestations that motivated the intuition.
3. Identify any important manifestation the explanation cannot recover.

Treat an abstract statement that can label every outcome but predicts none as insufficient. If reconstruction needs a discarded factor, either explain how it derives from the retained factors or return to S1 and revise the explanation.

**Exit:** The explanation reconstructs the focal phenomenon and exposes at least one meaningful condition or consequence. Move to S4.

## S4 — Scientific Stress Test

**Objective:** Turn a plausible explanation into a scientifically discriminable hypothesis.

Attack the current weakest scientific link. Choose among:

- **Alternative explanation:** another mechanism can produce the same observation.
- **Boundary condition or counterexample:** the explanation is too broad or does not say when it should fail.
- **Confounder:** a third variable may create the apparent relation.
- **Discriminative prediction:** two live explanations lack an observation that would distinguish them.

Do not ask all four by default. Select the attack that would most change confidence in the current explanation.

**Exit:** The round has a candidate hypothesis, a main alternative or meaningful boundary, and a discriminative evidence need. If the attack changes the basic explanation, return to S3 before searching evidence. Otherwise move to S5.

## S5 — Targeted Evidence Check

**Objective:** Build an Evidence Landscape that informs reflection without turning into a comprehensive literature review or a novelty search.

Define the search target before retrieval:

- the candidate hypothesis;
- the strongest competing explanation;
- the relevant setting or boundary;
- the observation that would discriminate between them.

Search for four kinds of evidence as relevant:

1. Direct tests of the hypothesis.
2. Evidence supporting a competing explanation or contradicting the hypothesis.
3. Boundary conditions under which reported results change.
4. Mechanism-level evidence that distinguishes the live explanations.

Prefer primary research for scientific claims. Report what the evidence actually tests; do not infer mechanism from outcome-only results. Stop when direct and competing evidence are covered well enough for reflection, the important boundary is roughly known, and additional searching has low expected value for the current decision. Absence of direct evidence may itself justify stopping with an Under-explored state; it does not establish novelty.

Summarize the evidence state as one of:

- **Well-supported**
- **Mixed or conditional**
- **Under-explored**
- **Pending** when evidence was not checked

Also state any unresolved tension and whether mechanism-level discrimination exists.

**Exit:** Move to S6. Do not revise the user's intuition automatically, even if the evidence strongly challenges it.

## S6 — User Reflection

**Objective:** Return interpretive ownership to the user.

Present a compact reflection packet:

- original intuition;
- candidate explanation or hypothesis;
- strongest evidence and counterevidence;
- main tension, boundary, or plausible interpretations.

Then ask the user how they now view the original intuition. Accept four outcomes:

- **Retain:** the user keeps the intuition, possibly with a clarified scope.
- **Revise:** the user states or accepts a changed intuition.
- **Pending:** the user cannot yet decide; the round remains open.
- **Unresolved Fundamental Tension:** the user identifies competing explanations that current reasoning and evidence cannot resolve.

Do not close a Pending round. A user-confirmed revision becomes \(I_{t+1}\). A retained intuition, confirmed revision, or unresolved tension may proceed to S7 when the completed reasoning already grounds a research question; otherwise begin the next round from \(I_{t+1}\).

## S7 — Research Question Gate

**Objective:** Decide whether the current understanding can be expressed as a good Candidate Research Question.

Make a reasoned judgment across five properties; do not total scores or treat them as a mechanical checklist:

- **Understanding Gain:** Answering the question would materially change what is understood.
- **Mechanism Depth:** The question concerns a determining mechanism or condition rather than only a surface symptom.
- **Evidence-backed Gap:** The targeted evidence leaves a real unresolved issue. This is not a claim of literature-wide novelty.
- **Discriminative Testability:** Conceivable evidence could distinguish the live explanations or conditions.
- **Stopping Sufficiency:** Going deeper is unlikely to improve the question enough to justify another decomposition round.

Use one of two verdicts:

- **Ready as Candidate RQ:** formulate the question and prepare the final output.
- **Not yet:** name the single most consequential deficiency and route back to S1, S3, S4, S5, or S6.

Prefer question forms that expose mechanism, boundary, or competing explanations, such as “What determines whether…?”, “Under what conditions…?”, or “Is Y driven primarily by X or Z under C?”. Do not force these templates when another formulation is clearer. Avoid converting the result into “Can we propose a method that…?” unless method invention is itself the user's confirmed object of inquiry.
