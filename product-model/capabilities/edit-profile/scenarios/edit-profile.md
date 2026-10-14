---
kind: primary
routes:
  web: Web
steps:
- text: The User changes their name, email or mobile, confirms with their current password and saves
  kind: actor
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Name, Email, Mobile]}
  contexts:
    web: {place: 'web::company-workspace::profile'}
- text: The Product saves the profile
  kind: product
  actor: user
  entities:
  - {entity: user, effect: changes, facts: [Name, Email, Mobile]}
  contexts:
    web: {place: 'web::company-workspace::profile'}
---

# Edit one's profile

## Trigger

The User's details change.

## Outcome

The profile shows the new details; a new email must be verified again.
