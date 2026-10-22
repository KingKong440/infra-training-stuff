# CNC-27: Day 8 | Task 2 | Configure GitHub Actions Workflow

- **Jira:** https://mail4mithunu.atlassian.net/browse/CNC-27
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-22T09:01:08.499Z
- **Updated:** 2026-10-22T16:14:50.076Z
- **Due date:** —
- **Labels:** github-actions
- **Components:** —

## Description

Create a GitHub Actions workflow that automatically installs Node.js dependencies and runs ESLint whenever code is pushed to the repository.

Step 1: Configure package.json

Create a package.json with a lint script and ESLint dependencies.


```
{
  "name": "lint-practice",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "lint": "eslint ."
  },
  "devDependencies": {
    "eslint": "^9.0.0",
    "@eslint/js": "^9.0.0",
    "globals": "^15.0.0"
  }
}
```

Step 2: Configure ESLint

Create eslint.config.js.


```
import js from "@eslint/js";
import globals from "globals";

export default [
  {
    ignores: ["node_modules/**"]
  },
  js.configs.recommended,
  {
    files: ["**/*.js"],
    languageOptions: {
      globals: globals.node
    },
    rules: {
      "no-unused-vars": "warn",
      "no-console": "off"
    }
  }
];
```

Step 3: Create the GitHub Actions workflow

Create .github/workflows/lint.yml.


```
name: Lint

on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Get Code
        uses: actions/checkout@v4

      - name: Install NodeJS
        uses: actions/setup-node@v4
        with:
          node-version: 22

      - name: Install Dependencies
        run: npm i

      - name: Run Lint
        run: npm run lint
```

npm i is used here because the repository does not contain a package-lock.json. If a lockfile is committed later, npm ci can be used instead.

## Attachments

- [screenshot-2026-10-22_14-58-11.png](attachments/screenshot-2026-10-22_14-58-11.png)
- [screenshot-2026-10-22_14-58-39.png](attachments/screenshot-2026-10-22_14-58-39.png)
