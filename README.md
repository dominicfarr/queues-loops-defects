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

---
## The idea was after reading these two years apart.

Otter wrote this great article 
https://www.industriallogic.com/blog/faster-and-more-predictable/

It popped up years later on linkedIn post https://www.linkedin.com/feed/update/urn:li:activity:7507747922164252672/

I'm asking myself? Can this be actually modelled, calculate each ticket that goes through a pipe with the queues, loops, and defects this arcticle expresses costs in real terms? 

## Where it went

The model works, but most of its inputs are guesses, so the project is now heading for a playful game instead. The playable experiments are in [prototypes/](prototypes/), and the [project map](https://github.com/dominicfarr/queues-loops-defects/issues/1) tracks the decisions.