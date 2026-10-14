---
appliesTo:
- type: entity
  id: tax-identifier
  effect: removes
permits:
- related:
  - {verb: holds, entity: client}
  - {verb: keeps, entity: company}
  - {verb: belongs-to, entity: user}
- related:
  - {verb: holds, entity: company}
  - {verb: belongs-to, entity: user}
- related:
  - {verb: holds, entity: client}
  - {verb: keeps, entity: company}
  - {verb: belongs-to, entity: user}
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
  target: src/TaxBundle/Entity/TaxIdentifier.php
---

# Only users of the company concerned delete tax identifiers

A client's tax identifiers are changed by the Users of the company that keeps the client, and the company's own by its Users. A connected AI agent with write access may add and remove a client's.
