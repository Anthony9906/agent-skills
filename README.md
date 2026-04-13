# agent-skills

Shared agent skills repository.

## Structure

- `registry.yaml`: minimal metadata for globally registered skills
- `.published/`: Git-tracked skill copies for sharing and version control
- `global-skill-manager`: tracked bootstrap symlink to the published manager skill
- other repo root symlinks: local discovery-only entries used on one machine

## Rules

- Real working skills stay in each agent's own skills directory.
- `global-skill-manager` is tracked as a relative symlink so new clones can discover it immediately.
- Other root-level global skills are local discovery symlinks and are not tracked by Git.
- Shareable skills are copied into `.published/` and committed to this repository.
- `registry.yaml` records only `updated_at`.

## Team Use

Clone this repository, then use skills discovered from `~/agent-skills`.
Additional published skills can be enabled by adding root-level symlinks that
point to `.published/<skill-name>`.
