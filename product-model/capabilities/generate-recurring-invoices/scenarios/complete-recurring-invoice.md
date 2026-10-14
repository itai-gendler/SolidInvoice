---
kind: alternative
routes:
  web: Web
steps:
- text: The hourly run finds an active recurring invoice whose end date, or the date its occurrences run out, is today or past
  kind: condition
  unattended: true
  entities:
  - {entity: recurring-invoice, effect: reads, facts: [End recurrence, End date, End after occurrences]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
- text: The Product marks the recurring invoice complete
  kind: product
  entities:
  - {entity: recurring-invoice, effect: changes, from: Active, to: Complete, facts: []}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
---

# Complete a recurring invoice at its end

## Trigger

A schedule reaches its end condition.

## Outcome

The recurring invoice is Complete and listed under Completed; it generates no more invoices.
