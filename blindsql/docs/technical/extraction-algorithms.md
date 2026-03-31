# Extraction Algorithms

## Binary search extractor (primary)

The main extractor infers one character at a time using binary search over printable ASCII bounds.

### Core steps

1. Build a per-position SQL expression for character code.
2. Test midpoint predicates (`char_code >= mid`).
3. Use timing significance result to choose upper/lower half.
4. Iterate until bounds converge.
5. Verify likely candidates and return final character.

### Complexity

- Character search complexity: `O(log n)` for range size `n`.
- For printable ASCII, this is typically a small bounded number of checks.

## Traditional linear extractor (baseline)

The baseline implementation checks values sequentially:

- test `char_code == 32`, then `33`, and so on,
- stop when a match appears true by threshold rule.

Complexity is `O(n)` and acts as a comparison baseline in benchmarks.

## Parallel extraction strategy

`ParallelExtractor` splits positions into chunks and extracts each chunk concurrently using a `ThreadPoolExecutor`.

Tradeoff:

- lower wall-clock time potential,
- higher instantaneous load and possible timing instability.

Use moderate worker counts and confirm reliability before scaling.
