# Review & Evolution

Read this reference for daily synchronization, weekly review, failure diagnosis, or changes to personalized operating rules.

## Daily state sync

Daily closure is a light synchronization step, not a journal or productivity score.

1. Confirm that completed Primary or Secondary loops updated Project State when warranted.
2. Triage Inbox items: connect, incubate, schedule genuine Maintenance, or discard.
3. Run [staleness-check.md](staleness-check.md) and surface at most one unresolved alert.
4. Leave one Tomorrow Candidate Primary, clearly marked as provisional.
5. Refresh Dashboard attention items from observed remote status; preserve `Unknown` when no recent observation exists.

Do not require the user to fill a daily reflection form.

## Weekly review objective

Answer only:

1. Which research states meaningfully changed?
2. Where did the operating system fail or become too heavy?
3. What single rule experiment, if any, should run next week?

## Weekly review workflow

### 1. Reconstruct state change

Compare the week-start card with current Project States and Session Records. Report learning, decisions, resolved risks, new risks, and changed questions. Distinguish activity from Meaningful Updates.

### 2. Evaluate the weekly plan

Classify each intended state change:

- **Achieved**: intended state change occurred;
- **Adapted**: the original goal was superseded by more important feedback;
- **Stalled**: no intended change, important new feedback, or valid blocker occurred.

Adaptation is not failure when evidence rationally changed direction.

### 3. Diagnose one dominant failure pattern

Use evidence, not self-judgment. Choose the most consequential category:

- **Planning Failure**: too many Push lines, oversized weekly change, or poor allocation;
- **Question Failure**: vague or expanding question, unclear evidence, or no feedback loop;
- **Execution Failure**: clear action existed but drift, context switching, or failure to start dominated;
- **State Failure**: state was too long, stale, contradictory, or insufficient for fast restart;
- **Load Failure**: throughput outpaced interpretation, Secondary became another Primary, or cognitive recovery was insufficient.

Classify stale server pointers, missing provenance, duplicate handoff imports, or confusing execution status under State Failure. Classify repeated dispatch without result interpretation under Load Failure. Do not create a separate remote-work failure category.

Do not infer a stable pattern from one noisy incident. State the evidence count and uncertainty.

### 4. Update the meta loop

Produce:

- **Keep**: one rule or practice supported by evidence;
- **Problem**: the dominant repeated or high-impact failure;
- **Experiment**: at most one testable rule change for next week.

An experiment must include a hypothesis, trigger or behavior, and evidence sought. Add it to Experimental Rules only after the user accepts it or has delegated rule experiments.

At a later review:

- **Promote** when repeated evidence supports the rule;
- **Reject** when it fails or creates worse tradeoffs;
- **Revise** when the mechanism appears useful but the trigger or scope is wrong;
- **Backlog** when evidence remains insufficient.

Never edit the installed Skill as part of ordinary review. A Skill change requires an explicit separate request and should cite the repeated failure or structural defect motivating it.

## Avoid moralizing

Do not reduce problems to motivation or discipline. First test whether the plan, question, state representation, or load design made execution unnecessarily hard. When evidence supports execution drift, describe the observable behavior without assigning character judgments.

Use the Daily State Sync and Weekly Review templates in [output-templates.md](output-templates.md).
