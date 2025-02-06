# workflows

collection of Shared workflows for Pragma Repositories

## Usage

### Rust Repositories

```yaml
name: Pragma

on: [pull_request]

jobs:
  workflow:
    permissions:
      # required for all workflows
      security-events: write
      checks: write
      pull-requests: write
      # only required for workflows in private repositories
      actions: read
      contents: read
    uses: astraly-labs/workflows/.github/workflows/rust.yaml@main
    secrets: inherit
```
