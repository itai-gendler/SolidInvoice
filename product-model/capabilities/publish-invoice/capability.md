---
domain: invoices
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Action/Transition.php
- kind: code
  role: implementation
  target: config/packages/workflow.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Resources/views/Default/view.html.twig
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Entity/Invoice.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/InvoiceTransitionProcessor.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/McpScopeGuard.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/InvoiceWriteTools.php
---

# Publish an invoice

Issue a draft invoice without emailing it.
