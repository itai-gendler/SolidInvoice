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
- entity: payment-method
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: src/PaymentBundle/Action/Prepare.php
---

# Invoice payment

Paying one invoice from its link: choosing an online payment method and the amount.
