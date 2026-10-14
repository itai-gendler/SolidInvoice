---
appliesTo:
- type: entity
  id: client
  effect: changes
  facts:
  - Credit balance
permits:
- related:
  - {verb: keeps, entity: company}
  - {verb: belongs-to, entity: user}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Action/Ajax/Credit.php
- kind: code
  role: implementation
  target: src/PaymentBundle/Listener/PaymentCompleteListener.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Listener/InvoicePaidListener.php
---

# Only users of the owning company adjust or spend a client's credit

Every User who belongs to the company that keeps it may; nobody outside that company can see or reach it. There are no roles inside a company. Credit is spent by paying an invoice with the Credit method, which only Users may choose.
