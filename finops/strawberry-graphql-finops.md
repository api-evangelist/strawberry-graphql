# Strawberry GraphQL FinOps

Strawberry GraphQL is a free, open-source MIT-licensed library. There is no licensing cost associated with using Strawberry. All FinOps considerations relate to the infrastructure and tooling required to run applications built with it.

## Direct Costs

| Item | Cost |
|---|---|
| Strawberry GraphQL library | $0 (MIT license) |
| PyPI package distribution | $0 |
| GitHub repository access | $0 (public repositories) |

## Infrastructure Costs (Developer Responsibility)

The following costs arise from operating a Strawberry-powered GraphQL API:

### Compute
- Application servers (EC2, Cloud Run, Fly.io, Railway, Heroku, etc.) hosting the ASGI/WSGI application.
- Serverless functions (AWS Lambda, Google Cloud Functions) if using serverless deployment patterns.

### Networking
- Egress bandwidth costs from the cloud provider serving GraphQL responses.
- CDN costs if caching static schema introspection or documentation assets.

### Database / Storage
- Cost of backing datastores (PostgreSQL, MongoDB, Redis, etc.) queried by Strawberry resolvers.
- DataLoader caching layer (typically in-memory or Redis) to batch and deduplicate backend calls.

### Observability
- Logging, tracing, and APM costs (Datadog, Honeycomb, Sentry, etc.) for monitoring GraphQL query performance.
- Query complexity and depth metrics are recommended to catch expensive operations early.

## Cost Optimization Tips

1. **DataLoader pattern** — Strawberry's built-in DataLoader support batches resolver calls, significantly reducing the number of database round-trips and lowering database compute costs.
2. **Query complexity limits** — Restricting maximum query depth and complexity prevents runaway queries that waste compute.
3. **Caching** — Schema introspection results and stable query responses can be cached at the HTTP or CDN layer.
4. **Async resolvers** — Strawberry's async-first design allows high concurrency on fewer compute instances.

## Open Collective Contributions

Optional financial contributions to the Strawberry project can be made at:
https://opencollective.com/strawberry-graphql

These contributions fund maintainer time and project infrastructure but are voluntary.
