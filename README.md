# Publish To ClawHub

`publish-to-clawhub` is an OpenClaw skill for preparing a local skill for public release on GitHub and ClawHub.

It is designed for workflows such as:

- cleaning a skill before public release
- converting a Chinese skill into a more international English release
- checking for sensitive or proprietary content
- publishing the final result to GitHub and ClawHub with a safer process

## What This Skill Covers

- pre-publish inspection
- English cleanup for public-facing release
- sensitive-content review
- GitHub push preparation
- ClawHub publish checks
- safer handling of credentials and force-push scenarios

## Repository Structure

- `SKILL.md`: core AI-facing release workflow
- `agents/openai.yaml`: optional Codex/OpenAI-style interface metadata
- `references/publish-checklist.md`: publishing checklist, command patterns, and failure handling

## Notes

- This skill is meant to reduce risky publishing mistakes.
- It treats GitHub authentication and force-push actions as high-caution steps.
- It is useful both for first-time release and for later updates.

## Current Release Focus

The latest local revision makes the release workflow shorter and clearer, with explicit decision rules and a dedicated checklist for safer GitHub and ClawHub publishing.
