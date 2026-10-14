---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a contact of a client that has other contacts
  kind: actor
  actor: user
  entities:
  - {entity: contact, effect: reads, facts: [First name, Last name]}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
- text: The Product removes the contact
  kind: product
  actor: user
  entities:
  - {entity: contact, effect: removes}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
---

# Delete one of several contacts

## Trigger

A person has left the client.

## Outcome

The contact is no longer listed or offered as a recipient.
