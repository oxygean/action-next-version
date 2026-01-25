# action-next-version

Automatically bump version in `package.json` after successful deployment.

## Usage

```yaml
- name: Version Bump
  uses: oxygean-hub/action-next-version@v0.0.4
  with:
    environment: staging  # or release
    version_type: patch   # or major, minor
    github_pat: ${{ secrets.BOT_PAT }}
```

## Inputs

- `environment` (required): Environment being deployed (`staging` or `release`)
  - `staging`: Adds `-b.X` suffix (e.g., `1.2.3-b.1`)
  - `release`: No suffix (e.g., `1.2.3`)
- `version_type` (required): Version bump type (`major`, `minor`, or `patch`)
- `github_pat` (required): GitHub Personal Access Token with `repo` scope for committing

## Features

- Bumps version in `package.json` using semantic versioning
- Adds beta suffix for staging deployments
- Auto-increments beta number for consecutive staging releases
- Commits with `[BOT] Version bump to vX.X.X` message
- Pushes changes back to repository
