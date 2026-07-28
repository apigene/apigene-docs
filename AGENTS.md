# AGENTS.md

## Repo role

Customer-facing documentation site for Apigene, built with [Mintlify](https://mintlify.com). Covers user guides, admin guides, and API reference.

Does **not** own:
- Platform runtime code → `apigene-backend`, `apigene-copilot`, `apigene-mcp-next`
- Marketing/landing pages → `apigene-website`

## Sibling repos

| Repo | Relationship |
|------|--------------|
| `apigene-backend` | API reference should match backend endpoints |
| `apigene-copilot` | User guide content describes this UI |
| `apigene-mcp-next` | MCP gateway docs |
| `apigene-docker-compose` | Self-hosted setup guides |

## Start here

| Area | Path |
|------|------|
| Site config / nav | `docs.json` |
| User guide | `user-guide/` |
| Admin guides | `guides/` |
| API reference | `api-reference/` |
| OpenAPI schema | `api-reference/openapi.json` |
| Landing page | `index.mdx` |

## Directory map

```
docs.json              # Mintlify config, navigation, theme
user-guide/            # Product features (copilot, agents, MCP, skills, …)
guides/                # Getting started, admin, connectors
api-reference/         # Per-endpoint MDX pages + openapi.json
index.mdx              # Docs home page
```

## Common change paths

### Add or update user-facing feature docs

1. Add/edit `.mdx` under `user-guide/` or `guides/`
2. Register page in `docs.json` navigation
3. Preview locally with `mintlify dev`

### Add or update API reference

1. Update endpoint `.mdx` in `api-reference/<area>/`
2. Update `api-reference/openapi.json` if schema changed
3. Register in `docs.json` under API Reference tab
4. Verify against `apigene-backend` actual endpoints

### MCP gateway documentation

- Pages under `user-guide/mcp-gateway/`
- Keep in sync with `apigene-mcp-next` behavior and URL formats

## Local dev

```bash
npm i -g mintlify
mintlify dev    # from repo root (where docs.json lives)
```

Site preview runs locally; changes deploy automatically on push to default branch via Mintlify GitHub App.

## Conventions

- **Format:** MDX with Mintlify components
- **Nav:** All pages must be listed in `docs.json`
- **API docs:** One MDX file per endpoint under `api-reference/`
- **Audience:** Customer/admin users, not internal engineering runbooks

## Cross-repo impact

| Change here | Triggered by |
|-------------|--------------|
| API reference update | `apigene-backend` endpoint changes |
| MCP docs update | `apigene-mcp-next` protocol or URL changes |
| Self-hosted guides | `apigene-docker-compose` or `apigene-helm-chart` setup changes |
| Copilot feature docs | `apigene-copilot` UI changes |

## Safe defaults for agents

- Preview with `mintlify dev` before committing nav changes
- Keep API reference aligned with backend, not aspirational
- Use `user-guide/` for product features, `guides/` for setup/admin
- Do not put internal engineering runbooks here — use per-repo `AGENTS.md`
