# CLAUDE.md — demo-test

This file gives Claude Code context about this project so it can assist effectively.

## Project Overview

This is a **Playwright end-to-end testing demo project** used to teach the QA team how to write automated browser tests and how to use Claude Code as an AI coding assistant.

## What This Project Tests

Two publicly accessible websites maintained by the Playwright team:

1. **https://playwright.dev** — the Playwright documentation site
   - Tests live in `tests/example.spec.ts`
   - Simple 2-test starter suite (page title, navigation link)

2. **https://demo.playwright.dev/todomvc** — Playwright's live Todo MVC demo app
   - Tests live in `tests-examples/demo-todo-app.spec.ts`
   - Comprehensive suite (~30 tests) covering full CRUD functionality, filtering, persistence, and routing

No local server is required — all tests run against live public URLs.

## Tech Stack

- **Language:** TypeScript
- **Test framework:** Playwright (`@playwright/test` v1.57+)
- **Node.js:** v18 or higher
- **Browsers tested:** Chromium, Firefox, WebKit (Safari)

## Project Structure

```
demo-test/
├── .claude/                          # Claude Code settings
│   └── settings.local.json           # Allowed CLI permissions
├── tests/                            # Primary test folder (Playwright default)
│   └── example.spec.ts               # Simple starter tests against playwright.dev
├── tests-examples/                   # Additional example tests
│   └── demo-todo-app.spec.ts         # Full TodoMVC test suite
├── playwright.config.ts              # Playwright configuration
├── package.json                      # Dependencies
├── package-lock.json                 # Lockfile
├── CLAUDE.md                         # This file
├── README.md                         # Team onboarding guide
└── .gitignore                        # Excludes node_modules, reports, test-results
```

## Running Tests

```bash
# Install dependencies (first time only)
npm install
npx playwright install

# Run all tests (headless, all browsers)
npx playwright test

# Run tests with browser visible
npx playwright test --headed

# Run a specific file
npx playwright test tests/example.spec.ts

# Run in Playwright UI mode (interactive)
npx playwright test --ui

# View the HTML report after a test run
npx playwright show-report
```

## Playwright Configuration

Key settings in `playwright.config.ts`:
- `testDir` points to `./tests` — only files in that folder run by default
- Tests run **fully in parallel**
- **HTML reporter** is used — generates a report in `/playwright-report/`
- On CI: retries twice on failure, runs single-threaded
- Browsers: Chromium, Firefox, WebKit

> Note: `tests-examples/` is outside the default `testDir`. To run the TodoMVC suite, reference it explicitly: `npx playwright test tests-examples/`

## Branch Strategy

| Branch    | Purpose                                  |
|-----------|------------------------------------------|
| `main`    | Stable, reviewed code                    |
| `develop` | Active development — all work goes here  |

Always work on `develop` and open a Pull Request to merge into `main`.

## How Claude Code Can Help

When working in this project, Claude Code can:
- Explain what existing tests do and how they work
- Write new Playwright tests based on a description
- Debug failing tests and suggest fixes
- Help with Git operations (status, commits, branches, PRs)
- Explain Playwright concepts (locators, assertions, fixtures, etc.)
- Generate test data or helper functions

## Common Playwright Patterns Used in This Project

- `page.getByRole()` — locate elements by ARIA role
- `page.getByPlaceholder()` — locate inputs by placeholder text
- `page.getByTestId()` — locate elements by `data-testid` attribute
- `expect(locator).toHaveText()` — assert text content
- `expect(locator).toBeVisible()` — assert visibility
- `test.describe()` — group related tests
- `test.beforeEach()` — setup that runs before each test
- `page.waitForFunction()` — wait for a browser-side condition (e.g. localStorage)
