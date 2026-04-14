# agent-skills

Shared agent skills repository.

## Structure

- `registry.yaml`: minimal metadata for globally registered skills
- `<skill-name>/`: shared skill directories discovered directly from `~/agent-skills/<skill-name>/`

## Rules

- Real working skills stay in each agent's own skills directory.
- Shared global skills live directly in the repository root as normal directories.
- Each shared skill should use the layout `~/agent-skills/<skill-name>/SKILL.md`.
- `registry.yaml` records only `updated_at`.

## Team Use

Clone this repository, then use skills discovered from `~/agent-skills`.
Add a shared skill by creating a new directory at `~/agent-skills/<skill-name>/`
with a `SKILL.md` file.
Register or update that skill's metadata in `registry.yaml` when needed.
