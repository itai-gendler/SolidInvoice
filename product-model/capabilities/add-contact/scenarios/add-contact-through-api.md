---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to add a contact to a client
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: []}
  - {entity: contact, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product adds the contact to the client
  kind: product
  actor: user
  entities:
  - {entity: contact, effect: creates, facts: [First name, Last name, Email, Additional contact details]}
  - {entity: client, effect: reads, facts: []}
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

# Add a contact through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The contact is listed on the client.
