---
appliesTo:
- type: entity
  id: ai-agent
  effect: creates
permits:
- related:
  - {verb: connects, entity: user}
references:
- kind: code
  role: implementation
  target: src/McpBundle/Security/Voter/McpAccessVoter.php
---

# On a self-hosted install, any user connects AI agents

Every User may connect AI agents to the companies they belong to.
