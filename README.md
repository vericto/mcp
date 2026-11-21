# Vericto MCP servers

Database guardrails for AI agents, over MCP. This repository holds the published
manifests for Vericto's two **hosted** MCP servers, so clients and registries have a
public source to inspect. The servers themselves are operated by Vericto S.A.S.

| Server | Endpoint | Auth | What it is for |
|---|---|---|---|
| `com.vericto/mcp` | `https://mcp.vericto.com/mcp` | `X-API-Key` header | Check SQL against your Vericto rules before it runs. For CI, scripts and agents that already hold a key. |
| `com.vericto/account` | `https://mcp.vericto.com/mcp/account` | OAuth | Your workspace over OAuth: setup status, rules, CI reports, docs search and SQL checks. |

Manifests: [`server.json`](server.json) (`com.vericto/mcp`) and
[`server-account.json`](server-account.json) (`com.vericto/account`), both against
the `2025-12-11` MCP server schema.

## Want Vericto to run SQL on your own database instead?

Use the **local** server, `vericto-proxy mcp`, from
[vericto/vericto-proxy](https://github.com/vericto/vericto-proxy). It runs on your
machine, gives the agent `execute_sql`, `describe_schema`, `check_sql` and `whoami`
and **no database credential**, and executes every statement read-only inside a
transaction that always rolls back, after evaluating it. PostgreSQL, MySQL and
MariaDB. It needs no Vericto account: with no control plane configured it runs on the
built-in ruleset and reports nothing anywhere. It is published to the MCP registry as
`com.vericto/vericto-proxy`.

## Client setup

Setup for Claude Code, Claude Desktop, Cursor, VS Code, Codex and generic MCP clients
is in <https://vericto.com/docs/mcp>, and for the local server in
[docs/MCP.md](https://github.com/vericto/vericto-proxy/blob/main/docs/MCP.md).

## Links

- Docs: <https://vericto.com/docs/mcp>
- Privacy: <https://vericto.com/privacy> · Terms: <https://vericto.com/terms>
- Security contact: see <https://github.com/vericto/vericto-proxy/blob/main/SECURITY.md>
