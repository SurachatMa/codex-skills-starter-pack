# User preferences: low-token workflow

These preferences override conflicting defaults in installed third-party skills. Follow system/developer instructions and the user's current request first.

- Routine work: `gpt-6.1-sol`, reasoning effort `low` (Light).
- Hard work: `gpt-6-astra`, reasoning effort `low` (Light). Use it for unresolved cross-system bugs, concurrency, subtle algorithms, or consequential architecture decisions. Return routine implementation to 6.1 low.
- Never raise effort to medium/high/xhigh/max/ultra or fall back to another model family unless the user explicitly changes this preference. A rejected model is a limitation to report, not permission to pick a stronger model.
- Config profiles set defaults, not automatic routing. Do not claim to switch the current chat model unless a supported control actually changed it. When delegation is allowed, give at most one difficult, bounded subtask to Astra low with fresh, minimal context. Otherwise tell the user which model to select for that part.
- Work in one agent by default. Multi-agent panels, races, reflection teams, and repeated independent reviews require an explicit request. For an explicitly requested panel, use two agents at most unless the user specifies more; normal workers use 6.1 low, only hard reasoning uses Astra low.
- Select one primary workflow per task. Routine implementation needs no process skill. Use pstack when requested, or Superpowers when requested, never both as mandatory pipelines. Do not recursively load every related skill or read skills merely because of a keyword.
- For routine edits, proceed from the available requirements. Brainstorm only unresolved design choices. Do not manufacture approval gates, design documents, commits, or PRs for small changes.
- Use one debugging method. Reproduce the failure and test the affected behavior. Use TDD when requested or when a cheap regression test materially reduces risk; do not force it on prose, settings, assets, or reversible trivial edits.
- Choose Impeccable for UI audit/polish or a complete UI workflow; frontend-design can supply aesthetic direction when needed. Do not run two complete design pipelines. For games, load only the chosen engine skill and the asset/playtest skill needed for the current step.
- pstack principles are references within an explicitly requested pstack workflow, not 24 independent global triggers. Unslop, TypeScript guidance, and review skills apply to relevant work, not every reply.
- Search narrowly, batch independent reads, return concise results, and reuse evidence already gathered. Send file paths and a short brief to delegated agents instead of full chat history. Use a plan only when multiple dependent steps need tracking.
- Verify the changed behavior once, fix actual failures, and stop after the relevant checks pass. Repeat or broaden checks only for new changes or unresolved risks. Never save tokens by omitting required safety checks, accessibility, correctness, or evidence.
- Answer concisely with the result, relevant verification, and any real limitation. No unsolicited diagrams, multi-option designs, reports, or token-saving percentages.
