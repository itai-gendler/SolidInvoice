---
appliesTo:
- type: entity
  id: recurring-invoice
  effect: changes
  from: Draft
  to: Active
permits:
- related:
  - &id001 {verb: keeps, entity: company}
  - &id002 {verb: belongs-to, entity: user}
- related:
  - *id001
  - *id002
  - {verb: connects, entity: ai-agent}
  when:
  - entity: ai-agent
    fact: Write access
    is: 'Yes'
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Doctrine/Filter/CompanyFilter.php
- kind: code
  role: implementation
  target: config/packages/security.php
- kind: code
  role: implementation
  target: config/packages/workflow.php
---

# On a self-hosted install, any user of the owning company activates a recurring invoice

Activating a draft recurring invoice needs nothing beyond belonging to the company.
