# Report Summary

This page summarizes the project report: **"StatSQLi: A Statistical Framework for Accelerated Time-Based Blind SQL Injection."**

## Problem statement

Time-based blind SQL injection is slow because data must be inferred indirectly from response timings. Traditional extraction often:

- uses static delays,
- applies threshold-based decisions,
- probes characters linearly.

These choices make extraction expensive and sensitive to network jitter.

## Proposed framework

The report presents StatSQLi with three main improvements:

1. **Statistical timing validation** via Welch's unequal-variance t-test.
2. **Binary-search character inference** instead of linear ASCII probing.
3. **Adaptive delay and optional parallel extraction** for practical speedup.

## Core contributions

- A modular implementation with clear components (`adaptive`, `stats`, `extractor`, `parallel`).
- A benchmark pipeline comparing StatSQLi, SQLMap, and a traditional linear baseline.
- Visualization scripts for publication-quality figures.

## Experimental highlights from the report

- Query cost per character reduced from roughly linear probing to logarithmic behavior.
- Representative benchmark showed meaningful speedups versus baseline approaches.
- Statistical decision logic improved robustness under jittered timing conditions.

## Scope and constraints

The report and code focus on **lab-controlled targets** and educational/research usage. The evaluation emphasizes:

- reproducibility,
- comparative performance,
- methodological clarity.

It does not claim universal behavior across all production environments or defensive stacks.
