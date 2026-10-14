---
entities:
- entity: company
  collects:
  - Name
  - Currency
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Action/CreateCompany.php
---

# Company form

Creating another company.
