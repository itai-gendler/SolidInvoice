---
appliesTo:
- type: entity
  id: recurring-invoice
  effect: changes
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
  target: src/InvoiceBundle/Command/SendRecurringInvoicesCommand.php
---

# Only users of the owning company, and its schedule, change a recurring invoice

Every User who belongs to the company that keeps it may; nobody outside that company can see or reach it. There are no roles inside a company. The Product's own hourly run completes recurring invoices that reach their end.
