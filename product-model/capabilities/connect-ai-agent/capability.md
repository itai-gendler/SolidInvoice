---
domain: profile
availability:
- {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/McpBundle/Action/Authorize.php
- kind: code
  role: implementation
  target: src/McpBundle/OAuth/ConsentService.php
- kind: doc
  role: intent
  target: docs/docs/ai/mcp-server.mdx
---

# Connect an AI agent

Approve an AI agent's access to one company, with read access and optionally write access.
