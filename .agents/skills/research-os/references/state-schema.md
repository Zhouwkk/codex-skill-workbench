# State Schema

Read this reference when creating, locating, restoring, or updating persistent research state.

## State home

Once the user chooses a state home, use this layout inside that directory unless an existing compatible layout is already in use:

```text
<state-home>/
├── Dashboard.md
├── projects/
│   └── <project-slug>.md
├── sessions/
│   └── YYYY-MM-DD-HHMM-<project-slug>.md
├── weekly/
│   └── YYYY-Www.md
├── reviews/
│   └── YYYY-Www.md
├── inbox.md
└── rules.md
```

Create only the files needed for the current operation. Do not generate empty archives or placeholder projects.

`Dashboard.md` is the single human-facing entry point on the Mac. It summarizes active allocation and remote execution status, then links to canonical Project States. It is a view, not a second source of truth: project beliefs and questions live in `projects/`, the active weekly allocation lives in `weekly/`, and raw session evidence lives in `sessions/`.

## Project State

Each research project has one canonical current-state file. Keep it compact enough to restore context in a few minutes.

```markdown
# <Project name>

- Status: Active | Paused | Completed | Incubating
- Weekly mode: Push | Keep-alive | Build | Maintenance | Unassigned
- Last meaningful update: YYYY-MM-DD
- Blocker: None | <specific blocker or waiting condition>

## Established
What evidence currently supports as known. Use concise claims, not a chronological log.

## Working hypothesis
The current best explanation or proposed direction. Mark uncertainty.

## Open risk
The most decision-relevant uncertainty, failure mode, or threat.

## Current question
One answerable question for the current feedback loop.

## Expected feedback
The observable evidence that would update the question or state.

## Next action
The smallest action that can begin immediately and obtain or inspect that feedback.

## Remote Context
Optional stable locators for projects executed outside the Mac. Use the schema in [remote-execution.md](remote-execution.md). Omit this section for fully local or non-computational projects.
```

### Field semantics

- `Status` describes lifecycle. `Weekly mode` describes current resource allocation; do not conflate them.
- `Established` contains compressed conclusions, not notes or raw results.
- `Working hypothesis` may be empty when evidence does not yet support one.
- `Open risk` should identify what could change the plan, not list every uncertainty.
- `Current question` should normally fit one feedback loop. Split multi-part questions.
- `Expected feedback` must be observable: a comparison, failure case, collaborator decision, measurement, or interpretable artifact.
- `Next action` starts with a concrete verb and identifies the immediate object, dataset, result, case set, draft, or person.
- Keep `Last Feedback` in Session Records. Promote only its durable implications into Project State.
- Keep remote locators in `Remote Context`; do not mix server inventory or raw log excerpts into the research-state fields.
- When importing a server snapshot, keep its accepted `Capture ID` as `Last imported capture` in Remote Context. This prevents duplicate evidence records without making the snapshot a second Project State.

## Project lifecycle

- **Incubating**: an idea exists but has not earned active resource allocation. Record the idea and the decision needed to activate it; do not fully plan it.
- **Active**: eligible for weekly allocation.
- **Paused**: intentionally inactive. Preserve the reactivation condition and do not include it in routine weekly scans.
- **Completed**: no further research loop is expected. Preserve final state and outcome.

Changing lifecycle status is a user-owned research decision. Recommend when appropriate, but obtain the user's decision before persisting it.

## Session Record

Session Records preserve evidence and the reasoning that produced a state change. They are append-only historical records.

```markdown
# Session — <date> — <project>

- Role: Primary | Secondary | Fallback
- Starting question: ...
- Expected feedback: ...
- Action taken: ...
- Feedback observed: ...
- Impact: Support | Challenge | Resolve | Surprise
- Reflection: ...
- State changes: ...
- Next question: ...
- Next action: ...
- Captures or interruption: ...
- Remote provenance: <server alias, job/run ID, artifact path, revision, and observed-at time when applicable>
```

Do not fabricate feedback from intended actions. If a session ended without interpretable evidence, record that fact and update the blocker, question, or action if warranted.

For remote work, record provenance precisely enough to find the evidence again, but summarize only the evidence needed for the research decision. A job submission or a path becoming available is an execution update; it becomes a Meaningful Update only when it changes a belief, question, decision, blocker, or next action.

## Inbox

Use one line or a very small block per item:

```markdown
- Type: Paper | Idea | Message | Other
  Context: <where it appeared>
  Capture: <why it may matter or the minimal next decision>
```

At daily sync, either connect the item to an existing project, incubate it, schedule a genuine maintenance action, or discard it. Do not convert every captured item into a task.

## Rules

Use `rules.md` for personalized operating hypotheses, not for duplicating this Skill:

```markdown
# Stable Rules
- ...

# Experimental Rules
- Rule: ...
  Hypothesis: ...
  Started: YYYY-Www
  Evidence sought: ...

# Evolution Backlog
- Observed pattern: ...
  Evidence: ...
```

Weekly reviews may update this file. They must not edit the installed Skill without an explicit separate request.

## State update discipline

After meaningful feedback:

1. Record raw evidence in the Session Record.
2. Classify its impact.
3. Update only Project State fields that actually changed.
4. Replace superseded current questions and actions; do not accumulate them.
5. Update `Last meaningful update` only when a Meaningful Update occurred.

When presenting an update, show a concise state diff before writing it if the interpretation is uncertain or research-direction judgment is involved.
