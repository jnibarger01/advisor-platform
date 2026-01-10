# Development Setup Guide

This document explains how the automated testing and linting system works.

## Pre-commit Hooks

This project uses **husky** and **lint-staged** to automatically run tests and linters before each commit.

### What Gets Checked

When you commit changes, the following happens automatically:

#### For Code Files (_.js, _.jsx)

1. **ESLint** - Checks for code quality issues and auto-fixes them
2. **Prettier** - Formats code consistently
3. **Vitest** - Runs tests related to the changed files

#### For Documentation Files (_.md, _.json, \*.css)

1. **Prettier** - Only formats the files
2. **No tests are run** - Documentation changes skip testing

### How It Works

The `lint-staged` configuration in `package.json` defines different rules for different file types:

```json
"lint-staged": {
  "*.{js,jsx}": [
    "eslint --fix",
    "prettier --write",
    "vitest related --run"
  ],
  "*.{json,md,css}": [
    "prettier --write"
  ]
}
```

This ensures that:

- Code changes are thoroughly checked
- Documentation changes are fast (no unnecessary test runs)
- Comments and markdown files only get formatted
