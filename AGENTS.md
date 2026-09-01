# Agent Instructions
## Commands
| Task    | Command                           |
| ------- | --------------------------------- |
| Install | none — static HTML/CSS site, no build step |
| Test    | none                               |
| Lint    | none                               |
| Format  | none                               |
## Rules
- Read relevant code before answering. Ground every claim in inspected files.
- Make surgical, atomic changes. One logical change per commit.
- Run the test command before every commit.
- Use conventional commits: `feat:`, `fix:`, `refactor:`, `docs:`, `test:`, `chore:`.
- No bare `except:`. No commented-out code. No global mutable state.
- Write or update tests alongside every behaviour change.
- A check that has never failed is unverified: before trusting a green run, break what it guards and confirm it goes red.
- Beware vacuous passes: a rule over "all X" holds when X is empty, and a total over groups holds when one group is zero. Assert per group that the check examined something.
- Before any PR, run one bounded background/stateful cross-family review from the table below when supported, fix blockers, then confirm with the same agent.
- Add `<!-- review-pass: coder=<coder-id> reviewer=<reviewer-id> effort=high -->` to the PR body; unavailable routing requires a `Cross-family review skipped:` reason.

| Coder family | Prefix | Reviewer | Effort |
| --- | --- | --- | --- |
| Claude | `claude-*` | `gpt-5.6-sol` | `high` |
| GPT | `gpt-*` | `claude-opus-5` | `high` |
## Boundaries
### Always
- Run lint and tests before claiming done.
- Keep changes branch-based and open a PR for review.

### Ask first

- Broad refactors or architectural changes.
- Adding, upgrading, or removing dependencies.
- Changing a public interface or API contract.

### Never

- Commit secrets, credentials, or tokens.
- Leave the test suite red.
- Rewrite git history unless explicitly requested.
