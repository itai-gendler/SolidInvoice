---
appliesTo:
- type: entity
  id: data-export
  effect: creates
permits:
- related:
  - {verb: requests, entity: user}
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Export/Action/RequestExport.php
---

# Only users of a company request an export of its data

Every User who belongs to the company that keeps it may; nobody outside that company can see or reach it. There are no roles inside a company.
