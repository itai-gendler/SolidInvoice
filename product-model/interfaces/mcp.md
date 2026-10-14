---
type: agent
actors:
- ai-agent
references:
- kind: code
  role: implementation
  target: src/McpBundle/Security/McpOAuthAuthenticator.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/McpScopeGuard.php
- kind: doc
  role: context
  target: docs/docs/ai/mcp-server.mdx
- kind: doc
  role: context
  target: src/McpBundle/README.md
---

# MCP server

The Model Context Protocol server at `/_mcp` through which a connected AI agent reads one company's billing and, when the User granted write access, creates and changes it on the User's behalf.
