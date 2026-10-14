---
appliesTo:
- type: capability
  id: publish-invoice
- type: capability
  id: send-invoice
- type: capability
  id: create-invoice
- type: capability
  id: publish-quote
- type: capability
  id: send-quote
- type: capability
  id: create-quote
- type: capability
  id: edit-tax-rate
- type: capability
  id: generate-recurring-invoices
- type: capability
  id: accept-quote
references:
- kind: code
  role: implementation
  target: src/TaxBundle/Listener/SnapshotTaxesOnIssueListener.php
- kind: code
  role: implementation
  target: src/TaxBundle/Entity/LineTax.php
- kind: code
  role: implementation
  target: src/TaxBundle/Service/TaxSnapshotCopier.php
- kind: code
  role: implementation
  target: src/TaxBundle/Form/Type/LineTaxType.php
- kind: doc
  role: intent
  target: docs/docs/taxes/applying-tax-to-invoices.md
---

# An issued invoice or quote keeps the tax rates it was issued with

Each line tax and each withholding or adjustment copies the tax rate's name, rate, category and type onto the document when it is chosen. When the document leaves draft, those copies are fixed: a later change to the tax rate never changes the document. Invoices generated from a recurring invoice and invoices made from an accepted quote get their own copies.

## Rationale

An issued document is a record the client has received; restating its tax later would make it disagree with what was sent.
