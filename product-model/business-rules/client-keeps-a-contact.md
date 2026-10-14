---
appliesTo:
- type: capability
  id: create-client
- type: capability
  id: delete-contact
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Twig/Components/ContactCollection.php
- kind: code
  role: implementation
  target: src/ClientBundle/Form/Type/ContactCollectionType.php
- kind: doc
  role: intent
  target: docs/docs/managing-clients/viewing-a-client.md
---

# A client always has at least one contact

A new client needs a contact, and a client's last contact cannot be deleted.
