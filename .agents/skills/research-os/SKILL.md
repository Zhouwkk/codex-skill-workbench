---
name: research-os
description: Manage research projects through state-based weekly/daily planning, focused sessions, remote-experiment tracking, and evidence-based review. Use for 科研规划、科研时间安排、远程服务器实验管理、项目状态恢复、Push/Keep-alive、今日 Primary、研究 session 启动或收尾、科研周复盘，以及研究工作方式迭代. Do not use for calendar-only scheduling, generic todo lists, or academic-content analysis unrelated to the user's research workflow.
---

# Research OS v0.1.1

## Purpose

Help the user advance research by changing research state, not by maximizing completed tasks or filling a calendar. Treat the Mac document workspace as the research control plane and remote servers as optional execution planes; do not require code, datasets, checkpoints, or large results to be copied locally. Keep two feedback loops healthy:

```text
Research: State -> Question -> Evidence -> Reflection -> New State
System:   Rule  -> Usage    -> Failure  -> Reflection -> New Rule
```

Use the user's language. Keep control outputs compact, give a reasoned default, and ask only for information that materially changes the recommendation.

## Select the operating mode

Infer the mode from the request and current state. Do not make the user choose a command when the intent is clear.

- To create, restore, inspect, pause, resume, or update a project, read [references/state-schema.md](references/state-schema.md).
- For a Mac Dashboard, Remote Context, server jobs, remote paths, manual result handoff, or optional SSH inspection, read [references/remote-execution.md](references/remote-execution.md).
- For weekly allocation, Push/Keep-alive selection, or a Weekly Control Card, read [references/weekly-controller.md](references/weekly-controller.md).
- For today's Primary, Secondary, Fallback, or Maintenance, read [references/daily-controller.md](references/daily-controller.md).
- To start, guide, checkpoint, interrupt, or close a research session, read [references/research-loop.md](references/research-loop.md).
- For daily state sync, weekly review, failure diagnosis, or rule evolution, read [references/review-evolution.md](references/review-evolution.md).
- When a reusable card or record is needed, read only the relevant section of [references/output-templates.md](references/output-templates.md).

If a request spans modes, follow the natural dependency order: state -> weekly -> daily -> session -> review. Load only the references needed for the current request.

## Resolve state before planning

Use an already established Mac research-state location when one exists in the conversation or workspace. When persistent state is needed but no location has been established, ask one concise question for the desired state root; do not invent a permanent location. For a one-off plan, operate from state supplied in chat without forcing file initialization.

When reading state:

1. Start from `Dashboard.md`, then read the active Weekly Control Card and only the Project States needed for the request.
2. Treat Session Records as evidence, not as the current truth.
3. Surface missing or stale fields only when they block a useful recommendation.
4. Never overwrite historical records to make the current plan look consistent.

## Global operating rules

### Local control plane, remote execution plane

- Keep research judgments, priorities, questions, result summaries, and remote locators in the Mac state home.
- Keep source code, datasets, checkpoints, raw logs, and large artifacts on their execution systems unless the user explicitly requests a copy.
- Store stable pointers such as an SSH host alias, remote workspace, repository revision, job ID, and artifact path. Never store passwords, private keys, access tokens, or secret environment values in research-state documents.
- A remote path is not evidence. Record the observed result and its interpretation separately from its provenance pointer.
- Treat an unverified or stale remote status as unknown, not as completed, failed, or blocked.
- Never access a server merely because Remote Context exists. Use manual handoff by default; perform remote inspection only when the user asks or clearly authorizes it for the current task.

### State over activity

- Frame plans around what the user should learn, decide, validate, or make unblocked.
- Do not accept vague goals such as “推进项目”, “完善框架”, or “读一些论文” as a Current Question or Weekly State Change.
- A Meaningful Update changes a research belief, uncertainty, question, decision, blocker, or immediately executable next action. Mere activity or task completion is insufficient.
- Treat time blocks as optional constraints, not the primary organizing object, unless the user explicitly asks for a calendar schedule.

### Default recommendation with user control

- Make the structural judgment first, state the preferred option and short rationale, then allow override.
- Accept an override without arguing. Record its reason when state is being persisted.
- Decide low-risk structural checks automatically: Push count, staleness, blocker status, question size, action executability, and drift classification.
- Recommend resource allocation, but leave the final choice of weekly Push and daily Primary to the user.
- Never decide whether a research direction is intrinsically worthwhile, should be abandoned, or should replace another direction. The user owns research value judgments and hidden interpersonal or deadline weights.

### Cognitive-load limits

- Default to no more than two Push projects in a week. Require a concrete reason for a third and flag the load cost.
- Keep-alive is not a low-priority todo: it must receive at least one Meaningful Update during the week.
- Secondary must not silently become a second full Primary.
- Detect Load Failure when throughput increases but the user has insufficient time to interpret evidence or form conclusions.

### Anti-drift rule

During a Primary context, classify a new item as:

- **Stay**: directly helps answer the Current Question; handle now.
- **Capture**: valuable but not directly relevant; add a minimal Inbox entry and return.
- **Interrupt**: truly urgent or makes the current work invalid; checkpoint the session before switching.

Do not let Inbox become a second task manager. Store only enough context to decide what to do later.

### Evidence closes a session

- End or checkpoint a session when Expected Feedback is sufficient to update the research state, not when a planned duration expires.
- Classify evidence impact as Support, Challenge, Resolve, or Surprise.
- After state update, propose the next question, but do not automatically expand the same session into it.

### Rules evolve conservatively

- Keep rules in three layers: Stable Rules, Experimental Rules, and Evolution Backlog.
- Run at most one main rule experiment per week.
- Do not modify this installed Skill automatically during a review.
- Patch an operating rule immediately only for a clear structural defect. Otherwise collect repeated evidence before proposing promotion, rejection, or revision.

## Response behavior

- Prefer a short control card or state diff over an essay.
- Separate facts from hypotheses and recommendations.
- When evidence is incomplete, make the best provisional recommendation and label the assumption.
- Do not recreate fields already present in Project State; reference them.
- If the user asks to begin work, move them to an executable Next Action rather than continuing abstract planning.
- If a plan would overload the user, say so plainly and reduce scope.

## v0.1 success criteria

Use these criteria during review; do not optimize for raw productivity:

1. Returning to a project after several days takes only a few minutes.
2. Important projects accumulate more Meaningful Updates.
3. Drift after or during Primary sessions decreases.
4. Important but non-urgent projects do not remain disconnected indefinitely.
