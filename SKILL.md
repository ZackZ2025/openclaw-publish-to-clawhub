---
name: publish-to-clawhub
description: |
  Prepare and publish an OpenClaw skill to GitHub and ClawHub, including English cleanup, sensitive-content review, Git setup, and publish checks.

  Use this skill when the user wants to release a skill publicly, sync a local skill to GitHub, internationalize a Chinese skill before publishing, or publish to ClawHub with a safer and more repeatable workflow.
---

# Publish To ClawHub

Use this skill when a local skill is ready to be cleaned up and released.

Typical requests:

- "Publish this skill to ClawHub."
- "Help me put this skill on GitHub and ClawHub."
- "Convert this skill to English and prepare it for release."

## Safety First

This workflow can involve:

- GitHub authentication
- git push to a public remote
- optional history rewriting
- ClawHub CLI publishing

Rules:

- never ask the user to paste a long-lived token into chat unless there is no safer option
- prefer browser login, credential manager, or SSH when available
- never store credentials in files
- never force-push without explicit user confirmation

## Prerequisites

Confirm these before publishing:

- the skill exists locally
- `SKILL.md` is present
- GitHub repo target is known or will be created
- ClawHub CLI is installed and logged in if ClawHub publishing is required

Detailed checks are in [references/publish-checklist.md](./references/publish-checklist.md).

## Workflow

### 1. Inspect The Skill

Review the skill folder for:

- non-English content that should be internationalized
- private or proprietary references
- user-specific file paths
- tokens, emails, or placeholders that should not be published

Check `SKILL.md`, scripts, notebooks, and any user-facing documentation that will ship with the repo.

### 2. Normalize Public-Facing Content

Before publishing:

- convert the skill description and instructions to clear English if the goal is public distribution
- replace proprietary names with generic placeholders when needed
- remove secrets, personal addresses, and private identifiers
- make examples understandable to an outside user

Keep `SKILL.md` focused on how the AI should use the skill, not on project history.

### 3. Prepare GitHub Publishing

If the repo does not exist yet:

- ask the user to create an empty GitHub repo or create one through their preferred GitHub workflow
- prefer an empty remote to avoid unnecessary merge conflicts

Then:

- initialize git if needed
- set the remote
- stage files deliberately
- review what is about to be published
- create a clear initial commit

Use SSH or a local credential helper when possible. HTTPS with manual login is acceptable if needed.

### 4. Push Safely

Before pushing:

- confirm the remote is the intended repository
- confirm that no secrets or proprietary files are staged
- explain clearly if the push will make the repo public

Never run `git push -f` unless the user explicitly agrees after understanding the risk.

### 5. Publish To ClawHub

If the user wants ClawHub publication:

- verify the CLI is installed
- verify login status
- run the publish command with a clear version and changelog
- confirm the published page or package identifier afterward

### 6. Report What Happened

Summarize:

- what files were cleaned or changed
- whether GitHub push succeeded
- whether ClawHub publish succeeded
- any follow-up steps still needed from the user

## Decision Rules

- If the skill is still private or contains sensitive material, stop before publishing.
- If the user only wants GitHub backup, skip ClawHub publishing.
- If ClawHub CLI is missing, explain the blocker and continue with GitHub prep if useful.
- If the remote repo already contains conflicting starter files, resolve carefully rather than overwriting blindly.

## Common Failure Modes

Use [references/publish-checklist.md](./references/publish-checklist.md) for:

- pre-publish checklist
- common errors
- safe credential guidance
- suggested commands
