# Investigation

**A read-only question. The deliverable is a cited answer, not a code change.**

1. **Restate the question** as one sentence with what a complete answer contains. If the question is ambiguous, present the readings and ask. → verify: the human would recognize the question.
2. **Fan out.** Spawn parallel read-only subagents per evidence source that applies: the code path (entry point to side effect), tests, git history and PRs for why, and docs, Slack, or Jira through MCP when the question is about intent or decisions. → verify: each agent returns `file:line` or link citations, not prose alone.
3. **Confirm the load-bearing claims at runtime** when a claim decides the answer and a check is cheap: run the test, call the endpoint, read the config value. → verify: each load-bearing claim is labeled measured or read in code.
4. **Answer.** Lead with the direct answer, then the trail. Don't edit code. If the investigation surfaced a bug or a better design, name it and offer the matching playbook.

**Reply:** the answer first, then a short walkthrough with `file:line` citations, each claim labeled measured, read in code, inferred, or guess, and open questions.
