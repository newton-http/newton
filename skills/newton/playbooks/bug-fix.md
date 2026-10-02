# Bug fix

**You own the task. Subagents attempt fixes. You verify.** Every shipped line traces to evidence. A change that "might help" is a hypothesis, not a fix, and it doesn't ship.

1. **Clarify the symptom.** Expected versus actual behavior, the input or request that triggers it, and where it was seen. Observe what you can yourself before asking. → verify: you can state the bug as one sentence with a concrete trigger.
2. **Write a failing test that reproduces it.** Prefer an integration-level test that calls the code the way its users do and asserts the literal expected value. Run it and watch it fail for the right reason. If it won't reproduce, tighten conditions or add instrumentation until it does. Don't move on with an unreproduced bug. → verify: paste the failing output and confirm the failure message matches the symptom.
3. **Root-cause it.** List the candidate hypotheses. Rule them out with evidence (logs, a debugger, a narrower test, git history for when it regressed) until one mechanism survives. Use subagents for broad searches. → verify: you can explain the mechanism and point to the line where behavior diverges.
4. **Delegate the fix.** Spawn one or more subagents with the failing test, the confirmed mechanism, and a specific scope. For a nontrivial fix, run two agents in parallel with different approaches and keep the smaller one that passes. Each agent must run the test and paste the output. → verify: you read each diff yourself.
5. **Prove it.** Run the repro test and the surrounding test suite yourself. The repro passes, nothing else regresses. → verify: paste the failing-then-passing output.
6. **Review.** Run `../references/review.md` on the diff. → verify: each finding is fixed or dismissed with a concrete reason.
7. **Stage the commits.** The failing test lands in a commit before the fix, or the test and fix share one commit if a red commit would break CI policy. → verify: `git log` reads as repro, then fix.
8. **Run Ship.** `ship.md`.

**Reply:** what was broken, the root cause, the fix, failing-then-passing output, and anything the review dismissed with reasons.
