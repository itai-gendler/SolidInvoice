---
appliesTo:
- type: capability
  id: connect-ai-agent
- type: context
  context: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/McpSecurityContext.php
- kind: doc
  role: intent
  target: docs/docs/ai/mcp-server.mdx
---

# A connected AI agent works in exactly one company

The company is chosen when the User approves the agent and never changes; the agent reads only that company's data, and changes it only with write access.
