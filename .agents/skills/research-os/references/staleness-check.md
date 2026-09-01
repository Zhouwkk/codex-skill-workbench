# Staleness Check

Read this reference whenever Research OS reads persistent Mac state. The check is opportunistic: it runs as part of an ordinary invocation and never claims to operate in the background.

Do not run it for a one-off plan with no persistent state or while operating only in Server Capture mode. Run it after a server snapshot is imported into the Mac state home.

## Objective

Surface an important feedback loop that has quietly lost contact, without turning Research OS into a generic reminder system or interrupting focused work with a portfolio scan.

Use the current date in the user's timezone and state already needed for the request:

- Dashboard active week and synchronization date;
- current Weekly Control Card;
- Project State `Status`, `Weekly mode`, `Last meaningful update`, `Blocker`, and `Next action`;
- explicit cadence or deadline when present;
- Remote Context status, observation time, and exact next check when relevant.

Do not read every Paused, Completed, or Incubating project merely to perform this check.

## 1. Check control-plane freshness

Compare the Dashboard's active week and linked Weekly Control Card with the current ISO week.

- If the active card belongs to an earlier week, classify the control plane as stale and surface this before project-level alerts. Recommend refreshing weekly allocation; do not pretend the old Push or Keep-alive roles still represent the current week.
- If no Weekly Control Card exists, mention unresolved allocation only in planning, Dashboard, or closure contexts. Do not block an executable one-off session.

## 2. Select eligible lines

Check only:

- Active projects currently assigned Push or Keep-alive;
- another Active project with an explicit activation cadence or near deadline already recorded in state;
- a named remote run whose recorded next-check condition has passed.

Exclude by default:

- Paused, Completed, and Incubating projects;
- Maintenance and ordinary Watchlist items with no explicit cadence or deadline;
- projects with a current, specific Blocker that additional effort cannot resolve;
- recently observed Pending or Running experiments that are legitimately waiting.

If `Last meaningful update` is missing, report incomplete state rather than asserting that the project is stalled.

## 3. Apply role-aware triggers

An explicit cadence, due condition, collaborator commitment, or deadline overrides these defaults.

### Keep-alive

Classify it as:

- **Overdue** when it has received no Meaningful Update within its explicit cadence, or within the previous seven days when the weekly role is the only cadence;
- **At risk** when it has no Meaningful Update in the current week and the week has reached Thursday or later.

Activity alone does not reset the clock. The update must change a belief, uncertainty, question, decision, blocker, or immediately executable Next Action.

### Push

Alert when an unblocked Push has no Meaningful Update for seven days and still has an executable Next Action. If a result is already available but uninspected, classify it as feedback waiting for interpretation rather than lack of work.

### Remote execution

Do not use an arbitrary age threshold for remote jobs. Alert only when a recorded next-check time or condition has passed, or when planning depends on a status whose observation is explicitly stale. Label this `Status check needed`, not research stagnation.

## 4. Distinguish waiting from neglect

Before alerting, decide which description is supported:

- **Stalled**: an executable feedback loop exists but has not received a Meaningful Update within its role or cadence;
- **At risk**: the activation window is nearing its end;
- **Waiting**: a specific current external or compute condition prevents feedback;
- **Status check needed**: the waiting condition may have changed, but remote or collaborator status is stale;
- **State incomplete**: the dates, cadence, blocker, or Next Action are insufficient to judge.

Only the first two are progress reminders. The others should request the smallest status or state clarification needed.

## 5. Choose and surface one alert

Show at most one alert per response. Prioritize:

1. stale Weekly Control Card;
2. overdue Keep-alive;
3. near-deadline commitment at risk;
4. unblocked Push that is stalled;
5. remote status check needed.

Keep the output compact:

```markdown
## Staleness alert
- <project or control plane>: <specific dated evidence>
- Interpretation: <Stalled | At risk | Status check needed | State incomplete>
- Recover with: <one smallest executable action or planning correction>
```

Do not moralize, score the user, or list every stale project. Mention an additional count only when it materially affects allocation.

Surface the alert during Dashboard review, weekly/daily planning, daily closure, or state synchronization. During a focused research session, do not interrupt the current loop; append the alert at checkpoint or closure unless it makes the current action invalid.

When refreshing `Dashboard.md`, keep at most one unresolved item under `Staleness attention` and remove it once the underlying state no longer meets the trigger.
