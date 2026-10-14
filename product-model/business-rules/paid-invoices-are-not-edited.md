---
appliesTo:
- type: capability
  id: edit-invoice
  contexts:
  - {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Action/Edit.php
---

# A paid invoice is never edited

The editor refuses a paid invoice.
