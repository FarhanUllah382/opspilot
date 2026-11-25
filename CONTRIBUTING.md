# Contributing to OpsPilot

## Daily workflow

1. Pick a task (GitHub Issue) from the project board and move it to **In progress**.
2. Update `main` and create a branch:
   ```bash
   git checkout main && git pull
   git checkout -b feat/12-telemetry-get-latency
   ```
3. Commit small and often (see message format below).
4. Push and open a pull request. Write `Closes #12` in the description.
5. Wait for CI to pass and for one teammate to approve.
6. **Squash and merge**, then delete the branch.

Pull `main` every morning. A branch should live 1 to 3 days, not 2 weeks.
Keep pull requests under about 400 changed lines so they are easy to review.

## Branch names

| Prefix | Use for |
| --- | --- |
| `feat/` | new functionality |
| `fix/` | bug fixes |
| `docs/` | documentation only |
| `chore/` | config, dependencies, CI |

## Commit messages

`<type>(<area>): <what changed>`, for example:

- `feat(mcp): add get_latency tool`
- `fix(api): require a reason when rejecting`
- `docs(readme): explain chaos scripts`

Areas: `shoplite`, `chaos`, `obs`, `ml`, `agents`, `rag`, `mcp`, `api`, `dashboard`, `evals`, `ci`, `contracts`.

## Reviewing

- Read the code, run it if you can, ask questions in comments.
- Approve only when you understand what it does.
- Be kind and specific: "this tool returns raw logs, can it return a summary?" beats "this is wrong".

## Rules

- **Never commit secrets.** `.env` is ignored; only `.env.example` is committed. CI uses GitHub Secrets.
- **Contracts are shared.** Any change in `contracts/` needs approval from all three members.
- **No direct pushes to `main`.** Branch protection enforces this.
- **Your own work, your own commits.** Instructors may check commit history for individual contribution.
