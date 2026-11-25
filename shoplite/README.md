# ShopLite

The fake online shop we break on purpose. Owner: Person C.

- `gateway/`, `orders/`, `payments/`: Express + TypeScript services
- `k6/`: load script sending about 20 requests per second to `POST /checkout`

Every service exposes `POST /checkout` (gateway only), `GET /health` and `GET /metrics`,
and writes JSON logs with `timestamp`, `level`, `service`, `message`, `trace_id`.
