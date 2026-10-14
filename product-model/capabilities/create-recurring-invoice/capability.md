---
domain: recurring-invoices
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Action/CreateRecurring.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Twig/Components/CreateRecurringInvoice.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Form/Type/RecurringInvoiceType.php
- kind: doc
  role: intent
  target: docs/docs/recurring-invoices/creating-a-recurring-invoice.md
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Entity/RecurringInvoice.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/RecurringInvoiceTransitionProcessor.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/RecurringInvoiceLinePersistProcessor.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/McpScopeGuard.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/RecurringInvoiceWriteTools.php
---

# Create a recurring invoice

Set up a template that generates invoices for a client on a schedule, saved as a draft or enabled straight away.
