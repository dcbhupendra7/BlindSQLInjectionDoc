# Module Walkthrough

This section maps source files to implementation behavior.

## `statsqli/main.py`

- Defines `StatSQLi` as the orchestration class.
- Initializes adaptive delay detection when delay is omitted.
- Routes extraction through sequential or parallel path.
- Exposes CLI entrypoint via `main()`.

## `statsqli/stats.py`

- Implements `TimingAnalyzer`.
- Supports baseline statistics, significance decisions, and threshold helper logic.

## `statsqli/adaptive.py`

- Implements `AdaptiveDelayDetector`.
- Measures no-delay baseline and tests delay candidates.
- Picks smallest delay crossing detectability criteria.

## `statsqli/extractor.py`

- Implements `BinarySearchExtractor`.
- Handles request timing collection and payload formatting.
- Performs binary-search extraction and candidate verification.

## `statsqli/parallel.py`

- Implements `ParallelExtractor`.
- Uses thread pool futures to extract multiple character positions.
- Reassembles characters by index order.

## `statsqli/traditional_extractor.py`

- Implements `TraditionalExtractor`.
- Provides linear probing and threshold timing checks.
- Used to benchmark algorithmic improvements against older method patterns.
