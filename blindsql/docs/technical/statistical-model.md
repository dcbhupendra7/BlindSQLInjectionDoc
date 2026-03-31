# Statistical Model

## Why statistics matter here

Time-based inference depends on response latency differences, but network jitter and server variance introduce noise. A fixed timing threshold can misclassify conditions under unstable latency.

## Decision strategy in StatSQLi

`TimingAnalyzer` applies a one-tailed Welch t-test:

- compare baseline sample set vs delayed-condition sample set,
- use unequal-variance assumptions (`equal_var=False`),
- infer delayed condition as true when `p_value < alpha`.

With default confidence `0.99`, alpha is approximately `0.01`.

## Baseline estimation

Before condition tests, the extractor collects baseline timings with a false condition (`1=0`) to model normal latency.

The analyzer computes:

- mean baseline latency,
- sample standard deviation,
- optional adaptive threshold estimate (`mean + 3 * std` style heuristic).

## Sample-size behavior

The implementation enforces minimum sample counts (`min_samples`) to avoid overconfident decisions from tiny datasets. It also includes a helper for rough sample-size estimation based on expected effect size and variance.

## Practical interpretation

- Lower p-values increase confidence in true delay effects.
- High variance demands larger sample sets or stronger delays.
- Statistical detection improves reliability but still depends on transport stability and endpoint behavior.
