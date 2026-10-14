---
appliesTo:
- type: entity
  id: invoice
  effect: changes
  facts:
  - Balance
permits:
- related:
  - {verb: keeps, entity: company}
  - {verb: belongs-to, entity: user}
- actors:
  - contact
references:
- kind: code
  role: implementation
  target: src/PaymentBundle/Listener/PaymentCompleteListener.php
---

# An invoice's balance changes only through payments made by users of its company or by a contact paying from the link

Recording a payment, or a contact's captured online payment, lowers the balance.
