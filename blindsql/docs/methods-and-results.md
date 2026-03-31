# Methods and Results

## Methodology overview

StatSQLi models time-based inference as a statistical decision process:

1. Collect baseline timing samples.
2. Choose delay candidates adaptively.
3. Compare delayed vs baseline distributions with Welch's t-test.
4. Use binary search to infer character values efficiently.

## Statistical model used

- Null hypothesis: delayed samples are not meaningfully greater than baseline.
- Alternative hypothesis: delayed samples are greater than baseline.
- Test: one-tailed Welch t-test (`equal_var=False`, `alternative='greater'`).
- Confidence target in code defaults to 99% (`confidence_level=0.99`), implying alpha near 0.01.

## Algorithmic shift

- Traditional approach: linear search over printable ASCII (`O(n)` per character).
- StatSQLi approach: binary search over ASCII range (`O(log n)` per character).

In practice, this reduces condition checks significantly for each character position.

## Adaptive delay strategy

The current implementation uses a baseline-driven heuristic:

- compute baseline mean and standard deviation,
- estimate detectable delay level,
- pick smallest candidate delay that is reliably distinguishable.

This reduces manual tuning effort while keeping delays practical.

## Benchmark pipeline

The benchmark runner:

- executes repeated runs per method,
- records extraction duration and query counts,
- computes summary statistics (mean, median, std, min, max, success rate),
- saves JSON output for later charting.

## Report-aligned figures

The figure set you added is included in the docs and can be viewed on the [Figures](figures.md) page.

Key visuals include:

- architecture overview (Fig. 1),
- query efficiency and speedup plots (Fig. 2 and Fig. 3),
- complexity and speedup trend comparison (Fig. 4).

## Result interpretation guidance

When evaluating your own benchmark runs:

- compare **query counts** first (algorithmic efficiency),
- compare **time** second (environment-sensitive),
- inspect run-to-run variation to assess jitter sensitivity.

Use the generated charts to communicate both raw performance and complexity trends.
