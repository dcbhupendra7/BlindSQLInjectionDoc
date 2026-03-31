# Chart Generation

`benchmarks/generate_charts.py` creates visual summaries from benchmark JSON output.

## Generate all charts

```bash
cd benchmarks
python generate_charts.py --input benchmark_results.json
```

## Generated files

- `benchmark_comparison.png` (tool-wise time comparison)
- `benchmark_speedup.png` (speedup factors vs baselines)
- `benchmark_iterations.png` (per-iteration trend lines)
- `algorithm_complexity.png` (query complexity and speedup curves)

## Notes on algorithm complexity chart

The chart logic can use measured query-count data when available and combine it with theoretical complexity trends for a practical visualization.

## Reproducibility checklist

- Use the same benchmark input file for all plots.
- Keep chart generation script versioned with benchmark scripts.
- Include metadata (date, machine, target setup) in your experiment logs.
