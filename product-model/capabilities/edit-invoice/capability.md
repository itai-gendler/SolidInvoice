---
domain: invoices
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
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
- kind: code
  role: implementation
  target: src/InvoiceBundle/Action/Edit.php
- kind: doc
  role: intent
  target: docs/docs/invoices/managing-invoices.md
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

# Edit an invoice

Change an invoice that is not paid.
