---
domain: recurring-invoices
availability:
- {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/GenerateInvoiceFromRecurringProcessor.php
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
---

# Generate an invoice now

Issue the next invoice from a recurring invoice on demand, without waiting for its schedule.
