---
entities:
- entity: client
  shows:
  - Name
  - Website
  - Currency
  - Payment terms
  - Custom field values
  collects:
  - Name
  - Website
  - Currency
  - Payment terms
  - Custom field values
- entity: contact
  collects:
  - First name
  - Last name
  - Email
  - Additional contact details
  - Custom field values
- entity: address
  collects:
  - Street
  - City
  - State
  - Zip
  - Country
- entity: tax-identifier
  shows: &id001
  - Type
  - Number
  - Primary
  collects: *id001
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Action/Add.php
- kind: code
  role: implementation
  target: src/ClientBundle/Action/Edit.php
- kind: code
  role: implementation
  target: src/ClientBundle/Form/Type/ClientType.php
---

# Client form

Adding a client or changing one client's details, with its contacts when the client is new.
