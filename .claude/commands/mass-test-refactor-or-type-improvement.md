---
name: mass-test-refactor-or-type-improvement
description: Workflow command scaffold for mass-test-refactor-or-type-improvement in mautic-.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /mass-test-refactor-or-type-improvement

Use this workflow when working on **mass-test-refactor-or-type-improvement** in `mautic-`.

## Goal

Refactor or improve types/structure of many test files across multiple bundles/plugins, often to improve type coverage, SOLID principles, or inline stub-only properties.

## Common Files

- `app/bundles/*/Tests/**/*.php`
- `plugins/*/Tests/**/*.php`
- `phpstan.neon`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Identify a cross-cutting test code issue (e.g., stub-only properties, missing type coverage, test inheritance problems).
- Apply automated or manual refactoring to dozens of test files across bundles/plugins.
- Update related configuration or static analysis files (e.g., phpstan.neon).
- Commit all changes in a single, large commit or PR.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.