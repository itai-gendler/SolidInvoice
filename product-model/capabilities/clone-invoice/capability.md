---
domain: invoices
availability:
- {place: 'web::company-workspace'}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Action/CloneInvoice.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Cloner/InvoiceCloner.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/McpScopeGuard.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/InvoiceWriteTools.php
---

# Clone an invoice

Start a new draft invoice from an existing one.
