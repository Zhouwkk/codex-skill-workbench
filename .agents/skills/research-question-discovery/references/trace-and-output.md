# Reasoning Trace and Output

Use outcome-level summaries, not hidden chain-of-thought or a transcript of every exchange.

## Round-level commit

Commit a round only after User Reflection is Retain, Revise, or Unresolved Fundamental Tension. Use this compact record:

```text
Round N

Intuition:
<the user-owned intuition at the start of the round>

Core Challenge:
<the one reasoning link examined>

Hypothesis:
<the candidate explanation and its strongest live alternative or boundary>

Evidence:
<direct evidence, counterevidence, boundary, mechanism gap, and evidence state>

User Revision:
<Retain, the user's revised intuition, or Unresolved Fundamental Tension>
```

When `User Revision` is a revised statement, use that exact meaning as the next round's `Intuition`. Do not polish it into a substantively different claim without confirmation.

If reflection is Pending, do not commit the round. Leave a checkpoint containing the same fields, with `User Revision: Pending` and the single decision still needed from the user.

## Final Candidate Research Question

When the Research Question Gate passes, return:

```text
Candidate Research Question
<one primary question>

Why this question matters for understanding
<the understanding change it could produce>

Underlying tension
<candidate mechanism versus its main alternative, boundary, or unresolved condition>

What would discriminate
<the kind of observation that would separate the live explanations>

Current evidence landscape
<Well-supported, Mixed or conditional, Under-explored, or Pending, with a concise rationale>

Scope boundary
<important setting and assumptions; explicitly state that novelty and publishability have not been evaluated>

Reasoning Trace
<the compact committed rounds>
```

Keep one primary research question. Add a secondary wording only when it clarifies a genuine ambiguity rather than creating a menu of ideas.

## Quality rules for the wording

The final question should:

- be faithful to the user's confirmed intuition or unresolved tension;
- name the phenomenon and relevant condition or mechanism clearly enough to guide evidence;
- remain answerable in principle without pretending that a full experiment has already been designed;
- distinguish competing explanations when that is the source of the research value;
- avoid novelty, venue, contribution-strength, and publication claims.

If one of these properties is missing, do not hide it with more polished wording. Return to the state that can resolve it.
