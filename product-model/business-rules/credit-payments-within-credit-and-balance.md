---
appliesTo:
- type: capability
  id: pay-invoice
  contexts:
  - {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/PaymentBundle/Action/Prepare.php
- kind: doc
  role: intent
  target: docs/docs/managing-clients/client-credit.md
---

# A credit payment never exceeds the client's credit or the invoice balance

Paying with client credit is refused when the amount is more than the client's credit balance or more than the invoice still owes.
