# Check Dirty Git

A simple GitHub Action that fails if there are uncommitted changes in the git working directory.

This is useful for CI workflows that generate code (e.g., `cargo fmt`, code generators) to ensure all generated files are committed.

## Usage

```yaml
- uses: cbeck88/check-dirty-git@v1
```

That's it! The action will fail if `git status --porcelain` returns any output.

## Example Workflow

```yaml
name: CI

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Build
        run: cargo build

      - name: Format
        run: cargo fmt

      - name: Check for uncommitted changes
        uses: cbeck88/check-dirty-git@v1
```

## License

MIT or Apache 2.0 at your option.
