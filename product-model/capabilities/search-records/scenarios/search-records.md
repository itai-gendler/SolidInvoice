---
kind: primary
routes:
  web: Web
steps:
- text: 'The User types words, optionally with qualifiers such as in:, status:, client:, amount:, created: or sort:'
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace'}
- text: The Product shows matching clients, contacts, quotes, invoices, recurring invoices and payments of the current company, grouped by kind
  kind: product
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Name]}
  - {entity: contact, effect: reads, facts: [Email]}
  - {entity: quote, effect: reads, facts: [Quote number]}
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  - {entity: recurring-invoice, effect: reads, facts: [Recurring type]}
  - {entity: payment, effect: reads, facts: [Reference]}
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace'}
---

# Search the company's records

## Trigger

The User looks for a record.

## Outcome

The User can open any match; records of other companies never appear.
