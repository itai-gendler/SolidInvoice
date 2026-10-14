---
kind: edge
routes:
  web: Web
steps:
- text: The hourly check finds an invoice at a reminder stage
  kind: condition
  unattended: true
  entities:
  - {entity: invoice, effect: reads, facts: [Due date]}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
- text: Automatic reminders are off for the company
  kind: condition
  entities:
  - {entity: company, effect: reads, facts: [Automatic reminders]}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
---

# Send no reminders while they are switched off

## Trigger

The company has switched automatic reminders off.

## Outcome

No reminder is sent and none is recorded as sent.

## Edge cases

- With automatic reminders on and pre-due reminders off, only the overdue reminders are sent.
- No reminder is sent for an invoice with no contacts chosen.
- On the hosted service, reminders are sent only on plans that include them.
