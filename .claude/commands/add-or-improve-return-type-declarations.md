---
name: add-or-improve-return-type-declarations
description: Workflow command scaffold for add-or-improve-return-type-declarations in mautic-.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-or-improve-return-type-declarations

Use this workflow when working on **add-or-improve-return-type-declarations** in `mautic-`.

## Goal

Add or improve PHP return type declarations across entities, helpers, models, forms, integrations, excluding controllers.

## Common Files

- `app/bundles/*/Entity/*.php`
- `app/bundles/*/Helper/*.php`
- `app/bundles/*/Model/*.php`
- `app/bundles/*/Form/**/*.php`
- `plugins/*/Helper/*.php`
- `plugins/*/Integration/*.php`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Identify PHP files (entities, helpers, models, forms, integrations) missing return type declarations.
- Add or update return type declarations in these files.
- Optionally update related test files if type changes require test adjustments.
- Update static analysis config (e.g., rector.php, phpstan.neon) if coverage metrics change.
- Commit all changes together.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.