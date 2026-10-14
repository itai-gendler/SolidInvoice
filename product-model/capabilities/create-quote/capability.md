---
domain: quotes
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Twig/Components/CreateQuote.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Manager/QuoteFormManager.php
- kind: code
  role: implementation
  target: config/packages/workflow.php
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
  target: src/ApiBundle/State/Processor/QuoteLinePersistProcessor.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/McpScopeGuard.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Mcp/QuoteWriteTools.php
---

# Create a quote

Prepare a new quote for a client, saved as a draft or issued straight away.
