---
domain: invoices
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
  target: src/InvoiceBundle/Action/View.php
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
  target: src/InvoiceBundle/Mcp/InvoiceReadTools.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/Tool/ResourceQueryTools.php
---

# View an invoice

Read an invoice as it is presented to the client, with its PDF.
