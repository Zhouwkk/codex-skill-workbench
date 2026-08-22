# Output Templates

Use only the template relevant to the current mode. Remove empty fields and explanatory placeholders. Keep the user's own terminology where it is clearer.

## Dashboard

```markdown
# Research OS Dashboard

- Active week: [<YYYY-Www>](weekly/<YYYY-Www>.md)
- Last synchronized: <timestamp>

## Today
- Primary: [<project>](projects/<project-slug>.md) — <Current Question>
- Start with: <exact local or remote action>
- Secondary: <project or loop>
- Fallback trigger: <condition> -> <alternative>

## Weekly allocation
- Push 1: [<project>](projects/<project-slug>.md) — <desired state change>
- Push 2: [<project>](projects/<project-slug>.md) — <desired state change>
- Keep-alive: [<project>](projects/<project-slug>.md) — <Minimum Feedback>

## Remote attention
- <project>: <Pending | Running | Completed, uninspected | Failed, untriaged | Blocked | Unknown> — <job/run ID and purpose> — observed <timestamp>

## Waiting / blocked
- ...

## Inbox
- <count or one short attention cue>
```

Regenerate this view from canonical files. Do not accumulate completed items or copy full Project States into it.

## Project State

```markdown
# <Project>

- Status: <Active | Paused | Completed | Incubating>
- Weekly mode: <Push | Keep-alive | Build | Maintenance | Unassigned>
- Last meaningful update: <date>
- Blocker: <None or specific condition>

## Established
<compressed evidence-backed conclusions>

## Working hypothesis
<current explanation, with uncertainty>

## Open risk
<most decision-relevant uncertainty>

## Current question
<one answerable question>

## Expected feedback
<observable evidence>

## Next action
<immediately executable action>

## Remote Context
- Execution location: <Remote | Hybrid>
- Access mode: <Manual handoff | SSH available>
- Server alias: ...
- Remote workspace: ...
- Repository: ...
- Revision: ...
- Environment: ...
- Scheduler: ...
- Active runs: <job/run ID — purpose — status>
- Artifact pointers: ...
- Last remote observation: ...
- Remote next check: ...
- Last imported capture: ...
```

## Weekly Control Card

```markdown
# Weekly Control Card — <YYYY-Www>

## Push 1 — <project>
- Weekly state change: ...
- Current question: ...
- Next action: ...

## Push 2 — <project or omitted>
- Weekly state change: ...
- Current question: ...
- Next action: ...

## Keep-alive — <project>
- Minimum feedback: ...
- Next action: ...

## Build
- Focus: ...
- Expected synthesis or decision: ...

## Maintenance
- ...

## Watchlist
- <blocked, stale, or capacity risk>
- <remote run needing inspection or status refresh>

## Experimental rule
- <one rule or omitted>
```

## Daily Control Card

```markdown
# Today

## Primary — <project>
- Current question: <reference current state>
- Expected feedback: <reference current state>
- Start with: <immediate action>
- Why now: <one sentence>

## Secondary — <project or loop>
- Intended feedback: ...

## Fallback
- Trigger: ...
- Switch to: ...

## Remote attention
- <project, run/job ID, exact check, and last-observed time>

## Maintenance
- ...

## Capacity note
- <only when relevant>
```

## Session Entry

```markdown
## Primary — <project>
- Question: ...
- Expected feedback: ...
- Start now: <include server alias and exact remote pointer when applicable>
- Checkpoint when: ...
```

## Session Checkpoint

```markdown
## Feedback
<what was observed>

## Provenance
- Server / location: ...
- Revision: ...
- Job or run: ...
- Artifact or log: ...
- Observed: ...

## Impact — <Support | Challenge | Resolve | Surprise>
<why>

## State update
- Established: <changed or unchanged>
- Working hypothesis: <changed or unchanged>
- Open risk: <changed or unchanged>
- Current question: <new or resolved>
- Next action: ...

## Captured for later
- ...
```

## Daily State Sync

```markdown
## State synchronized
- <project>: <meaningful change or “activity only”>

## Remote status synchronized
- <project>: <status and observed-at time, or Unknown>

## Inbox disposition
- ...

## Keep-alive risk
- ...

## Tomorrow candidate
- <project + question>, provisional
```

## Weekly Review

```markdown
# Weekly Review — <YYYY-Www>

## Research update
- <project>: <week-start state -> current state>

## Plan assessment
- <project>: <Achieved | Adapted | Stalled> — <evidence>

## Keep
- ...

## Problem — <Planning | Question | Execution | State | Load>
- Evidence: ...
- Confidence: ...

## Rule experiment
- Hypothesis: ...
- Rule for next week: ...
- Evidence sought: ...
```

## Override record

```markdown
- Override: <original recommendation> -> <user choice>
- Reason: <hidden constraint or judgment>
- Date: <date>
```
