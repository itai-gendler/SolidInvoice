---
entities:
- entity: invoice
  shows:
  - Invoice number
  - Balance
  - Currency
- entity: payment
  collects:
  - Amount
  - Reference
  - Notes
- entity: payment-method
  shows:
  - Name
- entity: client
  shows:
  - Credit balance
references:
- kind: code
  role: implementation
  target: src/PaymentBundle/Action/Prepare.php
- kind: code
  role: implementation
  target: src/PaymentBundle/Form/Type/PaymentType.php
---

# Invoice payment

Recording a payment against one invoice: the method, the amount, and for the company's own records a reference and notes.
