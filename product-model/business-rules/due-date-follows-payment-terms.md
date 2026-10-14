---
appliesTo:
- type: capability
  id: create-invoice
- type: capability
  id: edit-invoice
- type: capability
  id: generate-recurring-invoices
- type: capability
  id: accept-quote
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Enum/PaymentTerms.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Entity/Invoice.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Manager/InvoiceManager.php
- kind: doc
  role: intent
  target: docs/docs/invoices/payment-terms.md
---

# An invoice's due date follows its payment terms, counted from the invoice date

Due on receipt is the invoice date; Net N is N days after it; End of month and End of next month are the last day of the invoice's month or the next. Under Custom terms the due date is whatever is entered, or none. A new invoice starts with the client's payment terms, or the company default; an invoice from an accepted quote takes the same, and a generated invoice takes its recurring invoice's terms, counted from the day it is generated.
