---
domain: quotes
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Action/Transition.php
- kind: code
  role: implementation
  target: config/packages/workflow.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Resources/views/Default/view.html.twig
- kind: code
  role: implementation
  target: src/QuoteBundle/DataGrid/QuoteGrid.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Repository/QuoteRepository.php
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
  target: src/QuoteBundle/Mcp/QuoteWriteTools.php
---

# Archive a quote

Put a quote away so it no longer appears among the active quotes.
