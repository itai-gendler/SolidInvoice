---
domain: clients
availability:
- {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/DataGrid/ClientGrid.php
- kind: code
  role: implementation
  target: src/ClientBundle/Repository/ClientRepository.php
- kind: doc
  role: intent
  target: docs/docs/managing-clients/client-list.md
---

# Archive a client

Keep a client and its history but stop offering it for new documents.
