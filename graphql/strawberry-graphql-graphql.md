# Strawberry GraphQL GraphQL API

Strawberry is a code-first Python library for building GraphQL APIs using Python type hints and dataclasses. Rather than hosting a GraphQL endpoint, it is a framework developers embed in their own applications to generate and serve GraphQL schemas. It supports ASGI and WSGI integrations (Django, FastAPI, Flask, Litestar, Sanic, Chalice, AIOHTTP), queries, mutations, subscriptions over WebSocket, federation, dataloaders, and schema/field extensions.

The library generates GraphQL schemas from Python class decorators (`@strawberry.type`, `@strawberry.input`, `@strawberry.enum`, `@strawberry.interface`) and automatically translates Python snake_case identifiers to GraphQL camelCase. An interactive playground is available at the hosted demo environment.

**Endpoint:** N/A - library/tooling, no hosted endpoint (developers deploy their own GraphQL endpoint; a demo playground is at https://play.strawberry.rocks)

**Documentation:** https://strawberry.rocks/docs

**Authentication:** N/A - authentication is application-defined; the library provides context injection via `info.context` to propagate auth tokens or session data to resolvers.

**References:**
- Documentation: https://strawberry.rocks/docs
- GitHub: https://github.com/strawberry-graphql/strawberry
- Playground: https://play.strawberry.rocks
- PyPI: https://pypi.org/project/strawberry-graphql/
- Scalars reference: https://strawberry.rocks/docs/types/scalars
- Relay guide: https://strawberry.rocks/docs/guides/relay
- Federation guide: https://strawberry.rocks/docs/guides/federation
