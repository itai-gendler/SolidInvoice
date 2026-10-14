---
appliesTo:
- type: entity
  id: invoice
  effect: changes
  to: Overdue
permits:
- unattended: true
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
  target: src/InvoiceBundle/Command/MarkOverdueInvoicesCommand.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Message/Handler/MarkInvoiceOverdueHandler.php
---

# An invoice becomes overdue through the hourly check or when users of its company mark it

The hourly check moves pending invoices past their due date to overdue; Users of the company, through the REST API, and connected agents with write access may mark one overdue earlier.
