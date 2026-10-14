---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the contact's name, email or additional contact details
  kind: actor
  actor: user
  entities:
  - {entity: contact, effect: reads, facts: [First name, Last name, Email, Additional contact details]}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
- text: The Product saves the contact
  kind: product
  actor: user
  entities:
  - {entity: contact, effect: changes, facts: [First name, Last name, Email, Additional contact details, Custom field values]}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
---

# Edit a contact's details

## Trigger

A contact's details have changed.

## Outcome

Documents and reminders go to the contact's new email.
