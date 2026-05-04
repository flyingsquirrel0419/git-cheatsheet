# GitHub CLI

## Repository Work

```bash
gh repo create
gh repo clone <owner>/<repo>
```

The GitHub CLI uses your authenticated GitHub account and can create repositories without opening the browser.

## Pull Requests

```bash
gh pr create
gh pr list
gh pr checkout <number>
gh pr merge <number>
```

These commands cover the common PR loop from creation to local review to merge.

## Issues, Releases, and Automation

```bash
gh issue create
gh issue list
gh release create
gh workflow run <name>
gh gist create <file>
```

Use `gh workflow run` for manual GitHub Actions workflows.
