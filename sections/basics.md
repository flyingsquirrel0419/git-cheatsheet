# Basics

## Start or Copy a Repository

```bash
git init
git clone <url>
git clone <url> --depth 1
```

Use a shallow clone when you only need the latest files and do not need full history.

## Stage and Commit

```bash
git add .
git add -p
git commit -m "message"
git commit --amend
```

Use `git add -p` when you want one clean commit instead of mixing unrelated edits.

## Inspect Work

```bash
git status
git diff
git diff --staged
```

Check staged changes before committing so the commit contains exactly what you intended.
