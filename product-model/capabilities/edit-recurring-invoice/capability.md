---
domain: recurring-invoices
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Action/EditRecurring.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Form/Type/RecurringInvoiceType.php
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Entity/RecurringInvoice.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/RecurringInvoiceTransitionProcessor.php
---

# Edit a recurring invoice

Change a recurring invoice's template or schedule.
