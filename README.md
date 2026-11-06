# queues-loops-defects

[![CI](https://github.com/dominicfarr/queues-loops-defects/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/dominicfarr/queues-loops-defects/actions/workflows/ci.yml)

## Development setup

**Once per machine.** These install for your user, so you don't need a venv:

- [uv](https://docs.astral.sh/uv/)
- pre-commit: `uv tool install pre-commit==4.7.0` (the version CI uses; bump both together)
- shellcheck: `brew install shellcheck`, or `uv tool install shellcheck-py`

**Once per clone.** Git doesn't copy hooks when you clone, so run this in each new clone:

```sh
pre-commit install --install-hooks
```

This installs the hooks for both the `pre-commit` and `commit-msg` stages.

See [CONTRIBUTING.md](CONTRIBUTING.md) for the workflow and the commit message format, and [docs/DEVELOPMENT.md](docs/DEVELOPMENT.md) for the development practices.
