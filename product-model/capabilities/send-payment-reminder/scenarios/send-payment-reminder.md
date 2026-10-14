---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Send Reminder on a pending or overdue invoice and confirms the recipients
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  - {entity: contact, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: The Product emails a reminder to the contacts chosen on the invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Balance, Due date]}
  - {entity: contact, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# Send a reminder for an unpaid invoice

## Trigger

The client has not paid.

## Outcome

The contacts have a reminder; the automatic reminder schedule is unaffected.

## Edge cases

- The ability is offered only while the invoice has at least one contact chosen.
