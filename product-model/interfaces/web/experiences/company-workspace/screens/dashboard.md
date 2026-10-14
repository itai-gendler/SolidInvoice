---
entities:
- entity: invoice
  shows:
  - Balance
  - Total
  - Due date
- entity: payment
  shows:
  - Amount
- entity: client
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: src/DashboardBundle/Action/Index.php
- kind: code
  role: implementation
  target: src/DashboardBundle/Widgets/HeroStatsWidget.php
---

# Dashboard

The company at a glance: amounts outstanding and overdue, revenue, invoices by status, items needing attention and recent activity.
