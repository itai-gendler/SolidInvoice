---
kind: system
acts: external
references:
- kind: code
  role: implementation
  target: src/McpBundle/Entity/OAuthClient.php
- kind: code
  role: implementation
  target: src/McpBundle/Entity/ConsentGrant.php
- kind: code
  role: implementation
  target: src/McpBundle/Action/Authorize.php
- kind: doc
  role: context
  target: docs/docs/ai/mcp-server.mdx
---

# AI agent

An AI agent harness, such as Claude, Cursor or Codex, that a User connects to one company through the MCP server and that then reads, and with write access changes, that company's billing on the User's behalf.

## Information kept

- **Name** — the name the agent registered under
- **Write access** — whether the User granted write access as well as read access

## States

### Connected

The agent can call the MCP server for the company it was connected to.

### Revoked

The User revoked the agent; its tokens no longer work.
