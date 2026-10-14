---
references:
- kind: code
  role: implementation
  target: src/SettingsBundle/Action/CustomField/IndexAction.php
---

# Custom fields

Extra fields a company adds to its clients, contacts, invoices and quotes.

## Boundary

Owns the field definitions. It does not own the values, which are kept with each record.
