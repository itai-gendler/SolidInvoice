---
domain: payment-methods
availability:
- {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/PaymentBundle/Twig/Components/PaymentSettings.php
- kind: code
  role: implementation
  target: src/PaymentBundle/Form/Type/PaymentMethodType.php
---

# Delete a payment method

Remove a payment method nobody has paid with.
