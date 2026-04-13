---
name: global-skill-manager
description: |
  Manage the shared global skill discovery directory by adding or removing
  symlinks for existing agent-owned skills, and publish shareable copies for
  version control. It can also clone the shared skills repo and pull updates.

  Triggers when user mentions:
  - "add this skill to global skills"
  - "publish this skill to the global skills directory"
  - "remove this skill from global skills"
  - "clone the shared skills repo"
  - "pull the shared skills repo"
---

Use this skill only when the user gives an explicit instruction to add, remove,
publish, unpublish, clone, or pull a skill in the global skills directory.

## Purpose

The global skills directory has two parts:

- Discovery layer: `~/agent-skills`
- Published copies: `~/agent-skills/.published`

The discovery layer contains symlinks to real skills that remain in each agent's
own skills directory. The published directory contains real copies for Git-based
sharing and version control. The same repo can also be cloned and updated from a
remote.

- Discovery directory: `~/agent-skills`
- Published directory: `~/agent-skills/.published`
- Metadata file: `~/agent-skills/registry.yaml`

The real working skill content must stay in its source directory. Never copy a
skill into the discovery directory root.

## Hard Rules

- Only act on an explicit user instruction to add, remove, publish, or
  unpublish a skill.
- Only act on an explicit user instruction to clone the shared skills repo,
  or pull the shared skills repo.
- In `~/agent-skills`, only create or remove symlinks and update
  `registry.yaml`.
- Never copy a skill directory or any of its files into `~/agent-skills`.
- Only create published copies under `~/agent-skills/.published`.
- Never rewrite, edit, or move a skill in the discovery directory.
- Never modify the contents of the source skill as part of registration or
  publishing.
- If a target name already exists in `~/agent-skills`, ask the user what to do
  before making any change.
- If a target name already exists in `~/agent-skills/.published`, ask the user
  what to do before making any change.
- If the clone target already exists, ask the user what to do before making any
  change.
- If it is unclear which source skill the user means, ask one short clarifying
  question.

## Register A Skill In Global Discovery

1. Confirm the user explicitly asked to add or publish a skill globally.
2. Identify the source skill directory.
3. Verify the source directory contains `SKILL.md`.
4. Choose the global link name. By default, use the source folder name.
5. Check whether `~/agent-skills/<name>` already exists.
6. If it exists, stop and ask the user whether to keep the existing one, replace
   it, or use a different name.
7. Create a symlink from `~/agent-skills/<name>` to the source skill directory.
8. Update `~/agent-skills/registry.yaml` with:
   - skill name
   - source path
   - updated_at in ISO 8601 format

Example symlink command:

```bash
ln -s "/absolute/path/to/source-skill" "/Users/anthony/agent-skills/skill-name"
```

Example metadata entry:

```yaml
skills:
  skill-name:
    source: /absolute/path/to/source-skill
    updated_at: 2026-04-11T14:30:00Z
```

## Remove A Skill From Global Discovery

1. Confirm the user explicitly asked to remove a skill from global skills.
2. Check whether `~/agent-skills/<name>` exists.
3. If the entry does not exist, tell the user and stop.
4. Remove only the symlink in `~/agent-skills`.
5. Remove that skill entry from `~/agent-skills/registry.yaml`.
6. Do not delete or modify the source skill directory.

Example remove command:

```bash
rm "/Users/anthony/agent-skills/skill-name"
```

## Publish A Shareable Copy

Use this when the user explicitly asks to publish a skill for Git-based sharing
or team reuse.

1. Confirm the user explicitly asked to publish a skill copy.
2. Identify the real source skill directory.
3. Verify the source directory contains `SKILL.md`.
4. Choose the published name. By default, use the source folder name.
5. Check whether `~/agent-skills/.published/<name>` already exists.
6. If it exists, stop and ask the user whether to keep the existing one,
   replace it, or use a different name.
7. Copy the source skill directory to `~/agent-skills/.published/<name>`.
8. Do not change the discovery symlink unless the user separately asked for
   registration.
9. Do not add any extra metadata fields to `registry.yaml`.

Example publish command:

```bash
cp -R "/absolute/path/to/source-skill" "/Users/anthony/agent-skills/.published/skill-name"
```

## Remove A Published Copy

Use this when the user explicitly asks to remove a published copy from the
shared Git-tracked directory.

1. Confirm the user explicitly asked to remove the published copy.
2. Check whether `~/agent-skills/.published/<name>` exists.
3. If the published entry does not exist, tell the user and stop.
4. Remove only the published copy in `~/agent-skills/.published/<name>`.
5. Do not remove the discovery symlink unless the user separately asked for it.
6. Do not modify the source skill directory.

Example unpublish command:

```bash
rm -r "/Users/anthony/agent-skills/.published/skill-name"
```

## Clone The Shared Skills Repo

Use this when the user explicitly asks to set up the shared skills repo on a
machine for the first time.

1. Confirm the user explicitly asked to clone the shared repo.
2. Identify the remote URL and target directory. By default, use
   `~/agent-skills`.
3. If the target directory already exists, stop and ask the user what to do.
4. Clone the repo into the target directory.
5. After clone, tell the user that published skills live under
   `~/agent-skills/.published` and can be enabled by creating symlinks in
   `~/agent-skills/`.

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
6. After pull, tell the user to enable any newly published skills by creating
   symlinks in `~/agent-skills/` if needed.

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
- The published path does not already conflict, unless the user has chosen how
  to resolve the conflict.
- Registration only affects the symlink and the metadata file.
- Publishing only affects `~/agent-skills/.published/<name>`.
- Cloning only affects the requested target directory.
- Pulling only affects the existing shared repo checkout.

## Notes

- Treat skills stored under project directories as valid source skills if the
  user wants to publish them globally.
- The global directory is not a source of truth. It is only a shared discovery
  index.
- Keep registry entries minimal. Only record `source` and `updated_at`.
- `~/agent-skills/.published` is not part of skill discovery. It exists only to
  store shareable copies for Git and team sync.
