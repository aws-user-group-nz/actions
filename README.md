# actions

Reusable GitHub Actions workflows for AWSUG NZ.

## Workflows

| Workflow | Use |
| --- | --- |
| `markdown-lint` | Lint Markdown on pull requests |
| `commitmsg-conform` | Enforce conventional commit messages (skips Dependabot) |
| `dependabot-auto-merge` | Enable GitHub auto-merge for Dependabot PRs |

## Usage

### Markdown Lint

```yaml
name: Markdown Lint

on:
  pull_request: {}

permissions:
  statuses: write
  checks: write
  contents: read
  pull-requests: read

jobs:
  markdown-lint:
    uses: aws-user-group-nz/actions/.github/workflows/markdown-lint.yml@main
```

### Commit Message Conformance

```yaml
name: Commit Message Conformance

on:
  pull_request: {}

permissions:
  statuses: write
  checks: write
  contents: read
  pull-requests: read

jobs:
  commitmsg-conform:
    uses: aws-user-group-nz/actions/.github/workflows/commitmsg-conform.yml@main
```

### Dependabot auto-merge

```yaml
name: Auto-merge Dependabot PRs

on:
  pull_request:
    types: [opened, synchronize, reopened, ready_for_review]
  check_suite:
    types: [completed]

permissions:
  contents: write
  pull-requests: write
  checks: read

jobs:
  auto-merge:
    uses: aws-user-group-nz/actions/.github/workflows/dependabot-auto-merge.yml@main
    secrets: inherit
```

Enable Allow auto-merge on the caller repo. Do not add workflows write to permissions.

## Pinning

```yaml
uses: aws-user-group-nz/actions/.github/workflows/markdown-lint.yml@main
```

Or pin to a commit SHA for stricter supply-chain control.

## License

MIT
