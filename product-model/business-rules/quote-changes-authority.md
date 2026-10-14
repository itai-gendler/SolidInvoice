---
appliesTo:
- type: entity
  id: quote
  effect: changes
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
  target: src/QuoteBundle/Repository/QuoteRepository.php
---

# Only users of the owning company change quotes

Every User who belongs to the company that keeps it may; nobody outside that company can see or reach it. There are no roles inside a company. A connected AI agent may too when the User gave it write access.
