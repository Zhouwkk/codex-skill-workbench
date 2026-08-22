# Remote Execution

Read this reference when a project runs on a server, when building or refreshing the Mac Dashboard, or when the user asks to inspect remote jobs, logs, repositories, or artifacts.

## Architecture

Use two explicit planes:

```text
Mac control plane
  Dashboard, Project State, Weekly/Daily cards, Session Records, rules
                         |
                         | stable locators + summarized feedback
                         v
Remote execution plane
  code, data, environments, jobs, raw logs, checkpoints, large artifacts
  optional RESEARCH_STATE.md handoff snapshot
```

The Mac state home must remain usable when the server is offline. It should say what matters, where execution lives, what was last observed, and what to check next without mirroring the remote filesystem.

When Research OS is also installed on the server, use the single-file protocol in [server-capture.md](server-capture.md). The snapshot supplements manual handoff; it does not make the server a second control plane.

## Remote Context schema

Add this section to a Project State only when relevant. Omit unknown or unused fields rather than guessing.

```markdown
## Remote Context

- Execution location: Remote | Hybrid
- Access mode: Manual handoff | SSH available
- Server alias: <existing SSH host alias or human-readable server name>
- Remote workspace: <absolute project path>
- Repository: <remote repository path or URL, if useful>
- Revision: <branch and/or commit associated with current evidence>
- Environment: <environment name or activation hint, without secrets>
- Scheduler: Slurm | PBS | LSF | None | Other
- Active runs: <job/run IDs with status and purpose>
- Artifact pointers: <remote paths for current results, logs, or checkpoints>
- Last remote observation: <timestamp and observation source>
- Remote next check: <one exact status or result to inspect>
- Last imported capture: <Capture ID from RESEARCH_STATE.md, if used>
```

### Locator discipline

- Prefer stable SSH aliases over IP addresses when the user already has them.
- Use absolute remote paths.
- Pair every job/run ID with its purpose; an unexplained number is not useful state.
- Pair every status with an observed-at time. Remote status becomes stale; do not present stale status as current.
- Pair result claims with provenance when available: server alias, revision, run/job ID, artifact path, and observation time.
- Never store passwords, private keys, tokens, secret environment values, or copied credential files.
- `SSH available` records a connection capability, not standing authorization for remote actions. Resolve scope and permission again for each task.

## Manual handoff workflow

Manual handoff is the default and requires no server access by Codex.

1. The Mac control plane selects a Current Question and remote Next Action.
2. The user runs or inspects work on the server.
3. The user returns the minimum useful evidence directly or through a server-generated `RESEARCH_STATE.md`: result summary, relevant metric or failure, run/job ID, artifact or log path, revision when relevant, and observation time.
4. Separate the handoff into:
   - **execution status**: submitted, pending, running, completed, failed, or unknown;
   - **research feedback**: what the result shows;
   - **provenance**: where the evidence can be found again.
5. Update the Session Record, Project State, and Dashboard. Do not copy raw logs into Project State.

If the user reports only “the job finished,” update execution status and the next inspection action. Do not invent a research conclusion.

## Optional SSH inspection

Use remote inspection only when the user asks or clearly authorizes it for the current task and an existing access method is available.

Before connecting, resolve:

- the exact server alias;
- the exact project or artifact path;
- the requested observation;
- whether the operation is read-only or mutating.

For read-only inspection, keep scope narrow. Appropriate examples include checking a named job, reading the tail of a named log, inspecting a named result file, or reading repository revision and status in the named workspace.

Do not silently:

- scan unrelated directories or the user's remote home;
- modify SSH configuration, keys, or known-host settings;
- install software or alter environments;
- edit code or configuration;
- submit, cancel, restart, or reprioritize jobs;
- pull, checkout, commit, or push a repository;
- delete, move, overwrite, or download large artifacts.

Those actions require an explicit request and remain bounded to the named project. A failed connection or missing path should produce an `Unknown` status and a precise next check, not repeated broad probing.

## Execution states

Use these terms consistently:

- **Pending**: accepted by a scheduler or queue but not running;
- **Running**: currently executing;
- **Completed, uninspected**: execution ended, but expected feedback has not been interpreted;
- **Completed, inspected**: execution ended and its expected feedback has been interpreted; keep it out of Dashboard attention unless a follow-up action remains;
- **Failed, untriaged**: execution failed, but the cause and research impact are not yet known;
- **Failed, triaged**: execution failed and the cause or actionable next check has been identified;
- **Blocked**: progress requires a condition outside the current executable loop;
- **Unknown**: status has not been observed recently enough.

Completion is not Meaningful Update by itself. A completed run becomes research feedback only after inspecting an interpretable result.

## Dashboard synchronization

Refresh `Dashboard.md` after an accepted weekly allocation, a changed daily Primary, a remote status transition that affects the plan, or a Project State update. Keep it concise and regenerate summaries from canonical files rather than accumulating history.

The Dashboard should show:

- active Weekly Control Card link;
- today's Primary, Secondary, and Fallback;
- Push and Keep-alive project links;
- remote runs that require attention, with last-observed time;
- waiting or blocked conditions;
- Inbox count or a short attention cue, not the full Inbox.

Use the Dashboard and Remote Context templates in [output-templates.md](output-templates.md).
