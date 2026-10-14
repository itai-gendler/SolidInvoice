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
- kind: code
  role: implementation
  target: src/PaymentBundle/Twig/Components/PaymentMarketplace.php
---

# Add a payment method

Set up a gateway or offline method for paying invoices.
