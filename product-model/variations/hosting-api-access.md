---
kind: configuration
of: business-rule
takesEffect: Fixed by how SolidInvoice is deployed. On the hosted service the plan is checked when a token is created and on every request.
stability: An install does not move between the two. A hosted company that loses the REST API from its plan keeps its tokens, but their requests are refused until the plan includes it again.
alternatives:
- id: api-access-self-hosted
  selectedWhen: Selected when the install runs as the self-hosted product, the default for every download, package, container and binary.
- id: api-access-hosted
  selectedWhen: Selected when the install runs as the hosted SolidInvoice service.
references:
- kind: code
  role: implementation
  target: src/ApiBundle/Security/Voter/ApiAccessVoter.php
- kind: code
  role: implementation
  target: src/SaasBundle/Security/Voter/SubscriptionVoter.php
---

# REST API access by hosting

Self-hosted installs give every User the REST API; the hosted service includes it in some plans only.
