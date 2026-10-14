---
appliesTo:
- type: entity
  id: invoice
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
  target: src/InvoiceBundle/Resources/views/external_invoice_view.html.twig
- kind: doc
  role: intent
  target: docs/docs/invoices/creating-an-invoice.md
---

# Only users of the owning company read an invoice's notes

Notes are for the company's own records: they appear in the company workspace and never on the page, PDF or email a contact receives.
