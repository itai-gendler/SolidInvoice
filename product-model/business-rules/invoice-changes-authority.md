---
appliesTo:
- type: entity
  id: invoice
  effect: changes
  facts:
  - Invoice number
  - Invoice date
  - Payment terms
  - Due date
  - Line items
  - Discount
  - Withholding and adjustments
  - Terms
  - Notes
  - Custom field values
  - Listed in Archived
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
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Doctrine/Filter/CompanyFilter.php
- kind: code
  role: implementation
  target: config/packages/security.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Twig/Components/CreateInvoice.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Repository/InvoiceRepository.php
---

# Only users of the owning company edit an invoice

Every User who belongs to the company that keeps it may; nobody outside that company can see or reach it. There are no roles inside a company.
