---
kind: primary
routes:
  web: Web
steps:
- text: The User, sent by the agent to the consent page, picks the company and whether to allow write access, and approves
  kind: actor
  actor: user
  entities:
  - {entity: company, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::connected-apps'}
- text: The Product connects the agent to that company with the access chosen
  kind: product
  actor: user
  entities:
  - {entity: ai-agent, effect: creates, to: Connected, facts: [Name, Write access]}
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::connected-apps'}
---

# Approve an AI agent

## Trigger

The User adds SolidInvoice to an AI agent.

## Outcome

The agent can work in that company only, reading always and changing things only with write access.

## Edge cases

- A User who chose to be remembered is not asked again for the same agent, company and access.
