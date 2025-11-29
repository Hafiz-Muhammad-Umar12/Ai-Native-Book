---
id: 5
title: Fix GitHub Actions Node Version (Explicit)
stage: misc
date: 2025-11-29
surface: agent
model: claude-sonnet-4-5-20250929
feature: AI-Native-Hackathon-Deployment
branch: main
user: unknown
command: 'Task: Fix GitHub Actions Node Version (Again).

The build failed again with "Minimum Node.js version not met" because it is still using v18.
Action: Update `.github/workflows/deploy.yml` to be explicit.

1.  Find the `setup-node` step.
2.  Change `node-version: 20` to `node-version: '20'`. (Wrap it in single quotes).
3.  Also, verify the `jobs:` section has `runs-on: ubuntu-latest`.'
labels: ["github-actions", "build-fix", "node-version"]
links:
  spec: null
  ticket: null
  adr: null
  pr: null
files:
  - .github/workflows/deploy.yml
tests:

---

## Prompt

Task: Fix GitHub Actions Node Version (Again).

The build failed again with "Minimum Node.js version not met" because it is still using v18.
Action: Update `.github/workflows/deploy.yml` to be explicit.

1.  Find the `setup-node` step.
2.  Change `node-version: 20` to `node-version: '20'`. (Wrap it in single quotes).
3.  Also, verify the `jobs:` section has `runs-on: ubuntu-latest`.

## Response snapshot

I have updated the `.github/workflows/deploy.yml` file to use `node-version: '20'`. Both the `build` and `deploy` jobs are configured to run on `ubuntu-latest`.

## Outcome

- ✅ Impact: Updated Node.js version in GitHub Actions workflow with explicit quotes to resolve build issue.
- 🧪 Tests: Manual verification of `runs-on` setting.
- 📁 Files: `.github/workflows/deploy.yml` modified.
- 🔁 Next prompts: Awaiting further instructions from the user.
- 🧠 Reflection: Successfully addressed the Node.js version issue by explicitly quoting the version in the workflow file.

## Evaluation notes (flywheel)

- Failure modes observed: N/A
- Graders run and results (PASS/FAIL): N/A
- Prompt variant (if applicable): N/A
- Next experiment (smallest change to try): N/A
