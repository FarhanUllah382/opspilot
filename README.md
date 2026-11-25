# OpsPilot

AI-powered incident investigation and resolution platform (CS351 Artificial Intelligence, semester project).

We build a small online shop (**ShopLite**), monitor it like a real company, break it on purpose, and **OpsPilot**
finds what broke, explains why with real evidence, and fixes it only after a human clicks **Approve**.

> The AI never guesses and never acts alone.

## Repository layout

| Folder | What lives here | Owner |
| --- | --- | --- |
| `shoplite/` | gateway, orders, payments services (TypeScript) + k6 load script | Person C |
| `chaos/` | fault-injection scripts and their ground-truth labels | Person B |
| `observability/` | OpenTelemetry Collector, Prometheus, Loki, Jaeger, Grafana configs | Person C |
| `opspilot-ai/ml/` | feature extraction, Isolation Forest, Random Forest | Person B |
| `opspilot-ai/agents/` | LangGraph graph and the 4 agents | Person A |
| `opspilot-ai/rag/` | runbooks and the ingestion script (pgvector) | Person A |
| `mcp-servers/` | telemetry-mcp, knowledge-mcp, actions-mcp | Person A |
| `opspilot-api/` | Express + TypeScript API | Person C |
| `dashboard/` | web UI (incidents, approve/reject) | Person C |
| `evals/` | scenarios, recorded tool outputs, evaluation harness | Person B |
| `contracts/` | shared JSON shapes, tool list, API endpoints (change only with everyone's approval) | Everyone |
| `docs/` | design docs, diagrams, report material | Everyone |

## How we work

Read [CONTRIBUTING.md](CONTRIBUTING.md) before your first commit. Short version:

1. Every task is a GitHub Issue on the project board.
2. Work on a branch: `feat/<issue-number>-<short-name>`.
3. Open a pull request, CI must pass, one teammate must approve.
4. Squash and merge. Never push directly to `main`.

## Running locally (once the stack exists)

```bash
cp .env.example .env      # add your LLM API key
make up                   # start all containers
make chaos SCENARIO=redis # break something
make reset                # remove all faults
make down                 # stop everything
```

Needs Docker Desktop with about 8 GB of free RAM.
