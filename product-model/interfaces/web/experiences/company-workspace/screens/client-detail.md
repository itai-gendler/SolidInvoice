---
entities:
- entity: client
  shows:
  - Name
  - Website
  - Currency
  - Credit balance
  - Custom field values
- entity: contact
  shows:
  - First name
  - Last name
  - Email
  - Additional contact details
  collects:
  - First name
  - Last name
  - Email
  - Additional contact details
- entity: address
  shows: &id001
  - Street
  - City
  - State
  - Zip
  - Country
  collects: *id001
- entity: tax-identifier
  shows:
  - Type
  - Number
  - Primary
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Action/View.php
- kind: code
  role: implementation
  target: src/ClientBundle/Twig/Components/ContactCollection.php
- kind: code
  role: implementation
  target: src/ClientBundle/Twig/Components/ClientCredit.php
---

# Client detail

One client: its details, contacts, credit balance, and its quotes, invoices and payments.
