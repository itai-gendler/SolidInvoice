---
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Entity/ExportJob.php
- kind: code
  role: implementation
  target: src/CoreBundle/Export/Enum/ExportStatus.php
- kind: doc
  role: context
  target: docs/docs/using-solidinvoice/exporting-data.md
---

# Data export

A full export of one company's data that a User requested, prepared in the background as a downloadable archive.

## Information kept

- **Format** — CSV, JSON or XML
- **Archive** — the downloadable archive
- **Requested at** — when it was requested
- **Completed at** — when it finished

## States

### Pending

Requested and waiting to be prepared.

### Completed

Ready to download.

### Failed

Could not be prepared.
