---
appliesTo:
- type: capability
  id: delete-client
  contexts:
  - {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Entity/Client.php
- kind: doc
  role: intent
  target: docs/docs/managing-clients/client-list.md
---

# Deleting a client deletes everything kept for it

Its contacts, quotes, invoices, recurring invoices, payments and credit are deleted with it. Archiving is the way to stop billing a client and keep its history.
