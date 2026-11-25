# Express API endpoints

| Method + path | Does |
| --- | --- |
| `GET /api/incidents` | list incidents, newest first |
| `GET /api/incidents/:id` | one incident with triage, evidence, root cause, proposal, timeline |
| `GET /api/incidents/:id/stream` | live agent steps (Server-Sent Events) |
| `POST /api/ask` | start an investigation from a question |
| `POST /api/incidents/:id/approve` | approve the proposed action |
| `POST /api/incidents/:id/reject` | reject; body `{ "reason": "..." }` is required |
| `GET /api/metrics` | OpsPilot's own Prometheus metrics |
