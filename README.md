# newton

A Claude Code engineering workflow. `/newton` matches a task to a playbook (bug fix, feature, refactor, investigation, perf, ship), copies its steps into a todo list, and runs them with verification at every step.

Builds on [pstack](https://github.com/cursor/plugins/tree/main/pstack) by Lauren Tan (MIT), adapted to ask-first autonomy and Claude-only review.

## Try it

```bash
claude --plugin-dir ~/newton-http/newton
```

Then run `/newton:newton <task>`.
