---
title: Git Workflow
impact: MEDIUM
impactDescription: Inconsistent Git workflow causes merge conflicts and lost work
tags: git, branching, pull-request, workflow
---

## Git Workflow

Use a [simple Git workflow](https://docs.microsoft.com/en-us/azure/devops/repos/git/git-branching-guidance):

1. **Create a branch** for the changes you plan to make and give it a name, such as `users/jamal/add-login-page`.
2. **Commit changes** to your branch. People often have multiple commits for a bug fix or feature.
3. **Push your branch** to the remote repository.
4. **Create a pull request** so other people can review your changes.
5. **Complete your pull request** and resolve any merge conflicts.

### Branching Guidance

- Develop features and fix bugs in **user branches** based off your main branch.
- Use a **consistent naming convention** for branches.
- Allowed prefixes:
  - `users/username/description`
  - `users/username/workitem`
  - `feature/feature-name`
  - `hotfix/description`

> If **by mistake** you push code into the main branch (main, master, develop, ...), you must **revert** the last commit to return to the initial state.

### Pull Requests

- A Pull Request must be validated by **at least 2 approvers** before merging (squash merging) to the common development branch.
- Use pull requests to **discuss**, **review**, and **improve** code.

Reference: [Git Branching Guidance](https://docs.microsoft.com/en-us/azure/devops/repos/git/git-branching-guidance)
