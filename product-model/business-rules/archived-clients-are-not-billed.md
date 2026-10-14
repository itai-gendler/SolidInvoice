---
appliesTo:
- type: capability
  id: create-quote
- type: capability
  id: create-invoice
- type: capability
  id: create-recurring-invoice
- type: capability
  id: archive-client
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Form/ClientAutocompleteType.php
- kind: code
  role: implementation
  target: src/CoreBundle/Doctrine/Filter/ArchivableFilter.php
- kind: doc
  role: intent
  target: docs/docs/managing-clients/client-list.md
---

# Archived clients are not offered for new quotes, invoices or recurring invoices

Only active clients can be picked when preparing a document; archiving keeps the client's existing documents.
