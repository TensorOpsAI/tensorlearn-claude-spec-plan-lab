# Current constraints
Provider: at most 50 requests/second and 20 messages per batch. A released result version is the idempotency key. Bounded retries must not create duplicate deliveries. Log event IDs and delivery states only; never patient identifiers or clinical payloads.
Existing portal route is src/portal/result-route.mjs. Existing queue adapter is src/service/queue.mjs. Tests should cover release gating, privacy, duplicate retries and boundary throughput.
