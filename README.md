# demo-test

A demonstration project for learning how to use **Claude Code** alongside **Playwright** for automated browser testing. This repo is intended to help new team members get up and running quickly.

---

## Purpose

This project serves as a hands-on learning environment for the QA team to:
- Explore how to use Claude Code as an AI coding assistant
- Write and run Playwright end-to-end tests
- Practice Git workflows (branching, commits, pull requests)

---

## Prerequisites

Before you begin, make sure you have the following installed:

- [Node.js](https://nodejs.org/) (v18 or higher recommended)
- [Git](https://git-scm.com/)
- [Claude Code CLI](https://claude.ai/code) — Anthropic's AI coding assistant

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/qa-bob/demo-test.git
cd demo-test
```

### 2. Check out the develop branch

All active work happens on the `develop` branch, not `main`.

```bash
git checkout develop
```

### 3. Install dependencies

```bash
npm install
```

### 4. Install Playwright browsers

This downloads the browser binaries needed to run tests (Chromium, Firefox, WebKit).

```bash
npx playwright install
```

### 5. Run the tests

```bash
npx playwright test
```

### 6. View the test report

After running tests, open the HTML report:

```bash
npx playwright show-report
```

---

## Getting Started with Claude Code

### Install the CLI

```bash
npm install -g @anthropic-ai/claude-code
```

### Launch Claude Code in this project

From the project root directory:

```bash
claude
```

Claude Code will open in your terminal and have full context of this project. You can ask it to:
- Explain existing tests
- Write new test cases
- Debug failing tests
- Help with Git operations

### Example prompts to try

```
"Explain what the tests in the tests/ folder are doing"
"Write a new Playwright test that checks the homepage title"
"What does the playwright.config.ts file do?"
"Show me the git status and commit any changes"
```

---

## Project Structure

```
demo-test/
├── .claude/                  # Claude Code settings
├── tests/                    # Your Playwright test files
│   └── example.spec.ts       # Example test
├── tests-examples/           # Additional example tests
│   └── demo-todo-app.spec.ts # Playwright todo app demo
├── playwright.config.ts      # Playwright configuration
├── package.json              # Node.js dependencies
└── .gitignore                # Files excluded from Git
```

---

## Branch Strategy

| Branch    | Purpose                                      |
|-----------|----------------------------------------------|
| `main`    | Stable, production-ready code                |
| `develop` | Active development — all work goes here      |

When your work is ready, open a Pull Request from `develop` → `main` on GitHub.

---

## Useful Commands

| Command | Description |
|---|---|
| `npx playwright test` | Run all tests |
| `npx playwright test --headed` | Run tests with browser visible |
| `npx playwright test --ui` | Open Playwright UI mode |
| `npx playwright show-report` | View the last test report |
| `npx playwright codegen` | Record a test by clicking in a browser |
| `git status` | Check what files have changed |
| `git pull` | Get the latest changes from GitHub |

---

## Questions?

Use Claude Code — just type `claude` in your terminal and ask!
