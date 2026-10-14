---
domain: quotes
availability:
- {place: 'web::shared-documents'}
- {place: 'web::company-workspace'}
- {place: rest-api}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Action/ViewBilling.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Action/View.php
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Entity/Quote.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/QuoteTransitionProcessor.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/McpScopeGuard.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Mcp/QuoteReadTools.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/Tool/ResourceQueryTools.php
---

# View a quote

Read a quote as it is presented to the client, with its PDF.
