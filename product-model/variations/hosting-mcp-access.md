---
kind: configuration
of: business-rule
takesEffect: Fixed by how SolidInvoice is deployed. On the hosted service the plan is checked when an agent is connected and on every call.
stability: An install does not move between the two. A hosted company that loses MCP from its plan keeps its connected agents, but their calls are refused until the plan includes it again.
alternatives:
- id: mcp-access-self-hosted
  selectedWhen: Selected when the install runs as the self-hosted product, the default for every download, package, container and binary.
- id: mcp-access-hosted
  selectedWhen: Selected when the install runs as the hosted SolidInvoice service.
references:
- kind: code
  role: implementation
  target: src/McpBundle/Security/Voter/McpAccessVoter.php
- kind: code
  role: implementation
  target: src/SaasBundle/Security/Voter/SubscriptionVoter.php
---

# MCP access by hosting

Self-hosted installs let every User connect AI agents; the hosted service includes it in some plans only.
