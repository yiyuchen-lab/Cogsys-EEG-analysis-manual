# CogSys EEG Analysis Manual

This is a MkDocs Material starter repository for EEG analysis documentation.

## Local preview

```bash
pip install -r requirements-docs.txt
mkdocs serve
```

## Build

```bash
mkdocs build --strict
```

## Deploy

The included GitHub Actions workflow deploys the site to the `gh-pages` branch when changes are pushed to `main`.

If the GitHub Pages URL shows 404, check that the deployment workflow has completed and that GitHub Pages is using the `gh-pages` branch.

## Main tutorial

Start from:

- `docs/eeg/getting-started.md`
