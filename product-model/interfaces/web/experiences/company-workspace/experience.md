---
actors:
- user
access: authenticated
references:
- kind: code
  role: implementation
  target: config/packages/security.php
- kind: code
  role: implementation
  target: src/CoreBundle/Action/SelectCompany.php
---

# Company workspace

Where a signed-in User works inside the company they have selected: clients, quotes, invoices, recurring invoices, payments, tax rates, payment methods and settings, all scoped to that one company.
