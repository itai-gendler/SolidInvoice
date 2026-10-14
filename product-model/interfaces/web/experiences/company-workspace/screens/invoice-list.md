---
entities:
- entity: invoice
  shows:
  - Invoice number
  - Invoice date
  - Due date
  - Paid date
  - Balance
  - Total
  - Tax total
  - Discount
- entity: client
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Action/Index.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/DataGrid/InvoiceGrid.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/DataGrid/ArchivedInvoiceGrid.php
---

# Invoice list

The company's invoices, active and archived, where invoices are archived, brought back or deleted in bulk.
