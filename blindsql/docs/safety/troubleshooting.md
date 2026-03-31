# Troubleshooting

## Lab server does not start

- Confirm dependencies installed: `pip install -r requirements.txt`.
- Check if port `5000` is in use.
- Run from repository root or `lab/` as expected.

## Unexpected empty extraction results

- Verify target URL is reachable.
- Confirm payload template contains `{condition}`.
- Increase delay manually (`--delay`) if auto-detection is too aggressive for your environment.
- Reduce parallel workers and test sequential extraction first.

## Timing signal too noisy

- Increase sample counts by adjusting code parameters in extractor/analyzer.
- Use quieter network conditions (local host preferred).
- Reduce concurrent background load on test machine.

## SQLMap benchmark unavailable

`compare_tools.py` attempts to find SQLMap automatically. If missing, install it and retry:

```bash
pip install sqlmap
```

## MkDocs build issues

- Install docs dependencies: `pip install mkdocs mkdocs-material pymdown-extensions`.
- Run `mkdocs build --clean` from repository root.
- Check path and file names match entries in `mkdocs.yml`.
