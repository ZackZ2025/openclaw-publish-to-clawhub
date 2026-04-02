# Publish Checklist

Use this file when you need concrete checks or command patterns for GitHub and ClawHub publishing.

## Pre-Publish Checklist

- `SKILL.md` exists and is valid
- public-facing content is in English if the release is intended for a broad audience
- no proprietary project names remain unless the user explicitly wants them public
- no tokens, emails, secret keys, or private paths remain
- the target GitHub repo is correct
- the user understands whether the repo will be public

## Sensitive Content Sweep

Look for:

- API keys
- personal email addresses
- private local paths
- unpublished project names
- comments written only for the original author

Search common file types such as:

- `*.md`
- `*.py`
- `*.ipynb`
- config files

## GitHub Workflow

Typical steps:

```bash
git init
git remote add origin <repo-url>
git add -A
git status
git commit -m "Initial public release"
git push -u origin main
```

Prefer:

- SSH auth when already configured
- credential manager or browser login over pasting tokens

Use force-push only with explicit user confirmation.

## ClawHub Workflow

Typical checks:

```bash
clawhub --version
clawhub whoami
```

Typical publish pattern:

```bash
clawhub publish <skill-dir> \
  --slug <skill-name> \
  --name "<display name>" \
  --version <version> \
  --changelog "<summary>"
```

## Common Problems

### `SKILL.md required`

- confirm you are publishing the correct folder
- confirm the file name is exactly `SKILL.md`

### Push Rejected Because Remote Is Not Empty

- inspect the remote first
- pull and merge only if the remote files are intended to stay
- avoid overwriting remote history blindly

### ClawHub CLI Missing Or Not Logged In

- install the CLI first
- authenticate before retrying publish

## Safe Wording To Use With Users

Prefer:

- "This will publish the repository to GitHub."
- "I need your confirmation before any force-push."
- "Please complete login in the browser if prompted."

Avoid:

- asking the user to paste secrets into chat by default
- describing history rewrite as harmless
