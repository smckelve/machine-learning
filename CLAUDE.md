# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

A personal machine learning learning/experimentation repo (ML Zoomcamp-style exercises). It is a `uv`-managed Python project, not a packaged application — expect small scripts and Jupyter notebooks rather than a service with tests/CI.

## Environment & commands

- Python version is pinned via `.python-version` (3.14); dependencies and lockfile are managed with `uv` (`pyproject.toml` / `uv.lock`).
- Install/sync dependencies: `uv sync`
- Run the entrypoint script: `uv run main.py`
- Run a notebook cell-by-cell via Jupyter (kernel name `machine-learning`), or non-interactively: `uv run jupyter nbconvert --to notebook --execute ml.ipynb`
- Add a new dependency: `uv add <package>` (updates `pyproject.toml` and `uv.lock`)

There is no lint/test tooling configured yet — don't assume `pytest`, `ruff`, etc. exist unless you see them added to `pyproject.toml`.

## Structure

- `main.py` — placeholder entrypoint, not tied to the ML work.
- `ml.ipynb` — main scratch notebook; currently a scikit-learn `DecisionTreeClassifier` exercise trained on `music.csv`.
- `music.csv`, `vgsales.csv`, `woodbine_horses.csv`, `transactions.xlsx` — datasets used as notebook inputs. Treat these as read-only sample data; large CSVs (`vgsales.csv`, `woodbine_horses.csv`) are checked into the repo, so avoid loading them wholesale into context — read a small sample when inspecting schema/contents.
- `ML Zoomcamp/` — currently empty; likely destination for future zoomcamp exercises.
- `Machine Learning.code-workspace` — VS Code workspace that also references a Colab CPU remote folder (`colab://...`); irrelevant to local shell work.

## Working conventions

- New exploratory work generally belongs in a notebook (`.ipynb`) rather than a standalone script, matching the existing pattern.
- `.venv` and Python build artifacts are gitignored — never commit them.
