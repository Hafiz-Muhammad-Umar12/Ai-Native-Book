---
id: 3
title: Create GitHub Actions Workflow
stage: misc
date: 2025-11-29
surface: agent
model: claude-sonnet-4-5-20250929
feature: AI-Native-Hackathon-Deployment
branch: main
user: unknown
command: 'Task: Create GitHub Actions Workflow for Deployment.

Action: Create a file `.github/workflows/deploy.yml` with this EXACT content:

name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main
    paths:
      - 'frontend/**'

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: 18
          cache: 'npm'
          cache-dependency-path: frontend/package-lock.json
      - name: Install dependencies
        run: cd frontend && npm install
      - name: Build
        run: cd frontend && npm run build
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: frontend/build

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4'
labels: ["github-actions", "deployment", "workflow"]
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

Task: Create GitHub Actions Workflow for Deployment.

Action: Create a file `.github/workflows/deploy.yml` with this EXACT content:

name: Deploy to GitHub Pages

on:
  push:
    branches:
      - main
    paths:
      - 'frontend/**'

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: 18
          cache: 'npm'
          cache-dependency-path: frontend/package-lock.json
      - name: Install dependencies
        run: cd frontend && npm install
      - name: Build
        run: cd frontend && npm run build
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: frontend/build

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4

## Response snapshot

I have successfully created the GitHub Actions workflow file at `.github/workflows/deploy.yml`.

## Outcome

- ✅ Impact: Created GitHub Actions workflow for deployment.
- 🧪 Tests: N/A
- 📁 Files: `.github/workflows/deploy.yml` created.
- 🔁 Next prompts: Awaiting further instructions from the user.
- 🧠 Reflection: Successfully created the deployment workflow file as requested.

## Evaluation notes (flywheel)

- Failure modes observed: N/A
- Graders run and results (PASS/FAIL): N/A
- Prompt variant (if applicable): N/A
- Next experiment (smallest change to try): N/A
