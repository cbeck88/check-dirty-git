# Check Dirty Git

A simple GitHub Action that fails if there are uncommitted changes in the git working directory.

## Usage

```yaml
- uses: cbeck88/check-dirty-git@v1
```

The action will fail if `git status --porcelain` returns any output.

## Example Workflow

```yaml
name: CI

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Test
        run: cargo test

      - name: Check for uncommitted changes
        uses: cbeck88/check-dirty-git@v1
```

## License

MIT or Apache 2.0 at your option.
