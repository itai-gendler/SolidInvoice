---
entities:
- entity: client
  shows:
  - Name
  - Website
  - Currency
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Action/Index.php
- kind: code
  role: implementation
  target: src/ClientBundle/DataGrid/ClientGrid.php
- kind: code
  role: implementation
  target: src/ClientBundle/DataGrid/ArchivedClientGrid.php
---

# Client list

The company's clients, active and archived, where clients are archived, brought back or deleted in bulk.
