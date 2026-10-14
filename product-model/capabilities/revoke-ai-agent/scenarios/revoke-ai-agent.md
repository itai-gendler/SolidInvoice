---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Revoke on a connected app
  kind: actor
  actor: user
  entities:
  - {entity: ai-agent, effect: reads, facts: [Name, Write access]}
  contexts:
    web: {place: 'web::company-workspace::connected-apps'}
- text: The Product revokes the agent's access
  kind: product
  actor: user
  entities:
  - {entity: ai-agent, effect: changes, from: Connected, to: Revoked, facts: []}
  contexts:
    web: {place: 'web::company-workspace::connected-apps'}
---

# Revoke a connected app

## Trigger

The User stops using an agent.

## Outcome

The agent's requests are refused from now on.
