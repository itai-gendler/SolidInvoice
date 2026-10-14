---
appliesTo:
- type: capability
  id: delete-payment-method
  contexts:
  - {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/PaymentBundle/Twig/Components/PaymentSettings.php
---

# A payment method that payments were made with is never deleted

Deleting it is refused while any payment is associated with it.
