---
domain: clients
availability:
- {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Action/Ajax/Credit.php
- kind: code
  role: implementation
  target: src/ClientBundle/Twig/Components/ClientCredit.php
- kind: code
  role: implementation
  target: src/ClientBundle/Repository/CreditRepository.php
- kind: doc
  role: intent
  target: docs/docs/managing-clients/client-credit.md
---

# Add client credit

Add to or take from the prepaid credit a client holds.
