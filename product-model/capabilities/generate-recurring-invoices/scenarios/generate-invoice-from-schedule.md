---
kind: primary
routes:
  web: Web
steps:
- text: The hourly run finds an active recurring invoice whose schedule matches today and that has no invoice dated today
  kind: condition
  unattended: true
  entities:
  - {entity: recurring-invoice, effect: reads, facts: [Start date, Recurring type, Repeat days]}
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
- text: The Product creates an invoice dated today for the client and recipients, copying the line items with today's day, weekday, month and year filled in, the discount, taxes with their rates fixed, terms and notes, and the due date its due terms give
  kind: product
  entities:
  - {entity: invoice, effect: creates, to: Pending, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes, Total, Tax total, Balance, Currency]}
  - {entity: recurring-invoice, effect: reads, facts: [Line items, Discount, Withholding and adjustments, Terms, Notes, Payment terms]}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
---

# Generate today's invoice from a recurring invoice

## Trigger

A matching date arrives for an active recurring invoice.

## Outcome

A new Pending invoice is listed under the recurring invoice's generated invoices.

## Edge cases

- However often the scheduler runs, a recurring invoice generates at most one invoice per day.
- A monthly day that does not exist in a month, such as the 31st, generates nothing that month.
- Nothing is generated unless the scheduler runs.
