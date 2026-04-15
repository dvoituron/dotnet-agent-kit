---
title: Git Naming Conventions
impact: MEDIUM
impactDescription: Poor commit messages make debugging and release notes difficult
tags: git, commit, branch, naming
---

## Git Naming Conventions

### 1. Commit as Soon as Possible
- Your solution must compile correctly.
- At least every evening.

### 2. Commit Only Source Code
- `.cs`, `.ts`, `.xaml`, `.html`, resources, etc.
- Use `.gitignore` file. See [github/gitignore](https://github.com/github/gitignore).
- Not NuGet / NPM packages.

### 3. Commit Comment Convention

To speed up the reviewing process and help write release notes:
- Start with `Fix`, `Add`, `Change`
- Maximum **80 characters**
- (Optional) Reference to the work item (`#`)

**Examples:**
- `"Add a new login component with help button"`
- `"#2145125 - Change the login component to add a password remember link"`
- `"Fix the missing password remember link"`

### 4. Branch Naming

- All in **lower case** and **singular**.
- Use **dash** to separate words.
- Prefix by `users/username` or `hotfix`.

**Examples:**
- `users/jamal/add-login-page`
- `users/jamal/2145126-add-password-remember-link`
- `hotfix/fix-missing-password`
