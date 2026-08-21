# Weekly Controller

Read this reference when allocating the week, creating a Weekly Control Card, or deciding Push and Keep-alive roles.

## Objective

Allocate scarce cognitive capacity to the feedback loops most worth advancing. Do not build a weekly todo list or maximize calendar utilization.

## Inputs

Read:

- Active Project States only;
- the prior Weekly Control Card and latest review, if available;
- Stable and Experimental Rules;
- explicit deadlines, collaborations, meetings, compute/data waiting conditions, and personal capacity constraints supplied by the user.
- Remote Context for active computational projects, including last-observed run state and completed-but-uninspected results.

Do not scan Paused, Completed, or every Incubating idea unless the user asks for portfolio review.

## Workflow

### 1. Scan readiness and constraints

For each active project, assess without inventing a numeric score:

- **Urgency**: deadline or external commitment;
- **Importance**: user-established long-term value;
- **Feedback readiness**: clear Current Question, Expected Feedback, and executable Next Action;
- **Staleness**: time since the last Meaningful Update;
- **Blocker**: whether additional effort can currently produce feedback;
- **Remote readiness**: whether a run is still pending/running, completed but uninspected, failed but untriaged, stale, or unknown;
- **Cognitive load**: interpretation and context cost relative to available capacity.

State the decisive reasons. Do not treat urgency as the only factor.

### 2. Recommend allocation

- Recommend at most two Push projects by default.
- Select a Keep-alive when an important active project should not consume major capacity but must remain connected.
- Put directed learning under Build only when it has a question and expected cognitive output.
- Put required low-cognition obligations under Maintenance.
- Put blocked projects on Watchlist rather than assigning activity for appearance's sake.
- Treat completed-but-uninspected remote results as feedback-ready work; treat merely running jobs as waiting conditions, not as evidence of progress.

Give a default allocation and allow override. When recording an override, include its reason.

### 3. Define weekly state changes

For every Push, write one desired state change describing what should be known, decided, validated, or unblocked by week's end.

For Keep-alive, define one Minimum Feedback that would count as a Meaningful Update.

Reject or compress goals that:

- merely name an activity;
- contain several independent questions;
- have no observable feedback;
- remain blocked;
- are unlikely to yield interpretable evidence within the week.

### 4. Check executability

Each Push and Keep-alive must have:

- one Current Question;
- one Expected Feedback;
- one immediately executable Next Action;
- a clear blocker state.

If these are missing, repair the state before finalizing the card. Ask the user only for research judgments or hidden constraints that cannot be inferred.

### 5. Produce and persist the card

Use the Weekly Control Card in [output-templates.md](output-templates.md). Keep it short enough to scan daily. Update each Active Project State's Weekly mode only after the allocation is accepted or the user has clearly delegated that choice. Then refresh `Dashboard.md` from the accepted card and canonical Project States; do not copy full remote inventories into the weekly card.

## Special cases

- A new high-urgency request does not automatically become a third Push. First consider replacing a Push, making it Maintenance, or acknowledging explicit overload.
- A Push that is waiting on experiments or collaborators may temporarily yield daily priority without losing weekly importance.
- A remote job with stale or unknown status must not be treated as blocked, failed, or complete until observed; place the exact status check on Watchlist.
- A Keep-alive that receives its Minimum Feedback early does not automatically become a Push.
- If two Push projects already exceed capacity, recommend one Push plus one lighter protected line.
- Apply at most one active Experimental Rule to weekly allocation unless the user explicitly ends or replaces the existing experiment.
