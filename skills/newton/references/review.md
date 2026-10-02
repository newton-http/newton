# Adversarial review

Three independent reviewers try to break the diff. Launch them in one message so they run in parallel. Each gets the diff range (`git diff <base>...HEAD`), the task's acceptance criteria, and one lens. Each returns findings as `file:line`, severity, the failure scenario (concrete input or state leading to wrong output or a crash), and a suggested fix. No praise, no style nits unless they change meaning.

## Lenses

1. **Correctness.** Hunt for inputs, states, and orderings that produce wrong results: edge cases, null and empty handling, error paths, concurrency, context propagation, retries, and partial failure. Try to write the failing test for each finding.
2. **Design.** Review as a senior teammate would. Does the shape fit the domain? Is there a simpler design? Are there shallow layers, scattered conditionals, leaky boundaries, or code that ignores an existing pattern in the repo? Does any change reach beyond the ask?
3. **Verification.** Do the tests prove the behavior, or would they pass with the logic deleted? Is the end-to-end claim backed by real output? What's untested that could break in production?

## Triage

You own the verdict. For each finding:

- **Confirm** it by reading the code or writing the failing test. Fix confirmed findings. A finding two lenses raised independently is high signal.
- **Dismiss** with a concrete reason: a disproof, not "seems fine".
- **Escalate** anything touching auth, data deletion, billing, or migrations to the human instead of dismissing it yourself.

List fixed and dismissed findings in the reply.
