# Adversarial AI Engineer

Systems that survive contact with reality.

**Live:** [portfolio-nextjs-roan.vercel.app](https://portfolio-nextjs-roan.vercel.app)

---

## Impact

- **25× latency cut** — query rewrite hot path, 847ms → 34ms per request
- **55× throughput gain** — batch inference pipeline, 4.8 days → 2.1 hours
- **Zero regressions** — 3.2k-LOC legacy-to-Rust migration, single-cycle cutover

---

## Selected Work

Independent R&D. Numbers below are measured, not estimated.

### Query Rewrite — 25× Latency Reduction
Hot-path semantic rewrite sitting between user query and retrieval. Baseline p50: 847ms, measured over 10k requests. Root cause: three sequential model calls on a cache-miss path with no batching. Collapsed to a single call with a precomputed embedding index and a 1-layer classifier. Post-change p50: 34ms. Error rate unchanged.

### Batch Pipeline — 55× Throughput Gain
Batch job running embedding + classification + scoring over ~42M records. Wall-clock: 4.8 days per cycle. Bottleneck was sequential I/O on an NFS-mounted source. Rewrote as three parallel streams with local staging and a bounded work queue. New wall-clock: 2.1 hours. Same accuracy on holdout, lower memory ceiling.

### Legacy Modernization — C++ to Rust, Zero Regressions
Port of a numerical-methods core, several thousand LOC. Approach: property-based parity tests against the original before a single line was rewritten. Contract was the test suite, not the code. Cut over in one deploy. Follow-up instrumentation showed no correctness regressions and a 4× reduction in runtime memory.

---

## Stack

Next.js 15 · React 19 · TypeScript · Rust · Python · Vercel

---

## Contact

mpuodziukas@gmail.com
