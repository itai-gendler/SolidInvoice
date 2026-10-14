---
domain: invoices
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/DataGrid/BaseInvoiceGrid.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Repository/InvoiceRepository.php
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Entity/Invoice.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/InvoiceTransitionProcessor.php
---

# Delete an invoice

Remove invoices permanently.
