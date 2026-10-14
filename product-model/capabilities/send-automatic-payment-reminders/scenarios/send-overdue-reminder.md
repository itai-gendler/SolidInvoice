---
kind: alternative
routes:
  web: Web
steps:
- text: The hourly check finds a pending or overdue invoice whose due date was 1, 7 or 14 days ago
  kind: condition
  unattended: true
  entities:
  - {entity: invoice, effect: reads, facts: [Due date]}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
- text: Automatic reminders are on for the company and the reminder for this stage has not been sent for the invoice
  kind: condition
  entities:
  - {entity: company, effect: reads, facts: [Automatic reminders]}
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
- text: The Product emails the stage's reminder, polite at 1 day, firm at 7 days and urgent at 14 days, to the contacts chosen on the invoice
  kind: product
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Due date, Balance]}
  - {entity: contact, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: After the 14-day reminder, the Product tells the company's users that automatic reminders have stopped and follow-up is up to them
  kind: product
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Due date]}
  - {entity: company, effect: reads, facts: []}
  - {entity: user, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# Send an overdue reminder

## Trigger

An invoice stays unpaid after its due date.

## Outcome

The contacts have the reminder for the stage; after the third, reminders stop and the company is told.
