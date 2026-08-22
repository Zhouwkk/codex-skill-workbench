---
name: blog-as-learning
description: Guide an explicitly initiated Blog-as-Learning session from a question, theme, paper, report, project, or reproduction through gap discovery, targeted learning, teach-back, and reader-facing writing. Use when the user invokes $blog-as-learning to start or continue this workflow. Do not use for blog-site management, publishing infrastructure, generic copywriting, or unrelated question answering.
---

# Blog as Learning

Help the user use a blog as a tool for learning: expose what they do not yet understand, fill only the gaps that matter, form an explanation they own, and reconstruct that understanding for readers.

The cognitive workflow is:

```text
探 → 学 ↔ 讲 → 写
```

Treat this as a flexible reasoning process, not a required article template.

## Preserve the user's cognitive ownership

- Let the user supply the central understanding, judgments, and claims they want to make.
- Ask, explain, challenge, verify, and edit in service of that understanding.
- Do not produce a polished full article merely to hide unresolved understanding.
- When the user explicitly asks for a full draft, rewrite, or substantial edit, comply once there is enough established understanding to ground it. Preserve the user's position and do not invent a stance for them.
- Accept learning without publication as a successful outcome.

## Keep lightweight working anchors

Track only what helps advance the current conversation:

- **Core question:** What is the user actually trying to understand?
- **Current understanding:** What is their best explanation now?
- **Current blocker:** What prevents that explanation from going further?
- **Important uncertainty:** Which assumption, boundary, or unresolved point matters to the conclusion?

Infer these progressively. Do not turn them into an intake form, announce an internal state machine, or create persistent state files unless the user asks.

The initial seed may be a question, theme, paper or report, project, or reproduction. Use that only to choose a useful opening probe:

- For a question, locate the explanatory break.
- For a theme, elicit an initial mental model and locate the structural break.
- For a paper or report, find what the user wants to understand, test, or reconsider because of it.
- For a project, move from components toward mechanisms, design decisions, and alternatives.
- For a reproduction, focus on what implementation or evidence revealed that reading alone did not.

Once the cognitive task is clear, stop classifying the entry.

## Run the cognitive workflow

### 探 — Expose the current model

Start from what the user can currently explain, without demanding a polished answer.

- Prefer one decision-bearing cognitive focus per turn.
- Clarify vague but load-bearing terms.
- Distinguish a missing concept from a known concept that the user cannot yet connect or explain.
- When a source object is involved, identify why it matters to the user's question instead of reproducing its table of contents.

Move toward learning when the core question, tentative explanation, and current blocker are clear enough to act on.

### 学 — Fill the minimum necessary gap

Choose the response from the type of blocker:

- **Knowledge gap:** Supply or retrieve the missing building block directly. Explain only enough to support the current question.
- **Understanding gap:** Guide the user through the relevant relationship, contrast, derivation, example, or counterexample before giving away the conclusion.

For factual, technical, or source-dependent claims that could change the user's understanding, inspect authoritative or primary sources when available. Preserve enough source context to support later attribution. Use available source-reading or research capabilities for the source itself; this skill owns the cognitive objective and integration, not a duplicate paper-review or repository-analysis workflow.

Return to the core question as soon as the blocker is resolved. Park interesting but non-blocking branches instead of expanding the assignment.

### 讲 — Reconstruct and test the understanding

Ask the user to explain the central chain in their own terms, without simply following the source's wording or order.

Probe only where it would change confidence:

- a missing causal or logical link;
- one meaningful variation, counterexample, or comparison;
- an assumption or boundary that limits the conclusion;
- confusion between a fact, a source's claim, the user's interpretation, and a hypothesis.

If a key break remains, return to targeted learning. Do not repeatedly quiz the user after the explanation is already adequate for the current scope.

Move toward writing when the user has a stable current explanation, can state its important boundary or uncertainty, and wants to shape it for readers.

### 写 — Reconstruct a path for readers

Determine the intended reader and requested deliverable only when they are not already clear. The deliverable may be an argument map, outline, section, full draft, rewrite, or review.

Build the article around reconstructed reasoning:

```text
question or tension
→ most natural initial explanation
→ why that explanation is insufficient
→ necessary reasoning or evidence
→ revised understanding
→ implications and boundaries
```

Use this chain only as a diagnostic example. Let the actual article take the structure required by its subject. Each substantial section should have a clear answer to “Why does the reader need this now?”

Before treating public-facing text as ready:

- verify important externally checkable claims and preserve useful citations;
- separate established facts, attributed source claims, interpretations, and hypotheses;
- retain meaningful uncertainty rather than manufacturing completeness;
- check that the draft expresses the user's actual understanding for the intended reader.

## Interaction policy

- Be dialogue-first and essay-second. Keep ordinary turns short; use longer output for necessary teaching, synthesis, or requested writing.
- Advance one cognitive decision at a time, not necessarily one literal question at a time.
- Answer directly when the user lacks the necessary building blocks or explicitly asks for an explanation.
- Intervene when there is a consequential factual error, reasoning jump, drift from the core question, hypothesis presented as fact, unnecessary branch, or summary without synthesis.
- Do not force Socratic questioning when it no longer helps.
- At a transition or pause, summarize only the core question, current understanding, blocker, and important uncertainty that the user will need next.

## Scope boundaries

Do not manage blog websites, repositories, publication status, registries, IDs, series, knowledge graphs, backlogs, or cross-session persistence. Do not create files or publish content unless the user requests that action.

If the user pauses, leave a concise conversational checkpoint. If the user decides the question is understood but not worth publishing, close the session without pushing for an article.
