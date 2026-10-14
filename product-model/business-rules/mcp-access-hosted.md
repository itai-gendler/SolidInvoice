---
appliesTo:
- type: entity
  id: ai-agent
  effect: creates
permits:
- related:
  - {verb: connects, entity: user}
  when:
  - entity: company
    fact: Plan includes MCP
    is: 'Yes'
references:
- kind: code
  role: implementation
  target: src/SaasBundle/Security/Voter/SubscriptionVoter.php
---

# On the hosted service, users connect AI agents only on a plan that includes MCP

Connecting an agent, and every call it makes, is refused while the company is on a trial or a plan without MCP access.
