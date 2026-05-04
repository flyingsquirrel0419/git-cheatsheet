# Branching & Merging

## Create and Move

```bash
git branch
git branch <name>
git switch <name>
git switch -c <name>
git checkout -b <name>
```

Use `git switch` for modern branch movement. `checkout` still appears in older projects and documentation.

## Combine Work

```bash
git merge <branch>
git merge --no-ff <branch>
git rebase <branch>
git rebase -i HEAD~3
```

Merge preserves branch structure. Rebase rewrites local commits into a linear sequence.

## Clean Branches

```bash
git branch -d <name>
git branch -D <name>
```

Prefer `-d`. Use `-D` only when you intentionally want to delete an unmerged branch.
