---
entities:
- entity: recurring-invoice
  shows:
  - Recurring type
  - Start date
  - End date
  - Total
  - Tax total
  - Discount
- entity: client
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Action/RecurringIndex.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/DataGrid/RecurringInvoiceGrid.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/DataGrid/CompletedRecurringInvoiceGrid.php
---

# Recurring invoice list

The company's recurring invoices under Active, Completed and Archived, where completed ones are reactivated and recurring invoices are deleted in bulk.
