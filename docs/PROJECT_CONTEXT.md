## Project Goal

- Build a minimal, scalable API Gateway in TypeScript for learning system design through implementation.
- Deliver functionality in very small, testable increments to reduce complexity and mistakes.
- Keep the gateway stateless and focused on core request handling responsibilities.
- Maintain a living context and decision log so progress and tradeoffs are easy to understand later.

## Non-Goals

- Building a full service mesh or full platform orchestration.
- Implementing advanced auth, policy engines, or multi-tenant governance.
- Adding complex resilience patterns (for example, full circuit breaker frameworks) at this stage.
- Supporting every production feature from day one.

## Architecture Overview

This project uses a stateless Fastify gateway with Postgres and Redis as supporting stores, focused on clear routing, basic resilience, and observable behavior while staying minimal.

- Fastify gateway (stateless)
- Postgres for config snapshots and versions
- Redis for rate limiting, idempotency, and caching
- Canary routing (A/B by percentage)
- Timeouts and basic resilience
- Observability with pino logs and `/metrics`

## Request Lifecycle

1. Receive request at gateway and assign request context (request ID, timing start).
2. Match route and load relevant config snapshot/version.
3. Apply rate limiting and idempotency checks (Redis-backed).
4. Evaluate canary routing decision (A/B by configured percentage).
5. Forward request to selected upstream with timeout controls.
6. Return response, including fallback/error handling for timeout and upstream failures.
7. Emit structured logs and metrics for request outcome and latency.

## Implementation Strategy

### Step-by-step approach

- Follow the Minimal Step Rule: implement exactly one small feature per step.
- Keep each step scoped so it can be explained, tested, and reviewed quickly.
- Prefer simple, direct implementations before adding abstraction.
- Record lessons and corrections immediately when issues or decision changes occur.

### Definition of Done template

- Feature: [single small feature]
- Scope: [what is included]
- Out of scope: [what is intentionally not included]
- Behavior verified: [manual or automated check performed]
- Observability added: [logs and/or metrics touched, if applicable]
- Docs updated: [this file updated if decisions or lessons changed]

## Current State

- Not implemented yet.

## Next Step

- [To be defined]

## Lessons Learned

- [No lessons recorded yet]

## Corrections / Changes

- [No corrections recorded yet]
