# AGENTS.md

## Overview

Wayback Gap Detector is a CLI tool that finds URLs in a local list that are
not archived in the Wayback Machine. The code lives in `waygap.py` and the
tests in `test_waygap.py`. See [ARCHITECTURE.md](ARCHITECTURE.md) for the
internal design and [README.md](README.md) for usage.

## Commands

```bash
uv sync                                   # install dependencies
uv run pytest                             # tests
uv run ruff check .                       # lint
uv run ruff format --check .              # format check
uv run basedpyright                       # type check
```

All of these must pass before a change is complete (CI runs the same commands).

## Rules

- Tests must not make external network calls; mock all API requests.
- When changing dependencies, update `pyproject.toml`, `uv.lock` and
  `requirements.txt` together. Regenerate `requirements.txt` with
  `uv export --no-dev --no-hashes --no-emit-project -o requirements.txt`.
- Keep `README.md` and `README_ja.md` in sync; update both together.
- `ARCHITECTURE.md` covers the data flow, the cache schema, rules that span
  functions, and one-line roles of the key functions; update it when those
  change. Leave function-level details (signatures, edge cases, log wording,
  retry counts) to the code, adding docstrings or comments only where the
  code alone is unclear.

## Commits

Conventional Commits `type: subject`. Subject in English.
