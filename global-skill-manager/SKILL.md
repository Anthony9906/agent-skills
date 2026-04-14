---
name: global-skill-manager
description: |
  Manage the shared global skill discovery directory by adding or removing
  shared skills in place. It can also clone the shared skills repo and pull
  updates.

  Triggers when user mentions:
  - "add this skill to global skills"
  - "publish this skill to the global skills directory"
  - "remove this skill from global skills"
  - "clone the shared skills repo"
  - "pull the shared skills repo"
---

Use this skill only when the user gives an explicit instruction to add, remove,
clone, or pull a skill in the global skills directory.

## Purpose

The global skills directory is the shared discovery location.

- Global directory: `~/agent-skills`
- Metadata file: `~/agent-skills/registry.yaml`

Shared skills live directly under `~/agent-skills/<skill-name>/`.

## Hard Rules

- Only act on an explicit user instruction to add or remove a shared skill from
  local global discovery.
- Only act on an explicit user instruction to clone the shared skills repo,
  or pull the shared skills repo.
- In `~/agent-skills`, only create, remove, or update skill directories when
  the user explicitly asks.
- Shared skills should live directly in `~/agent-skills/<skill-name>/`.
- Do not redesign the global skill layout unless the user explicitly asks.
- If a target name already exists in `~/agent-skills`, ask the user what to do
  before making any change.
- If the clone target already exists, ask the user what to do before making any
  change.
- If it is unclear which shared skill the user means, ask one short clarifying
  question.

## Register A Skill In Global Discovery

1. Confirm the user explicitly asked to add or enable a shared skill globally.
2. Identify the source skill directory the user wants to add.
3. Verify the source skill directory contains `SKILL.md`.
4. Choose the global skill name. By default, use the source folder name.
5. Check whether `~/agent-skills/<name>` already exists.
6. If it exists, stop and ask the user whether to keep the existing one, replace
   it, or use a different name.
7. Create or copy the skill directory into `~/agent-skills/<name>`.
8. Update `~/agent-skills/registry.yaml` with:
   - skill name
   - updated_at in ISO 8601 format

Example copy command:

```bash
cp -R "/path/to/skill-name" "/Users/anthony/agent-skills/skill-name"
```

Example metadata entry:

```yaml
skills:
  skill-name:
    updated_at: 2026-04-11T14:30:00Z
```

## Remove A Skill From Global Discovery

1. Confirm the user explicitly asked to remove a skill from global skills.
2. Check whether `~/agent-skills/<name>` exists.
3. If the entry does not exist, tell the user and stop.
4. Remove the skill directory in `~/agent-skills`.
5. Remove that skill entry from `~/agent-skills/registry.yaml`.

Example remove command:

```bash
rm -rf "/Users/anthony/agent-skills/skill-name"
```

## Clone The Shared Skills Repo

Use this when the user explicitly asks to set up the shared skills repo on a
machine for the first time.

1. Confirm the user explicitly asked to clone the shared repo.
2. Identify the remote URL and target directory. By default, use
   `~/agent-skills`.
3. If the target directory already exists, stop and ask the user what to do.
4. Clone the repo into the target directory.
5. After clone, tell the user that shared skills are discovered directly from
   `~/agent-skills/<skill-name>/`.

Example clone command:

```bash
git clone "https://github.com/example/agent-skills.git" "/Users/anthony/agent-skills"
```

## Pull Shared Skills Repo Updates

Use this when the user explicitly asks to update an existing shared skills repo
from its GitHub remote.

1. Confirm the user explicitly asked to pull or update the shared repo.
2. Verify that `~/agent-skills` is an existing git repository.
3. Run `git status` and check for local changes.
4. If there are uncommitted local changes, stop and ask the user how to proceed.
5. Run `git pull` on the current branch.
6. After pull, tell the user that any newly pulled skill directories under
   `~/agent-skills/` are immediately discoverable.

Example commands:

```bash
git status --short
git pull
```

## Safety Checks

Before changing anything, verify all of the following:

- The source path exists.
- The source path is a skill directory with `SKILL.md`.
- The global path does not already conflict, unless the user has chosen how to
  resolve the conflict.
- Registration only affects the skill directory and the metadata file.
- Cloning only affects the requested target directory.
- Pulling only affects the existing shared repo checkout.

## Notes

- The global directory is both the shared storage location and the discovery
  location for global skills.
- Keep registry entries minimal. Only record `updated_at`.
