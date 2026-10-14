---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to change a contact's details
  kind: actor
  actor: user
  entities:
  - {entity: contact, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product saves the contact
  kind: product
  actor: user
  entities:
  - {entity: contact, effect: changes, facts: [First name, Last name, Email, Additional contact details]}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Entity/Contact.php
- kind: code
  role: implementation
  target: src/ClientBundle/Api/Processor/ContactPersistProcessor.php
---

# Edit a contact through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The contact shows the new details.
