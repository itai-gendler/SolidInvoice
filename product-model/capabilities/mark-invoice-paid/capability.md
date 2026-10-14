---
domain: invoices
availability:
- {place: rest-api}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/InvoiceTransitionProcessor.php
- kind: code
  role: implementation
  target: config/packages/workflow.php
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/McpScopeGuard.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/InvoiceWriteTools.php
---

# Mark an invoice paid

Mark a pending or overdue invoice paid without recording a payment, through the REST API or an AI agent.
