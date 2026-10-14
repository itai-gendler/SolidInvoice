---
references:
- kind: code
  role: implementation
  target: src/PaymentBundle/Menu/PaymentMenu.php
---

# Payment methods

The gateways and offline methods through which invoices are paid.

## Boundary

Owns setting payment methods up and removing them. It does not own the payments made through them.
