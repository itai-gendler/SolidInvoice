---
appliesTo:
- type: entity
  id: payment
  effect: changes
permits:
- related:
  - {verb: receives, entity: invoice}
  - {verb: keeps, entity: company}
  - {verb: belongs-to, entity: user}
- actors:
  - contact
references:
- kind: code
  role: implementation
  target: src/PaymentBundle/Action/Done.php
---

# A payment's outcome is recorded for the user or contact who started it

The gateway's result, captured or failed, is stored on the payment when the person who started it returns from the gateway.
