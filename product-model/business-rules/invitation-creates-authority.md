---
appliesTo:
- type: entity
  id: invitation
  effect: creates
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
  target: src/UserBundle/Action/InviteUser.php
---

# Only users of a company invite people to it

Every User who belongs to the company that keeps it may; nobody outside that company can see or reach it. There are no roles inside a company.
