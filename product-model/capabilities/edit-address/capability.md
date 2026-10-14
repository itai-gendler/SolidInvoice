---
domain: clients
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Entity/Address.php
- kind: code
  role: implementation
  target: src/ClientBundle/Twig/Components/AddressCollection.php
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
---

# Edit an address

Change one of a client's addresses.
