---
domain: profile
availability:
- {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Export/Action/RequestExport.php
- kind: code
  role: implementation
  target: src/CoreBundle/Export/Action/DownloadExport.php
- kind: code
  role: implementation
  target: src/CoreBundle/Export/Message/Handler/ProcessCompanyExportHandler.php
- kind: doc
  role: intent
  target: docs/docs/using-solidinvoice/exporting-data.md
---

# Prepare a data export

Build a requested export in the background and tell the User when it is ready.
