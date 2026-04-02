# Publish To ClawHub

`publish-to-clawhub` is a skill for updating and releasing local skills with a workflow that keeps the local publish directory clean while still maintaining a readable GitHub repository.

It is designed for workflows such as:

- improving a skill before release
- publishing the updated local skill to ClawHub
- using GitHub as backup and public showcase
- adding a temporary `README.md` only for GitHub presentation
- deleting the local `README.md` after the GitHub sync succeeds

## Validated Workflow

This repository now reflects a tested release flow:

1. inspect and improve the skill itself
2. publish the local skill folder to ClawHub
3. add a temporary `README.md`
4. sync the GitHub-facing copy
5. remove the local `README.md`

## What This Skill Covers

- skill cleanup before release
- English normalization for public distribution
- sensitive-content review
- ClawHub publish checks
- GitHub sync with SSH or credential-based auth
- keeping local skill folders minimal after publishing

## Repository Structure

- `SKILL.md`: core AI-facing workflow
- `agents/openai.yaml`: optional interface metadata
- `references/publish-checklist.md`: validated release order, checks, and troubleshooting

## Notes

- This workflow separates the local publish folder from the GitHub showcase copy on purpose.
- It is especially useful for users who want strict local skill cleanliness.
- SSH-based GitHub auth is recommended for long-term maintenance.
