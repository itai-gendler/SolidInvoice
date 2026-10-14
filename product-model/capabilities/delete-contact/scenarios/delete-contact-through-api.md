---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to delete one of a client's contacts
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: []}
  - {entity: contact, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product removes the contact
  kind: product
  actor: user
  entities:
  - {entity: contact, effect: removes}
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

# Delete a contact through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The contact is gone.
