# CI/CD Demo Repo

A minimal Python project used as a controllable target for the
[CI/CD Failure Diagnosis AI](https://github.com/) project.

This repo intentionally exists to be broken. Its CI workflow
(`.github/workflows/ci.yml`) runs `pytest` on every push to `main`.
The diagnosis system watches this repo's GitHub Actions runs, and
`seed_demo_repo.py` (from the diagnosis tool) pushes deliberately
broken commits here to generate real, reproducible failures.

## Structure

- `src/calculator.py` — a trivial module to test against
- `tests/test_calculator.py` — the test suite CI runs
- `.github/workflows/ci.yml` — the CI pipeline itself
- `requirements.txt` — just `pytest`

## Running tests locally

```bash
pip install -r requirements.txt
pytest
```

## Breaking it on purpose

Edit `tests/test_calculator.py` (e.g. change an assertion to something
false) or `src/calculator.py`, commit, and push to `main` — the Actions
tab will show a failing run within a minute.
