---
appliesTo:
- type: entity
  id: quote
  effect: reads
  facts:
  - Notes
permits:
- related:
  - {verb: keeps, entity: company}
  - {verb: belongs-to, entity: user}
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Action/ViewBilling.php
---

# Only users of the owning company read a quote's notes

Notes are for the company's own records: they appear in the company workspace and never on the page, PDF or email a contact receives.
