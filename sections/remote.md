# Remote & Sync

## Connect a Remote

```bash
git remote -v
git remote add origin <url>
```

`origin` is the conventional name for the main remote repository.

## Push Work

```bash
git push origin <branch>
git push -u origin <branch>
git push --force-with-lease
```

Use `--force-with-lease` instead of `--force` after rewriting history. It checks whether the remote changed first.

## Receive Work

```bash
git pull
git pull --rebase
git fetch origin
```

Fetch is safe for inspection because it does not merge into your current branch.
