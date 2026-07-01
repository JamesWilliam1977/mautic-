```markdown
# mautic- Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches the core development patterns, coding conventions, and repeatable workflows observed in the `mautic-` repository, a TypeScript codebase (with significant PHP components) focused on modular, maintainable, and type-safe code. You'll learn how to structure files, write and refactor tests, enforce coding standards, and manage mass updates using standardized commands and processes.

---

## Coding Conventions

### File Naming

- **PascalCase** is used for file names.
  - Example: `UserProfile.ts`, `EmailSender.ts`

### Import Style

- **Relative imports** are preferred.
  - Example:
    ```typescript
    import { EmailSender } from './EmailSender';
    ```

### Export Style

- **Named exports** are used.
  - Example:
    ```typescript
    export function sendEmail() { ... }
    export const EMAIL_REGEX = /.../;
    ```

### Commit Message Patterns

- No strict type; freeform messages.
- Common prefixes: `[tests]`, `[rector]`, `[types]`
- Example: `[tests] inline stub-only properties`

---

## Workflows

### Mass Test Refactor or Type Improvement

**Trigger:** When you want to improve test code quality, type coverage, or refactor tests for consistency across the codebase.  
**Command:** `/refactor-tests`

1. Identify a cross-cutting test code issue (e.g., stub-only properties, missing type coverage, test inheritance problems).
2. Apply automated or manual refactoring to dozens of test files across bundles/plugins.
3. Update related configuration or static analysis files (e.g., `phpstan.neon`).
4. Commit all changes in a single, large commit or PR.

**Files Involved:**
- `app/bundles/*/Tests/**/*.php`
- `plugins/*/Tests/**/*.php`
- `phpstan.neon`

**Example:**
```php
// Before: Missing type hints or stub-only properties
public function testSomething() {
    $stub = $this->createMock(SomeClass::class);
    // ...
}

// After: Improved type coverage and explicit stubs
public function testSomething(): void {
    $stub = $this->createMock(SomeClass::class);
    // ...
}
```

---

### Add or Improve Return Type Declarations

**Trigger:** When you want to increase type safety and static analysis coverage by adding return type declarations.  
**Command:** `/add-return-types`

1. Identify PHP files (entities, helpers, models, forms, integrations) missing return type declarations.
2. Add or update return type declarations in these files.
3. Optionally update related test files if type changes require test adjustments.
4. Update static analysis config (e.g., `rector.php`, `phpstan.neon`) if coverage metrics change.
5. Commit all changes together.

**Files Involved:**
- `app/bundles/*/Entity/*.php`
- `app/bundles/*/Helper/*.php`
- `app/bundles/*/Model/*.php`
- `app/bundles/*/Form/**/*.php`
- `plugins/*/Helper/*.php`
- `plugins/*/Integration/*.php`
- `rector.php`
- `phpstan.neon`

**Example:**
```php
// Before
public function getName() {
    return $this->name;
}

// After
public function getName(): string {
    return $this->name;
}
```

---

### Rector or Coding Standard Mass Update

**Trigger:** When you want to enforce a new coding standard or Rector rule across the codebase.  
**Command:** `/rector-run`

1. Configure Rector or coding standard tool with new rule(s).
2. Run tool across all PHP source files (controllers, entities, helpers, integrations, etc).
3. Review and commit all automated changes in a single commit/PR.

**Files Involved:**
- `app/bundles/*/Controller/*.php`
- `app/bundles/*/Entity/*.php`
- `app/bundles/*/Helper/*.php`
- `app/bundles/*/Model/*.php`
- `app/bundles/*/EventListener/*.php`
- `plugins/*/Integration/*.php`
- `rector.php`

**Example:**
```php
// Before: Loose comparison
if ($a == $b) { ... }

// After: Strict comparison enforced by Rector
if ($a === $b) { ... }
```

---

### Merge PR with Mass Test or Type Changes

**Trigger:** When a PR with mass test refactoring or type declaration improvements is ready to merge.  
**Command:** `/merge-mass-change-pr`

1. Review PR containing many test or type changes across bundles/plugins.
2. Merge PR (often with a descriptive message referencing the workflow, e.g., `[tests] inline stub-only properties`).
3. Resulting merge commit touches dozens of test or source files.

**Files Involved:**
- `app/bundles/*/Tests/**/*.php`
- `plugins/*/Tests/**/*.php`
- `app/bundles/*/Entity/*.php`
- `app/bundles/*/Helper/*.php`
- `rector.php`
- `phpstan.neon`

---

## Testing Patterns

- **Test files:** Use the `*.test.ts` pattern for TypeScript tests.
- **Framework:** Not explicitly detected; follow standard TypeScript test conventions.
- **Test code:** Focuses on type coverage, explicit stubs, and SOLID principles.

**Example:**
```typescript
// UserService.test.ts
import { UserService } from './UserService';

describe('UserService', () => {
  it('should return user by ID', () => {
    // Arrange
    const service = new UserService();
    // Act
    const user = service.getUserById(1);
    // Assert
    expect(user.id).toBe(1);
  });
});
```

---

## Commands

| Command                | Purpose                                                      |
|------------------------|--------------------------------------------------------------|
| /refactor-tests        | Refactor or improve types/structure across many test files   |
| /add-return-types      | Add or improve PHP return type declarations in source files  |
| /rector-run            | Apply Rector or coding standard changes across the codebase  |
| /merge-mass-change-pr  | Merge PRs with mass test or type declaration changes         |
```
