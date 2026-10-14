---
appliesTo:
- type: entity
  id: api-token
  effect: creates
permits:
- related:
  - {verb: owns, entity: user}
references:
- kind: code
  role: implementation
  target: src/ApiBundle/Security/Voter/ApiAccessVoter.php
---

# On a self-hosted install, any user creates API tokens

Every User may create API tokens for the companies they belong to and use the REST API with them.
