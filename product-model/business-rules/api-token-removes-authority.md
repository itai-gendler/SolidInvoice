---
appliesTo:
- type: entity
  id: api-token
  effect: removes
permits:
- related:
  - {verb: owns, entity: user}
references:
- kind: code
  role: implementation
  target: src/UserBundle/Twig/Components/ApiTokens.php
- kind: code
  role: implementation
  target: src/UserBundle/Entity/ApiToken.php
---

# Only its owner revokes an API token

An API token belongs to the User who created it.
