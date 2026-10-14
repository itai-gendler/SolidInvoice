---
appliesTo:
- type: entity
  id: company
  effect: changes
permits:
- related:
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
  target: src/SettingsBundle/Action/Index.php
---

# Only users of a company change its invoice and quote settings

Every User who belongs to the company may; nobody outside it can see or reach its settings. There are no roles inside a company.
