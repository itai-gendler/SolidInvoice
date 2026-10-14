---
domain: quotes
availability:
- {place: 'web::company-workspace'}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Action/CloneQuote.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Cloner/QuoteCloner.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/McpScopeGuard.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Mcp/QuoteWriteTools.php
---

# Clone a quote

Start a new draft quote from an existing one.
