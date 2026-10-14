---
domain: invoices
availability:
- {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/DataGrid/ArchivedInvoiceGrid.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Repository/InvoiceRepository.php
---

# Activate an archived invoice

Bring an invoice listed under Archived back to the active invoices.
