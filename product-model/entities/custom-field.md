---
domain: settings
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Entity/CustomField/CustomField.php
- kind: doc
  role: context
  target: docs/docs/managing-clients/custom-fields.md
---

# Custom field

An extra field a company adds to its clients, contacts, invoices or quotes.

## Information kept

- **Applies to** — Client, Contact, Invoice or Quote
- **Label** — the name shown beside the field and on PDFs; at most 125 characters
- **Type** — Text, Long text, Number, Date, Email, URL, Checkbox, Single-select or Multi-select
- **Options** — the choices of a single- or multi-select field
- **Required** — whether a value must be given
- **Visibility** — for invoice and quote fields, Internal or Client-visible
- **Default value** — the value new records start with
- **Position** — its place in forms and on PDFs
