# MCP tools

Tools always return short summaries, never raw dumps.

## telemetry-mcp (read only)

| Tool | Inputs | Returns |
| --- | --- | --- |
| `list_services()` | none | service names and dependencies |
| `get_latency(service, minutes)` | service, 1-60 | p50/p95 now vs. 30 min ago, minute it started rising |
| `get_error_rate(service, minutes)` | service, 1-60 | error rate now vs. before, top 3 status codes |
| `get_db_pool(service)` | service | connections in use / max, waiting requests |
| `get_redis_latency(minutes)` | 1-60 | Redis p95 now vs. before |
| `search_logs(service, level, text, minutes)` | service, level, text, 1-60 | count, top 3 messages, 5 sample lines with trace IDs |
| `get_slow_traces(service, limit)` | service, 1-10 | per trace: total time and slowest span |

## knowledge-mcp (read only)

| Tool | Inputs | Returns |
| --- | --- | --- |
| `search_runbooks(query, k)` | text, 1-5 | top runbook sections with similarity score |
| `search_past_incidents(query, k)` | text, 1-5 | resolved incidents with root cause and fix |

## actions-mcp (changes things, approval required)

| Tool | Allowed targets |
| --- | --- |
| `get_container_status()` | read only, all ShopLite containers |
| `restart_container(name, idempotency_key)` | ShopLite containers only |
| `rollback_service(name, idempotency_key)` | gateway, orders, payments |
| `set_config(service, key, value, idempotency_key)` | `DB_POOL_MAX` (10-100), `SLOW_QUERY_ENABLED` |

actions-mcp refuses any call without an approved record in `actions_audit`, refuses unknown targets or keys,
and logs every call.
