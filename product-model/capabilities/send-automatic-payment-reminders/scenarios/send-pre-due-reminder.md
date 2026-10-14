---
kind: primary
routes:
  web: Web
steps:
- text: The hourly check finds a pending invoice due in exactly the company's pre-due reminder days
  kind: condition
  unattended: true
  entities:
  - {entity: invoice, effect: reads, facts: [Due date]}
  - {entity: company, effect: reads, facts: [Pre-due reminder days]}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
- text: Automatic and pre-due reminders are on for the company and this reminder has not been sent for the invoice
  kind: condition
  entities:
  - {entity: company, effect: reads, facts: [Automatic reminders, Pre-due reminders]}
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
- text: The Product emails a friendly reminder to the contacts chosen on the invoice
  kind: product
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Due date, Balance]}
  - {entity: contact, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: The Product notifies the company's users who follow reminder alerts
  kind: product
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  - {entity: company, effect: reads, facts: []}
  - {entity: user, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# Send a reminder before the due date

## Trigger

An invoice is coming due.

## Outcome

The contacts have a pre-due reminder; it will not be sent again for this invoice.
