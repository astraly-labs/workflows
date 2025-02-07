# Rust Test Coverage - Github Action

This action runs Rust tests with code coverage using cargo-llvm-cov and nextest

The action runs the following:
- Sets up Rust toolchain
- Installs cargo-llvm-cov and nextest
- Runs tests with coverage collection
- Uploads coverage reports to Codecov

## Inputs

```yaml
fail_ci:
  description: 'Fail CI if coverage upload fails'
  required: false
  default: false
token:
  description: 'Codecov token'
  required: false
```

## Outputs

- LCOV coverage report
- Coverage data uploaded to Codecov

## Detailed example

```yaml
name: Rust Test Coverage

on:
  pull_request: {}
  workflow_dispatch: {}
  push:
    branches:
      - main

jobs:
  test:
    name: Rust Tests
    runs-on: ubuntu-latest

    steps:
    - name: Checkout source code
      uses: actions/checkout@v3

    - name: Run Tests
      uses: astraly-labs/workflows/rust/test@main
      with:
        token: ${{ secrets.CODECOV_TOKEN }}
        fail_ci: false
```
