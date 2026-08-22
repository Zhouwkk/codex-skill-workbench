# Server Capture

Read this reference when Research OS is running inside a server project, when the user asks to create or update `RESEARCH_STATE.md`, or when a server snapshot is being imported into the local Research OS.

## Purpose and boundary

Server Capture is a lightweight execution-state mode. It converts the latest run, result, or failure into one compact handoff file that can be copied or pasted into the local control plane.

Enter this mode only when the user explicitly says the current environment is the server project, asks for Server Capture, or asks to update/import `RESEARCH_STATE.md`. A remote path appearing in a Mac planning conversation is not enough to switch modes.

In this mode:

- maintain one file at `<project-root>/RESEARCH_STATE.md` unless the user names another path;
- capture execution-facing state and evidence provenance;
- update the same file rather than building a server-side archive;
- do not create `Dashboard.md`, `projects/`, `sessions/`, `weekly/`, `reviews/`, `inbox.md`, or `rules.md`;
- do not select Push, Keep-alive, Primary, or other cross-project priorities;
- do not change lifecycle or research-direction decisions on behalf of the user;
- do not run, cancel, restart, or modify experiments unless separately requested.

The Mac Project State remains canonical after import. The server snapshot is a transport document, not a second planning database.

## Server state file

Keep the file short enough to inspect and copy directly. Omit unknown optional fields rather than guessing.

```markdown
# Research State Handoff — <project>

- Mode: Server Capture
- Project key: <stable slug shared with the local project when known>
- Capture ID: <YYYY-MM-DD-HHMM-run-or-result-label>
- Updated: <timestamp with timezone>
- Execution host: <server alias or hostname>
- Workspace: <absolute project path>
- Revision: <branch and/or commit, plus dirty state when observed, or Unknown>

## Current experiment question
<the one question this execution loop is testing>

## Expected feedback
<the observable comparison, metric, failure, or artifact>

## Latest execution
- Run or job: <ID and purpose>
- Status: <Pending | Running | Completed, uninspected | Completed, inspected | Failed, untriaged | Failed, triaged | Blocked | Unknown>
- Artifact or log: <absolute path>
- Observed: <timestamp>

## Latest feedback
<concise observed result, or “Not yet interpreted”>

## Interpretation
- Evidence status: <Interpretable | Execution only | Uncertain>
- Impact: <Support | Challenge | Resolve | Surprise | Not assessed>
- Execution-backed conclusion: <what the evidence supports, with uncertainty>
- Open uncertainty: <what remains unresolved>

## Execution next action
<one immediately executable run, inspection, or comparison>
```

`Capture ID` is a readable identity for the latest handoff, not a checksum. Reuse it while correcting the same capture; create a new one when recording a different result or materially newer observation.

## Capture workflow on the server

1. Resolve the exact project root and existing `RESEARCH_STATE.md`. Use the current directory only when the user identifies it as the project root.
2. Read the existing snapshot before updating it. Inspect only the named result, metric, log, job, or repository state needed for the request.
3. Separate execution status from research feedback. A completed job with no interpreted result is `Completed, uninspected`, not evidence for a conclusion.
4. Replace stale current fields with the latest compact state. Do not append chronological logs or copy raw output into the file.
5. Preserve prior execution-backed conclusions only when the new result has not challenged them. Mark uncertain interpretation instead of silently deciding research direction.
6. Report the file path, Capture ID, what changed, and whether the snapshot contains interpretable feedback or execution status only.

`RESEARCH_STATE.md` may contain unpublished results and server paths. Do not add it to Git, edit `.gitignore`, or publish it unless the user explicitly asks. If it appears as an untracked file in a repository, simply tell the user so they can choose how to transport or exclude it.

When the user supplies a result summary, use it as evidence and preserve its provenance. When the user asks Codex to inspect a result file, keep the read scope within the named project and object. Do not broadly scan the server because the Skill is installed there.

## Import workflow on the Mac

The user may paste the snapshot, attach it, or copy it to any local path accessible to Codex. Do not require a permanent import directory.

1. Match `Project key` to one local Project State. If it is missing or ambiguous, ask one concise mapping question.
2. Compare `Capture ID` with `Last imported capture` in the local Remote Context. If it is unchanged, report that no new import is needed; do not create a duplicate Session Record. If the snapshot's `Updated` time is older than the last remote observation, treat it as stale and do not overwrite newer state unless the user confirms the rollback.
3. Update execution status, revision, artifact pointers, observation time, and remote next check from the snapshot.
4. If feedback is interpretable, create a local Session Record and classify its impact. Propose the resulting Project State diff before persisting when the interpretation changes a hypothesis, question, or research decision and remains uncertain.
5. If the snapshot contains execution status only, update Remote Context without claiming a Meaningful Update or creating an evidence Session Record.
6. Never overwrite local `Status`, `Weekly mode`, allocation, rules, or user-owned research decisions from a server snapshot.
7. Record the accepted `Capture ID` as `Last imported capture`, then refresh the Dashboard when the imported state changes current attention.

The copied `RESEARCH_STATE.md` is not itself the local Project State. Its durable implications belong in the canonical project file; its evidence belongs in a Session Record when applicable.
