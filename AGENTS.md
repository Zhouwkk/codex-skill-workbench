# Project instructions

This repository is the source of truth for personal Codex skill development.

- Create skills only under `.agents/skills/<skill-name>/` unless the user explicitly requests another location.
- Use `$skill-creator` for new skills and substantial skill revisions.
- Keep every skill focused: include only guidance and resources that materially improve its target workflow.
- A skill must contain `SKILL.md` with valid `name` and `description` frontmatter.
- Add `scripts/`, `references/`, `assets/`, and `agents/openai.yaml` only when the skill needs them.
- Validate changed skills and run any new or modified scripts before reporting completion.
- Keep repository-wide planning notes in `notes/`. Every skill intended for sharing must include a user-facing `README.md` covering installation and concrete usage; do not add changelogs or other ancillary files unless specifically required.
- Preserve unrelated work and keep commits scoped to one skill or one repository-maintenance change.

## Skill release lifecycle

Treat a request to create or update a skill in this repository as standing authorization to complete its release lifecycle unless the user explicitly opts out for that request.

1. Make the repository copy under `.agents/skills/<skill-name>/` the source of truth. Do not develop only in the user-level installed copy.
2. Validate the changed skill and run every new or modified script that materially affects it.
3. Commit only that skill and its directly required repository metadata or documentation in one scoped commit. Never include unrelated working-tree changes.
4. Push the commit to the repository's configured GitHub origin without waiting for a separate user request.
5. After the push succeeds, install a newly created skill or update the existing user-level copy at `/Users/zhouwkk/.codex/skills/<skill-name>/` from the committed GitHub version. Use a recoverable replacement when updating an existing installation, and verify that the installed files match the committed repository copy.
6. Report the commit, push, and local-install result together. If validation, push, authentication, network access, or installation is blocked, preserve completed work and report the exact unfinished step instead of claiming the lifecycle is complete.
