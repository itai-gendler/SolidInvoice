---
appliesTo:
- type: entity
  id: api-token
  effect: creates
permits:
- related:
  - {verb: owns, entity: user}
  when:
  - entity: company
    fact: Plan includes REST API
    is: 'Yes'
references:
- kind: code
  role: implementation
  target: src/SaasBundle/Security/Voter/SubscriptionVoter.php
- kind: code
  role: implementation
  target: src/UserBundle/Twig/Components/CreateApiToken.php
---

# On the hosted service, users create API tokens only on a plan that includes the REST API

Creating a token, and every request made with one, is refused while the company is on a trial or a plan without the REST API.
