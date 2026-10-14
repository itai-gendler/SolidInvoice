---
domain: settings
availability:
- {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/SettingsBundle/Action/Index.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Config/ConfigProvider.php
- kind: doc
  role: intent
  target: docs/docs/invoices/overdue-invoices.md
---

# Change invoice settings

Set how the company's invoices are numbered, emailed and reminded, and their default payment terms.
