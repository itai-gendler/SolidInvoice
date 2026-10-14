---
domain: invoices
relations:
- {entity: contact, verb: is-sent-to, cardinality: many-to-many}
- {entity: payment, verb: receives, cardinality: one-to-many}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Entity/Invoice.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Entity/BaseInvoice.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Enum/InvoiceStatus.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Enum/PaymentTerms.php
- kind: code
  role: implementation
  target: config/packages/workflow.php
- kind: doc
  role: context
  target: docs/docs/invoices/invoice-statuses.md
---

# Invoice

A bill to one client. Its status is kept by the invoice state machine; its balance falls as payments are captured.

## Information kept

- **Invoice number** — the number generated from the company's invoice number format, changeable on the invoice
- **Invoice date** — the date the invoice is issued; payment terms count from it
- **Payment terms** — Due on receipt, Net 7, 14, 15, 30, 45, 60 or 90, End of month, End of next month, or Custom
- **Due date** — the date payment is due: worked out from the payment terms, or entered or left empty under Custom terms
- **Line items** — the items billed, each with a name, description, unit price, quantity to six decimal places and any number of line taxes; each line tax copies the tax rate's name, rate, category, type and compounding when it is chosen
- **Discount** — a discount on the whole invoice, as a percentage or a fixed amount
- **Withholding and adjustments** — taxes applied to the whole document, each additive, deductive or informational, with an optional note and the rate's name, rate and category copied onto the document
- **Terms** — terms and conditions shown to the client
- **Notes** — internal notes that are never shown to the client
- **Custom field values** — values for the company's invoice custom fields; client-visible ones appear on the invoice
- **Total** — the amount the invoice comes to after discount and taxes
- **Tax total** — the tax the invoice includes
- **Balance** — what is still owed: the total less captured payments
- **Paid date** — when the invoice became paid
- **Currency** — the client's currency while the invoice is a draft, fixed once it is issued
- **Listed in Archived** — whether the invoice is listed under Archived instead of the active invoices

## States

### Draft

Saved and still being prepared; not yet issued to the client.

### Pending

Issued; payment is expected.

### Overdue

Issued, unpaid, and past its due date.

### Paid

Paid in full.

### Cancelled

Withdrawn; no payment is expected.

### Archived

Put away from the invoice's own page; no further changes.
