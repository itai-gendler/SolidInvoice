---
kind: primary
routes:
  web: Web
steps:
- text: The hourly check finds a pending invoice whose due date has passed
  kind: condition
  unattended: true
  entities:
  - {entity: invoice, effect: reads, facts: [Due date]}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
- text: The Product marks the invoice overdue
  kind: product
  entities:
  - {entity: invoice, effect: changes, from: Pending, to: Overdue, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: The Product notifies the company's users who follow invoice alerts
  kind: product
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Due date, Balance]}
  - {entity: company, effect: reads, facts: []}
  - {entity: user, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# Mark a pending invoice overdue

## Trigger

An invoice's due date passes without full payment.

## Outcome

The invoice is Overdue and subscribed users have been told.

## Edge cases

- Invoices without a due date are never marked overdue.
- The check runs only while the scheduler runs.
