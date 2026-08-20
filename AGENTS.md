# Project instructions

This repository is the source of truth for personal Codex skill development.

- Create skills only under `.agents/skills/<skill-name>/` unless the user explicitly requests another location.
- Use `$skill-creator` for new skills and substantial skill revisions.
- Keep every skill focused: include only guidance and resources that materially improve its target workflow.
- A skill must contain `SKILL.md` with valid `name` and `description` frontmatter.
- Add `scripts/`, `references/`, `assets/`, and `agents/openai.yaml` only when the skill needs them.
- Do not install, copy, or symlink a skill into a user-level directory unless the user explicitly requests installation.
- Validate changed skills and run any new or modified scripts before reporting completion.
- Keep repository-wide planning notes in `notes/`; do not add README or changelog files inside individual skill folders unless specifically required.
- Preserve unrelated work and keep commits scoped to one skill or one repository-maintenance change.

