---
appliesTo:
- type: entity
  id: invoice
  effect: creates
permits:
- related:
  - &id001 {verb: keeps, entity: company}
  - &id002 {verb: belongs-to, entity: user}
- related:
  - *id001
  - *id002
  - {verb: connects, entity: ai-agent}
  when:
  - entity: ai-agent
    fact: Write access
    is: 'Yes'
- unattended: true
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Doctrine/Filter/CompanyFilter.php
- kind: code
  role: implementation
  target: config/packages/security.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Validator/Constraints/WithinPlanInvoiceLimitValidator.php
---

# On a self-hosted install, users of the owning company create invoices without a monthly limit

Any User of the company may create invoices, from the editor, by cloning or by accepting a quote, as often as they like; the company's own schedule creates invoices from its recurring invoices.
