# Undoing Changes

## Working Tree and Index

```bash
git restore <file>
git restore --staged <file>
```

`restore --staged` unstages without discarding your edits.

## Commits

```bash
git reset HEAD~1
git reset --hard HEAD~1
git revert <commit>
```

Use `revert` for shared history. It creates a new commit that undoes an older commit.

## Untracked Files

```bash
git clean -fd
```

Preview destructive cleanups with `git clean -fdn` before running them.
