---
appliesTo:
- type: entity
  id: ai-agent
  effect: changes
  to: Revoked
permits:
- related:
  - {verb: connects, entity: user}
references:
- kind: code
  role: implementation
  target: src/McpBundle/Action/ConnectedAppsRevoke.php
---

# Only the User who connected an AI agent revokes it

Connected apps are listed and revoked by the User who approved them.
