# Daily Controller

Read this reference when choosing today's Primary, Secondary, Fallback, or Maintenance.

## Objective

Choose which feedback loop should enter execution first and remove decision vacuums after it ends or becomes blocked. Do not re-litigate weekly strategy every morning.

## Inputs

Use:

- the active Weekly Control Card;
- the latest Project States for Push and Keep-alive lines;
- current blockers and newly available feedback;
- completed-but-uninspected remote results, active-run status, and last observation time;
- today's real constraints supplied by the user;
- the active Experimental Rule, if relevant.

If no weekly card exists, produce a provisional daily plan from current states and say that weekly allocation is unresolved. Do not force a full weekly review when the user needs to start now.

## Selection logic

### Primary

Prefer the highest-value feedback-ready question, considering:

1. whether evidence is already available for interpretation;
2. whether the Next Action can begin now;
3. whether the result could change near-term research decisions;
4. deadline or collaboration constraints;
5. Keep-alive staleness and protection rules;
6. cognitive capacity available today.

A completed remote run whose result can change the next decision is often a strong Primary candidate. A pending or running job is a waiting condition; select a feedback-ready alternative and use the remote result check as a trigger, not as an all-day task.

Do not mechanically select Push 1 every day. A blocked Push should yield to a ready Push or protected Keep-alive.

### Secondary

Choose a smaller complete feedback loop for after Primary. It should be useful but not so large that it becomes a second Primary by default.

### Fallback

Choose an immediately startable alternative for a predictable Primary blocker or waiting period. Fallback prevents drift; it is not an extra commitment.

### Maintenance

Group necessary administration so it does not interrupt Primary. Include only obligations that genuinely need attention today.

## Workflow

1. Run [staleness-check.md](staleness-check.md), then scan readiness and blockers.
2. Recommend Primary, Secondary, Fallback, and Maintenance with one-line reasons.
3. Reference, rather than rewrite, the selected project's Current Question and Expected Feedback.
4. Ask for override only when hidden information could materially reverse the choice; otherwise provide the default plan.
5. If overridden, accept the change and record the reason when state is persistent.
6. When the user says they are starting, transition directly to the Research Loop and verify the Next Action is executable in the correct location. For remote work, include the server alias, workspace or artifact pointer, and exact observation or action needed without exposing credentials.
7. Refresh the Dashboard after an accepted daily plan.

Use the Daily Control Card in [output-templates.md](output-templates.md).

## Guardrails

- Do not schedule every open task.
- Do not use precise time blocks unless the user asks or an external event requires them.
- Do not make reading Primary unless it answers a Current Question and has an expected synthesis or decision.
- If the user is depleted, reduce loop scope rather than pretending full capacity.
- Once Expected Feedback is sufficient, checkpoint the Primary; do not continue because more time was reserved.
- Do not label a remote job “done” in the research sense until its expected feedback has been inspected.
- When the highest staleness alert is an overdue Keep-alive, prefer a Secondary-sized recovery loop when capacity allows; do not silently turn it into another Primary.
