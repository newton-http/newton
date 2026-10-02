# Perf

**Measure, then change. Every win is a before and after number.**

1. **Define the metric and target.** Which operation, which percentile or total, measured how, and what number counts as done. → verify: one sentence each for the metric, the method, and the target.
2. **Baseline.** Measure the current number with a repeatable script or command, run enough times to see the variance. → verify: paste the baseline and its spread.
3. **Profile before guessing.** Find where time goes: traces, timing logs, a profiler, or counting calls. Check network and RPC fan-out first (N+1 calls, serial calls that could run in parallel, missing batching), because they dominate CPU. → verify: the top cost centers are listed with measured share.
4. **Hypothesize and change one thing.** Pick the biggest measured cost. Make one change aimed at it. In Java services, parallelize with structured concurrency, not `CompletableFuture.supplyAsync`. → verify: tests still pass.
5. **Re-measure with the same script.** Keep the change only if the win clears the noise. Revert changes that don't move the number. → verify: paste before and after.
6. **Repeat steps 4 and 5** until the target is met or the remaining costs are out of scope. One commit per accepted win.
7. **Review.** Run `../references/review.md`, with extra attention to correctness under concurrency and caching staleness. → verify: findings fixed or dismissed.
8. **Run Ship.** `ship.md`.

**Reply:** the metric, baseline versus final with spread, each accepted change and its measured contribution, reverted hypotheses, and remaining cost centers.
