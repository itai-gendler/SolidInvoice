---
appliesTo:
- type: entity
  id: api-token
  effect: reads
  facts:
  - Request history
permits:
- related:
  - {verb: owns, entity: user}
references:
- kind: code
  role: implementation
  target: src/UserBundle/Twig/Components/ApiTokenHistoryModal.php
---

# Only its owner reads an API token's request history

The history of a token is shown only to the User who owns it.
