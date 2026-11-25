# Failure scenarios (answer key)

| # | Script | Breaks | Correct root cause | Correct fix |
| --- | --- | --- | --- | --- |
| 1 | `chaos/redis-latency.sh` | Toxiproxy adds 5 s delay to Redis | `redis` | `restart_container(redis)` |
| 2 | `chaos/db-pool.sh` | `DB_POOL_MAX=2` on orders | `orders` DB pool | `set_config(orders, DB_POOL_MAX, 20)` |
| 3 | `chaos/bad-deploy.sh` | payments image v2 (30% errors) | `payments` bad deploy | `rollback_service(payments)` |
| 4 | `chaos/slow-query.sh` | `SLOW_QUERY_ENABLED=true` on orders | `orders` slow query | `set_config(orders, SLOW_QUERY_ENABLED, false)` |

Extra cases: a no-fault run (correct answer: nothing is wrong) and a two-faults run.
Each script writes a JSON label: fault type, start time, target service, correct fix.
