# StatSQLi Documentation

StatSQLi is a research-focused framework for improving the speed and reliability of **time-based blind SQL injection testing in controlled environments**. It combines statistical hypothesis testing, binary-search extraction, and optional parallelization.

This documentation is designed to be **ready to deploy** with MkDocs and useful for:

- researchers documenting methodology and results,
- students learning timing-side-channel concepts,
- security testers validating ideas in isolated lab targets.

## What this project includes

- A Python package (`statsqli`) with extraction logic and CLI.
- A deliberately vulnerable local lab app (`lab/app.py`) for reproducible testing.
- Benchmark scripts (`benchmarks/`) for comparing approaches and generating figures.
- A report-driven methodology based on Welch's t-test and binary search.

## Key ideas in one minute

- Traditional time-based extraction often uses linear probing over ASCII values.
- StatSQLi models timing decisions as a statistical test (Welch t-test).
- Character inference uses binary search to reduce per-character query complexity.
- Delay selection is adaptive using baseline timing behavior.

## Documentation map

- Start with [Getting Started](getting-started.md) for installation and first run.
- Read [Report Summary](report-summary.md) for the research context.
- Use [CLI Guide](user-guide/cli-guide.md) and [Python API Guide](user-guide/python-api.md) for daily usage.
- Explore [Technical Deep Dive](technical/architecture.md) pages for implementation details.
- Follow [Deployment](safety/deployment.md) to publish docs to GitHub Pages or similar platforms.

## Safety notice

This project must be used only for systems you own or are explicitly authorized to test. The included vulnerable apps are for educational lab use and should not be exposed publicly.
