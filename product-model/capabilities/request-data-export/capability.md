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

# Request a data export

Ask for a full export of the current company's data.
