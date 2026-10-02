# Refactor

**Behavior-preserving change to structure. Small steps, green between every one.**

1. **Name the target shape and the reason.** What gets simpler for the reader or the next change? If you can't say, the refactor doesn't earn its place. Say so. → verify: one sentence each for the before shape, the after shape, and the payoff.
2. **Read the fence.** Check blame, tests, and comments on the code that looks wrong before you change it. → verify: each "ugly" part has a known reason or a confirmed absence of one.
3. **Pin current behavior.** Make sure tests cover the behavior you're about to move. If they don't, add characterization tests first and commit them separately. → verify: tests pass on the unchanged code.
4. **Subtract first.** Delete dead code and redundant layers in the area before restructuring. → verify: tests still pass.
5. **Move in small steps.** One mechanical transformation per step (extract, inline, rename, move). Prefer a tool or script over hand edits when a change repeats across many sites. Keep compatibility while callers migrate, and delete the old path once nothing uses it. → verify: tests pass after every step, and no step breaks the build.
6. **Diff for behavior changes.** Read the full diff hunting for anything that isn't purely structural: changed defaults, error handling, ordering, logging. → verify: none found, or each one is split out and called out.
7. **Review.** Run `../references/review.md`. → verify: findings fixed or dismissed with reasons.
8. **Run Ship.** `ship.md`. Commits follow the steps above so the reviewer can follow the story.

**Reply:** the before and after shape, the payoff, proof that behavior is unchanged, and any behavior change you found and split out.
