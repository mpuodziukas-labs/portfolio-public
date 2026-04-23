# Adversarial AI Engineer

Systems that survive contact with reality.

**Live:** [portfolio-nextjs-roan.vercel.app](https://portfolio-nextjs-roan.vercel.app)

---

## Impact

- **25× latency cut** — query rewrite hot path, 847ms → 34ms per request
- **55× throughput gain** — batch inference pipeline, 4.8 days → 2.1 hours
- **Zero regressions** — 3.2k-LOC legacy-to-Rust migration, single-cycle cutover

---

## Case Studies

### Query Rewrite — 25× Latency Reduction
Hot-path semantic rewrite sitting between user query and retrieval. Measured p50 at 847ms. Root cause: three sequential model calls on a cache-miss path with no batching. Collapsed to a single call with a precomputed embedding index and a 1-layer classifier. p50 landed at 34ms. Error rate unchanged.

### Batch Pipeline — 55× Throughput Gain
Legacy batch job processing embedding + classification + scoring over ~42M records. Ran for 4.8 days per cycle. Bottleneck was sequential I/O on an NFS-mounted source. Rewrote as three parallel streams with local staging and a bounded work queue. Pipeline now finishes in 2.1 hours. 98% throughput improvement, same accuracy, lower memory ceiling.

### Legacy Modernization — 3.2k LOC, Zero Regressions
Port of a numerical-methods core from C++ to Rust. Approach: property-based parity tests against the original before a single line was rewritten. Contract was the test suite, not the code. Cut over in one deploy. Follow-up instrumentation showed no correctness regressions and a 4× reduction in runtime memory.

---

## Stack

Next.js 15 · React 19 · TypeScript · Rust · Python · Vercel

---

## Contact

mpuodziukas@gmail.com
