# Research Loop

Read this reference when the user starts, continues, checkpoints, interrupts, or closes a research session.

## Objective

Run one bounded feedback loop that produces an interpretable research-state update. The session is not defined by elapsed time or by finishing every related task.

## Entry

Before action, confirm or repair:

- **Current Question**: one answerable uncertainty;
- **Expected Feedback**: evidence that would update it;
- **Next Action**: the smallest immediately executable step;
- **Stop condition**: when evidence is sufficient for a checkpoint.
- **Execution context**: local document, named remote server/workspace, or hybrid handoff.

When state is incomplete, propose a narrow default. Do not conduct a long planning interview. If the user is already acting, capture the minimal missing frame without stopping useful work.

## Execution support

- Keep the active question visible in concise check-ins.
- Help interpret results, inspect artifacts, or choose the next evidence-producing action when requested.
- Do not introduce adjacent papers, experiments, optimizations, or ideas unless they directly affect the Current Question.
- Apply Stay / Capture / Interrupt to every new item.
- For Capture, create a minimal Inbox entry and return to the loop.
- For Interrupt, first record current action, observed feedback, and the exact restart action.
- When execution is remote, keep execution status, research feedback, and provenance separate. A submitted or completed job is not itself a conclusion.

## Feedback checkpoint

Trigger a checkpoint when any of these occurs:

- Expected Feedback is obtained;
- evidence makes the Current Question obsolete;
- progress is blocked and further effort cannot yield useful evidence;
- the user must interrupt;
- new evidence is surprising enough to require reframing.

At checkpoint:

1. State the observed feedback without embellishment.
2. Classify impact:
   - **Support**: increases confidence in the current hypothesis;
   - **Challenge**: weakens or contradicts it;
   - **Resolve**: answers the Current Question sufficiently for a decision;
   - **Surprise**: exposes a new mechanism, assumption, or question not covered by the frame.
3. Write a short reflection explaining why the evidence has that impact.
4. Derive the minimal Project State changes.
5. Propose the next Current Question and Next Action.
6. Stop by default. Continue into a new loop only when the user explicitly wants to and the new question is clear.

For remote feedback, also record the minimum provenance needed to find the evidence again: server alias, repository revision when relevant, job/run ID, artifact or log path, and observation time. Do not paste large raw logs into the local Project State.

## Close without expected feedback

Do not describe the session as failed merely because the expected result did not appear. Determine whether the outcome changed:

- the blocker;
- the feasibility of the action;
- the question definition;
- the evidence standard;
- the next action.

If nothing changed, record activity without updating `Last meaningful update` and identify the execution or question failure for later review.

## Persistence

When persistent state is active, create a Session Record and update the canonical Project State according to [state-schema.md](state-schema.md). Preserve a concise evidence excerpt or summary plus provenance in the session and compressed implications in the project file. Keep raw remote evidence on the server. Refresh `Dashboard.md` when the state, blocker, next action, or remote attention status changes.

Use the Session Checkpoint template in [output-templates.md](output-templates.md).

For server access, status vocabulary, and permission boundaries, read [remote-execution.md](remote-execution.md).
