---
domain: invoices
availability:
- {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Action/Transition/Send.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Email/InvoiceEmail.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Listener/Mailer/InvoiceReceiverListener.php
- kind: doc
  role: intent
  target: docs/docs/invoices/sending-invoices.md
---

# Send an invoice

Email an invoice to the contacts chosen on it, issuing it first if it is a draft.
