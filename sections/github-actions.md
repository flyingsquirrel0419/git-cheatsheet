# GitHub Actions

## Workflow Files

Workflows live in `.github/workflows/*.yml`.

```yaml
on: [push]
```

```yaml
on: [pull_request]
```

```yaml
on: workflow_dispatch
```

## Common Steps

```yaml
- uses: actions/checkout@v4
- uses: actions/setup-node@v4
```

Use encrypted repository secrets for credentials:

```yaml
env:
  TOKEN: ${{ secrets.NAME }}
```
