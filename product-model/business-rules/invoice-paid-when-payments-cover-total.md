---
appliesTo:
- type: capability
  id: pay-invoice
  contexts:
  - {place: 'web::company-workspace'}
  - {place: 'web::shared-documents'}
references:
- kind: code
  role: implementation
  target: src/PaymentBundle/Listener/PaymentCompleteListener.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Repository/InvoiceRepository.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Listener/InvoicePaidListener.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Listener/WorkFlowSubscriber.php
---

# An invoice is paid once its captured payments cover its total

Each captured payment lowers the balance. When captured payments reach the total, the invoice becomes Paid with that day as its paid date; anything paid beyond the total is added to the client's credit balance.
