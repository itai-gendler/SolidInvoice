---
kind: primary
routes:
  web: Web
steps:
- text: The User enters a name and optional description and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::api-tokens'}
- text: The Product creates the token for the User in the current company and shows its value once
  kind: product
  actor: user
  entities:
  - {entity: api-token, effect: creates, facts: [Name, Description, Token]}
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::api-tokens'}
---

# Create an API token

## Trigger

The User connects an integration.

## Outcome

The token authenticates API requests as the User in this company; its value cannot be shown again.
