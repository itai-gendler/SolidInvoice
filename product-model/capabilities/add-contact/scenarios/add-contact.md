---
kind: primary
routes:
  web: Web
steps:
- text: The User enters the contact's first name, last name, email and additional contact details
  kind: actor
  actor: user
  entities:
  - {entity: contact, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
- text: The Product adds the contact to the client
  kind: product
  actor: user
  entities:
  - {entity: contact, effect: creates, facts: [First name, Last name, Email, Additional contact details, Custom field values]}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
---

# Add a contact to a client

## Trigger

Someone else at the client should receive documents.

## Outcome

The contact is listed on the client and can be chosen as a recipient.
