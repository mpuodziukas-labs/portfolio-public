# Michael Puodziukas — Agentic AI Engineer

**Red Team · Systems · Data | Agents that find the failure before it ships.**

**Live:** [michaelpuodziukas.com](https://michaelpuodziukas.com)

---

## Impact

Independent R&D. Numbers below are measured, not estimated.

- **96%** per-query latency cut — Baseline p50: 847ms (10k requests). Post-change p50: 34ms.
- **98%** batch pipeline reduction — 4.8d → 2.1h end-to-end
- **$2.3M** payroll misallocation root-caused — COBOL arithmetic boundary, CFO sign-off on file
- **27×** throughput gain — COBOL/Fortran → Rust, byte-exact arithmetic parity (IEEE 754 ≤1e-10)
- **0** adversarial false negatives — 24-month window, 8-agent validation gate
- **$745K** annual savings — VSAM batch optimization, CFO-quantified

---

## Selected Work

### Semantic Router — 96% Per-Query Latency Cut
Priority-classified routing layer sitting between query intake and retrieval. Baseline p50: 847ms measured over 10k requests. Root cause: sequential blocking calls on cache-miss paths with no batching. Replaced with async pipeline, local HNSW index, and semantic reranking. Post-change p50: 34ms. Error rate unchanged. 47,000+ deterministic replays, 0% divergence.

### Batch Pipeline — 98% End-to-End Reduction
Batch job running classification and scoring over 50M+ records per cycle. Wall-clock: 4.8 days. Bottleneck was sequential I/O with no parallelism. Redesigned as event-sourced deterministic architecture with parallel stream processing. New wall-clock: 2.1 hours. Every decision logged and replay-verifiable. 0 late payroll cycles in 24 months.

### COBOL/Fortran → Rust — 27× Throughput, Byte-Exact
Port of a financial computation core, several thousand LOC. Approach: property-based parity tests against the original before a single line was rewritten. Arithmetic parity maintained to ≤1e-10 across every field and boundary case — COBOL decimal arithmetic vs Rust IEEE 754 requires re-deriving the arithmetic at every boundary, not just porting the code. 27× throughput. 85% memory reduction. 0 CVEs introduced. Several hundred integration tests, 100% pass.

### LLM Validation Gate — 0 False Negatives, 24 Months
8-agent adversarial gate evaluating every LLM output before it reaches production. Same adversarial methodology that caught the COBOL payroll bug: attack the input space, don't watch the output. Each agent evaluates a distinct failure class — architectural separation prevents correlated bypasses. Block on any single agent fail. Gate latency: <1ms P99. 24-month production window, 0 false negatives shipped.

---

## Stack

Next.js 15 · React 19 · TypeScript · Rust · Python · COBOL · Vercel

---

## Contact

mpuodziukas@gmail.com · Remote-only · No recruiters · Async-first
