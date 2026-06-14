# Strawberry GraphQL Rate Limits

Strawberry GraphQL is a self-hosted open-source library. There are no rate limits imposed by the Strawberry project itself — rate limiting is entirely the responsibility of the application developer and the infrastructure where Strawberry is deployed.

## Library-Level Controls

Strawberry does not ship built-in rate limiting middleware, but it provides extension points that allow developers to implement rate limiting:

- **Schema Extensions** (`strawberry.extensions`) — custom extensions can intercept query execution to enforce per-query or per-operation limits.
- **Field Extensions** — per-resolver logic can enforce fine-grained limits on individual fields.
- **Middleware / ASGI/WSGI layers** — framework-level middleware (e.g., Django middleware, FastAPI dependencies) is the most common pattern for rate limiting Strawberry-powered APIs.

## Recommended Approaches

| Layer | Tool / Pattern |
|---|---|
| HTTP / reverse proxy | nginx `limit_req`, Caddy rate limit module, AWS API Gateway throttling |
| ASGI middleware | `slowapi` (Starlette/FastAPI), custom `starlette.middleware` |
| Django | `django-ratelimit`, DRF throttling classes |
| GraphQL depth / complexity | `strawberry-django` query complexity extensions or custom `strawberry.extensions.QueryDepthLimiter` |

## Query Complexity

Runaway or deeply nested GraphQL queries can exhaust server resources. Developers are encouraged to:

1. Use query depth limiting via Strawberry's built-in `QueryDepthLimiter` extension.
2. Implement query complexity analysis using custom extensions.
3. Set execution timeouts at the ASGI/WSGI server level (e.g., uvicorn `--timeout-keep-alive`).

## Notes

- No hosted Strawberry GraphQL API endpoint exists that would impose centrally managed rate limits.
- Consult your hosting provider's documentation for infrastructure-level quotas (e.g., Fly.io, Railway, AWS Lambda).
