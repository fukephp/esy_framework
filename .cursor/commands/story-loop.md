Run one product story through Loop Engineering (map → answer key → Cloud Agent brief → Bugbot).

Follow `.cursor/skills/story-loop/SKILL.md` and `.cursor/loops/PLAYBOOK.md` exactly. Those files are the source of truth.

If the user named a story id or title after this command, use that as the unit of work. Otherwise ask which story from the stories source named in `.cursor/CONTEXT.md`.

Do not invent product scope or architecture. Do not start a coding Cloud Agent until an answer key is approved and the app root has concrete verify commands. Prefer grill-me when decisions are still open.
