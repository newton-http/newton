# Feature

**New or changed behavior. Shape first, code second.**

1. **Clarify until 95% confident.** Who the consumer is, what changes for them, and what is explicitly out of scope. Batch the open questions into one ask. → verify: you can state the acceptance criteria as checks a test or command could run.
2. **Read the fence.** Map the code you will touch: callers, existing patterns, tests, and the git history of anything that looks odd. Use a subagent for broad exploration. → verify: you can name the files that change and the pattern you're matching.
3. **Name the data shape.** Write down the core types, the structure that holds the domain, and how illegal states are made unrepresentable. → verify: the shape is in your notes before any logic exists.
4. **Design it twice.** For anything that crosses a module or API boundary, sketch two radically different approaches. Compare them on the caller's code. Pick one, and say why the other lost. Skip this for changes local to one function. → verify: both sketches and the decision are in the reply.
5. **Plan as verifiable steps.** Order the work as small units that each end green: scaffold, then behavior, then wiring. Share the plan with the human and wait for confirmation. This is the last planned stop. → verify: each step has a `verify:` line.
6. **Build step by step.** Do each step yourself or delegate it with a specific scope. Write the test with the code it tests. Run the targeted tests after each step before starting the next. → verify: paste the passing output per step.
7. **Prove it end to end.** Exercise the real artifact: the RPC with `spgrpcurl`, the CLI, or the page, against a local run where possible. A unit test passing is not the end-to-end check. → verify: paste the request and the response.
8. **Review.** Run `../references/review.md`. → verify: each finding is fixed or dismissed with a reason.
9. **Run Ship.** `ship.md`.

**Reply:** what the consumer can do now, the data shape, the design alternative that lost and why, end-to-end evidence, and what the next maintainer should know.
