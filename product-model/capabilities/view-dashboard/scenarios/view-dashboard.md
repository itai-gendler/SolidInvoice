---
kind: primary
routes:
  web: Web
steps:
- text: The User opens the dashboard
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::dashboard'}
- text: The Product shows outstanding and overdue totals per currency, revenue from captured payments, invoices by status, invoices needing attention and recent activity
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Balance, Total, Due date]}
  - {entity: payment, effect: reads, facts: [Amount]}
  contexts:
    web: {place: 'web::company-workspace::dashboard'}
---

# Open the dashboard

## Trigger

The User wants an overview.

## Outcome

The User sees the company's billing at a glance, in each currency separately.
