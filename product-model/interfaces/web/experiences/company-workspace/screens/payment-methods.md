---
entities:
- entity: payment-method
  shows:
  - Name
  - Gateway
  - Enabled
  - Internal
  collects:
  - Name
  - Enabled
  - Internal
  - Gateway settings
references:
- kind: code
  role: implementation
  target: src/PaymentBundle/Action/Settings.php
- kind: code
  role: implementation
  target: src/PaymentBundle/Twig/Components/PaymentSettings.php
- kind: code
  role: implementation
  target: src/PaymentBundle/Twig/Components/PaymentMarketplace.php
---

# Payment methods

The payment gateways and offline methods the company has set up, and the ones it can add.
