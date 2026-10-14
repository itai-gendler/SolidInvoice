---
type: web
actors:
- user
- contact
- visitor
references:
- kind: code
  role: implementation
  target: config/routes.php
- kind: code
  role: implementation
  target: config/packages/security.php
---

# Web

The browser application. Visitors sign in or register; people who belong to a company run its billing; a client's contacts open the quotes and invoices emailed to them, and pay invoices, without signing in.
