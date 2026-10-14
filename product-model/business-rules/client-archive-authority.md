---
appliesTo:
- type: entity
  id: client
  effect: changes
  to: Archived
permits:
- related:
  - {verb: keeps, entity: company}
  - {verb: belongs-to, entity: user}
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Doctrine/Filter/CompanyFilter.php
- kind: code
  role: implementation
  target: config/packages/security.php
- kind: code
  role: implementation
  target: src/ClientBundle/Repository/ClientRepository.php
---

# Only users of the owning company archive a client

Every User who belongs to the company that keeps it may; nobody outside that company can see or reach it. There are no roles inside a company.
