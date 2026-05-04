# Git & GitHub Cheat Sheet

> The most complete Git & GitHub cheat sheet: commands, workflows, GitHub CLI, and Actions in one place.

[![PRs welcome](https://img.shields.io/badge/PRs-welcome-238636.svg)](CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Website](https://img.shields.io/badge/Website-GitHub%20Pages-0969da.svg)](https://flyingsquirrel0419.github.io/git-cheatsheet/)

This repository includes a searchable website and a Markdown reference for daily Git and GitHub work. The commands are organized by scenario so you can find the right command without remembering the exact name first.

## Table of Contents

- [Setup & Config](#setup--config)
- [Basic Commands](#basic-commands)
- [Branching & Merging](#branching--merging)
- [Remote & Sync](#remote--sync)
- [Undoing Changes](#undoing-changes)
- [Stash](#stash)
- [Log & Diff](#log--diff)
- [GitHub CLI](#github-cli)
- [GitHub Actions](#github-actions)
- [Tips & Tricks](#tips--tricks)

## Setup & Config

| Scenario | Command | Notes |
|---|---|---|
| Set your name | `git config --global user.name "Name"` | Stored in new commits. |
| Set your email | `git config --global user.email "email@example.com"` | Match your GitHub email for attribution. |
| Use VS Code as editor | `git config --global core.editor "code --wait"` | Opens commit messages in VS Code. |
| List settings | `git config --list` | Add `--show-origin` to see source files. |
| Add alias | `git config --global alias.st status` | Then run `git st`. |

## Basic Commands

| Scenario | Command | Notes |
|---|---|---|
| Start a repository | `git init` | Creates a new local repo. |
| Clone a repository | `git clone <url>` | Copies history and files. |
| Shallow clone | `git clone <url> --depth 1` | Faster for large repos. |
| Stage everything | `git add .` | Includes new, modified, and deleted files. |
| Stage selected hunks | `git add -p` | Review changes before staging. |
| Commit staged changes | `git commit -m "message"` | Use clear, imperative messages. |
| Edit last commit | `git commit --amend` | Avoid after pushing shared history. |
| Check state | `git status` | Shows staged, unstaged, and untracked files. |
| View unstaged diff | `git diff` | Working tree vs index. |
| View staged diff | `git diff --staged` | Index vs HEAD. |

## Branching & Merging

| Scenario | Command | Notes |
|---|---|---|
| List branches | `git branch` | Current branch is marked with `*`. |
| Create branch | `git branch <name>` | Does not switch to it. |
| Switch branch | `git switch <name>` | Modern branch checkout. |
| Create and switch | `git switch -c <name>` | Preferred modern command. |
| Legacy create and switch | `git checkout -b <name>` | Common in older docs. |
| Merge a branch | `git merge <branch>` | Merges into current branch. |
| Force merge commit | `git merge --no-ff <branch>` | Keeps branch history visible. |
| Rebase onto branch | `git rebase <branch>` | Replays current commits. |
| Interactive rebase | `git rebase -i HEAD~3` | Edit, squash, reorder commits. |
| Delete merged branch | `git branch -d <name>` | Refuses unsafe deletion. |
| Force delete branch | `git branch -D <name>` | Deletes even if unmerged. |

## Remote & Sync

| Scenario | Command | Notes |
|---|---|---|
| List remotes | `git remote -v` | Shows fetch and push URLs. |
| Add origin | `git remote add origin <url>` | Connect local repo to remote. |
| Push branch | `git push origin <branch>` | Upload commits. |
| Push and set upstream | `git push -u origin <branch>` | Future `git push` can omit names. |
| Safer force push | `git push --force-with-lease` | Refuses if remote moved unexpectedly. |
| Pull changes | `git pull` | Fetch plus merge. |
| Pull with rebase | `git pull --rebase` | Keeps local history linear. |
| Fetch only | `git fetch origin` | Updates remote refs without merging. |

## Undoing Changes

| Scenario | Command | Notes |
|---|---|---|
| Discard file changes | `git restore <file>` | Restores from index. |
| Unstage a file | `git restore --staged <file>` | Keeps working tree edits. |
| Undo last commit, keep changes | `git reset HEAD~1` | Moves branch pointer back. |
| Delete last commit and changes | `git reset --hard HEAD~1` | Destructive. Use carefully. |
| Revert a commit safely | `git revert <commit>` | Adds a new inverse commit. |
| Remove untracked files | `git clean -fd` | Destructive. Preview with `-n`. |

## Stash

| Scenario | Command | Notes |
|---|---|---|
| Save changes | `git stash` | Stores tracked changes. |
| Save with message | `git stash push -m "message"` | Easier to recognize later. |
| List stashes | `git stash list` | Shows stash refs. |
| Apply and remove latest | `git stash pop` | May create conflicts. |
| Apply specific stash | `git stash apply stash@{0}` | Keeps stash in list. |
| Drop specific stash | `git stash drop stash@{0}` | Removes one stash. |
| Clear all stashes | `git stash clear` | Destructive. |

## Log & Diff

| Scenario | Command | Notes |
|---|---|---|
| Compact history | `git log --oneline` | One commit per line. |
| Graph history | `git log --oneline --graph` | Useful for branches. |
| Show patch history | `git log -p` | Includes diffs. |
| Filter by author | `git log --author="Name"` | Matches author string. |
| Filter by time | `git log --since="2 weeks ago"` | Accepts natural dates. |
| Inspect commit | `git show <commit>` | Metadata plus diff. |
| Trace line ownership | `git blame <file>` | Use for context, not blame. |
| Contributor summary | `git shortlog -sn` | Count commits by author. |

## GitHub CLI

| Scenario | Command | Notes |
|---|---|---|
| Create repository | `gh repo create` | Interactive by default. |
| Clone repository | `gh repo clone <owner>/<repo>` | Uses GitHub auth. |
| Create pull request | `gh pr create` | Opens PR from current branch. |
| List pull requests | `gh pr list` | Add filters for state/label. |
| Check out PR | `gh pr checkout <number>` | Creates local branch. |
| Merge PR | `gh pr merge <number>` | Supports squash/rebase/merge. |
| Create issue | `gh issue create` | Interactive by default. |
| List issues | `gh issue list` | Filter with labels or assignees. |
| Create release | `gh release create` | Attach files as assets. |
| Run workflow | `gh workflow run <name>` | Triggers GitHub Actions. |
| Create gist | `gh gist create <file>` | Private by default with `--private`. |

## GitHub Actions

| Scenario | Snippet | Notes |
|---|---|---|
| Workflow location | `.github/workflows/<name>.yml` | YAML files define workflows. |
| Run on push | `on: [push]` | Triggers for every push. |
| Run on PR | `on: [pull_request]` | Checks incoming changes. |
| Manual run | `on: workflow_dispatch` | Enables the Run workflow button. |
| Checkout code | `uses: actions/checkout@v4` | Common first step. |
| Set up Node | `uses: actions/setup-node@v4` | Configure runtime and cache. |
| Use secrets | `${{ secrets.NAME }}` | Never commit secrets. |

## Tips & Tricks

| Scenario | Command | Notes |
|---|---|---|
| Empty commit | `git commit --allow-empty -m "trigger CI"` | Useful for CI reruns. |
| Cherry-pick commit | `git cherry-pick <commit>` | Bring one commit over. |
| Create tag | `git tag v1.0.0` | Lightweight tag. |
| Push tag | `git push origin v1.0.0` | Uploads a single tag. |
| Global ignore file | `git config --global core.excludesfile ~/.gitignore_global` | For OS/editor files. |
| Previous branch | `git switch -` | Jump back quickly. |
| Restore file from branch | `git checkout <branch> -- <file>` | Copies one file into current branch. |
| Compare with HEAD | `git diff HEAD` | Shows staged and unstaged changes. |

## More Detail

Section-specific notes live in [`sections/`](sections/):

- [`basics.md`](sections/basics.md)
- [`branching.md`](sections/branching.md)
- [`remote.md`](sections/remote.md)
- [`undoing.md`](sections/undoing.md)
- [`github-cli.md`](sections/github-cli.md)
- [`github-actions.md`](sections/github-actions.md)

## Contributing

Corrections, examples, and workflow additions are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT
