---
domain: invoices
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Twig/Components/CreateInvoice.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Manager/InvoiceFormManager.php
- kind: code
  role: implementation
  target: config/packages/workflow.php
- kind: doc
  role: intent
  target: docs/docs/invoices/creating-an-invoice.md
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
  target: src/ApiBundle/State/Processor/InvoiceLinePersistProcessor.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/McpScopeGuard.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/InvoiceWriteTools.php
---

# Create an invoice

Prepare a new invoice for a client, saved as a draft or issued straight away.
