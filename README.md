# greet-ci

A greeting program with GitHub Actions CI.

## Setup and run

Install uv, then run these commands from the repository root:

```sh
uv sync --locked
uv run --locked python greet.py Hee
uv run --locked python greet.py
```

Expected output: `Hello, Hee!` and `Hello, world!`, respectively.

## Validate and build

```sh
uv run --locked pytest -q greet.py
uv run --locked black --check greet.py
uv run --locked flake8 greet.py
uv run --locked mypy greet.py
uv build
```

CI runs on pushes and pull requests targeting main. Tests cover Ubuntu and
Windows with Python 3.11 and 3.12. Formatting, lint, and type checks must pass
before the package is built and saved as the `greet-dist` artifact.
