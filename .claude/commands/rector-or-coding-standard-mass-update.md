---
name: rector-or-coding-standard-mass-update
description: Workflow command scaffold for rector-or-coding-standard-mass-update in mautic-.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /rector-or-coding-standard-mass-update

Use this workflow when working on **rector-or-coding-standard-mass-update** in `mautic-`.

## Goal

Apply Rector or coding standard changes (e.g., use identical on same-typed compares) to many PHP source files across bundles and plugins.

## Common Files

- `app/bundles/*/Controller/*.php`
- `app/bundles/*/Entity/*.php`
- `app/bundles/*/Helper/*.php`
- `app/bundles/*/Model/*.php`
- `app/bundles/*/EventListener/*.php`
- `plugins/*/Integration/*.php`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Configure Rector or coding standard tool with new rule(s).
- Run tool across all PHP source files (controllers, entities, helpers, integrations, etc).
- Review and commit all automated changes in a single commit/PR.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.