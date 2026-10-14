---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses Send on a pending invoice
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: The Product emails the invoice again to the contacts chosen on it
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Total, Due date]}
  - {entity: contact, effect: reads, facts: [Email]}
  - {entity: company, effect: reads, facts: [Invoice email subject, Invoice BCC address]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# Send an issued invoice again

## Trigger

The client missed the email or asks for a copy.

## Outcome

The contacts have the invoice again; its status and its reminders are unchanged.

## Edge cases

- Overdue and paid invoices can be sent again the same way.
