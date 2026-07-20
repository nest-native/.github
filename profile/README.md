# nest-native

**NestJS integrations that feel like first-class NestJS packages.** Decorator-first, DI-native, full enhancer-pipeline support, zero runtime dependencies in every published package, and 100% test coverage as a hard CI gate.

## Packages

| Package | What it does | |
| --- | --- | --- |
| [`@nest-native/drizzle`](https://github.com/nest-native/drizzle) | Drizzle ORM integration — repositories, transactions (`@Transactional` via nestjs-cls), named connections, bring-your-own driver | [docs](https://nest-native.dev/drizzle/) · [npm](https://www.npmjs.com/package/@nest-native/drizzle) |
| [`@nest-native/trpc`](https://github.com/nest-native/trpc) | Typesafe APIs with tRPC v11 — `@Router`/`@Query`/`@Mutation`, guards/interceptors, generated `AppRouter`, SSE subscriptions, superjson | [docs](https://nest-native.dev/trpc/) · [npm](https://www.npmjs.com/package/@nest-native/trpc) |
| [`@nest-native/kafka`](https://github.com/nest-native/kafka) | Kafka on Confluent's official JS client — `@KafkaConsumer`/`@KafkaHandler`, producer service, in-memory test broker | [docs](https://nest-native.dev/kafka/) · [npm](https://www.npmjs.com/package/@nest-native/kafka) |
| [`@nest-native/messaging`](https://github.com/nest-native/messaging) | Transactional outbox + idempotent inbox on Drizzle (SQLite/Postgres/MySQL), in-process or Kafka transport — solves the dual-write problem | [docs](https://nest-native.dev/messaging/) · [npm](https://www.npmjs.com/package/@nest-native/messaging) |
| [`@nest-native/asyncapi`](https://github.com/nest-native/asyncapi) | AsyncAPI 3.0 documents for your event-driven API — decorators, Zod or JSON-Schema payloads, served UI | [docs](https://nest-native.dev/asyncapi/) · [npm](https://www.npmjs.com/package/@nest-native/asyncapi) |
| [`@nest-native/ai-sdk`](https://github.com/nest-native/ai-sdk) | Streaming AI endpoints on the AI SDK (`ai@7`) — `@AiStream`, abort on client disconnect, request context in tools, offline test models | [docs](https://nest-native.dev/ai-sdk/) · [npm](https://www.npmjs.com/package/@nest-native/ai-sdk) |
| [`@nest-native/jobs`](https://github.com/nest-native/jobs) | Background jobs without Redis — Drizzle-backed queue (SQLite/Postgres/MySQL), transactional enqueue, `@JobHandler` classes, retries/backoff | [docs](https://nest-native.dev/jobs/) · [npm](https://www.npmjs.com/package/@nest-native/jobs) |
| [`@nest-native/cache`](https://github.com/nest-native/cache) | tag-based cache invalidation through the database you already have — in-memory L1, invalidation over Postgres `LISTEN`/`NOTIFY` (transactional: delivered on commit) or a same-machine socket mesh, on a zero-dep core (`@stalefree/core`) with optional Drizzle L2 stores; no Redis | [docs](https://nest-native.dev/cache/) · [npm](https://www.npmjs.com/package/@nest-native/cache) |
| [`@nest-native/lockout`](https://github.com/nest-native/lockout) | django-axes-style login lockout — failure limits, tiered cooloff, `Retry-After`, on a zero-dep framework-agnostic core (`@authlock/core`) with atomic Drizzle stores (SQLite/Postgres/MySQL) | [docs](https://nest-native.dev/lockout/) · [npm](https://www.npmjs.com/package/@nest-native/lockout) |

## See them working together

The [**reference app**](https://github.com/nest-native/reference-app) is a multi-tenant work-tracking SaaS that composes the whole family under realistic backend pressure: every task write emits domain events through the transactional outbox, consumers build an activity feed through the idempotent inbox over Kafka, the event contracts are published as an AsyncAPI catalog, and a streaming AI assistant summarizes the activity — one coherent journey, green tests, no Docker required for the default profile.

## Principles

- **Feel native** — Nest modules, DI, decorators, lifecycle hooks; no functional wrappers around the underlying library.
- **Stay honest** — Drizzle stays SQL-first, tRPC stays tRPC; thin integrations, documented non-goals, claims backed by code and tests.
- **Zero runtime dependencies** — every package publishes `"dependencies": {}`; you only install the peers you actually use.

Docs hub: [nest-native.dev](https://nest-native.dev) · Issues and discussions welcome in each repo. Not affiliated with the NestJS core team.
