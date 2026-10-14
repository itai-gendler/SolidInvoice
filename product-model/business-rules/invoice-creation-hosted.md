---
appliesTo:
- type: entity
  id: invoice
  effect: creates
permits:
- related:
  - &id001 {verb: keeps, entity: company}
  - &id002 {verb: belongs-to, entity: user}
  when:
  - entity: company
    fact: Invoices created this month
    under: {entity: company, fact: Monthly invoice limit}
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
  target: src/InvoiceBundle/Validator/Constraints/WithinPlanInvoiceLimitValidator.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Action/Create.php
- kind: code
  role: implementation
  target: src/SaasBundle/Feature/Feature.php
---

# On the hosted service, users of the owning company create invoices within their plan's monthly limit

A User of the company may create an invoice while the company has created fewer invoices this calendar month than its plan allows.
