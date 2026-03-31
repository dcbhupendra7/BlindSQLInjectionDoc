# Running Benchmarks

Benchmark scripts compare multiple extraction approaches and summarize time/query efficiency.

## Run benchmark script

```bash
cd benchmarks
python compare_tools.py "http://127.0.0.1:5000/vulnerable?id=1" \
  --payload "' OR ({condition}) AND SLEEP(2) -- -" \
  --iterations 5 \
  --user-id 1 \
  --output benchmark_results.json
```

## What gets measured

- extraction time per iteration,
- summary statistics (mean, median, std, min, max),
- success rates,
- query counts for StatSQLi and traditional baseline.

## Output artifact

- JSON file (default: `benchmark_results.json`) containing raw runs and summary metrics.

## Good benchmarking practices

- Keep target environment stable (same host, same load profile).
- Use identical target and payload settings across methods.
- Run enough iterations to estimate variance.
- Report both time and query counts for balanced interpretation.
