---
domain: recurring-invoices
relations:
- {entity: contact, verb: is-sent-to, cardinality: many-to-many}
- {entity: invoice, verb: generates, cardinality: one-to-many}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Entity/RecurringInvoice.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Entity/RecurringOptions.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Enum/RecurringInvoiceStatus.php
- kind: code
  role: implementation
  target: config/packages/workflow.php
- kind: doc
  role: context
  target: docs/docs/recurring-invoices/managing-the-schedule.md
---

# Recurring invoice

A template for one client that generates a real invoice on each date its schedule matches, until it is stopped or reaches its end.

## Information kept

- **Start date** — when the schedule begins; not in the past when set
- **Recurring type** — Daily, Weekly, Monthly or Yearly
- **Repeat days** — the weekdays, days of the month, or months and day of month the schedule matches
- **End recurrence** — Never, On a date, or After a number of occurrences
- **End date** — the date the schedule ends, when it ends on a date
- **End after occurrences** — how many invoices the schedule generates, when it ends after occurrences
- **Payment terms** — the payment terms each generated invoice gets, counted from the day it is generated
- **Line items** — the items each generated invoice bills; their names and descriptions may hold {day}, {day_name}, {month} and {year}
- **Discount** — a discount on each generated invoice
- **Withholding and adjustments** — taxes applied to each generated invoice as a whole
- **Terms** — terms and conditions for each generated invoice
- **Notes** — internal notes for each generated invoice
- **Total** — the amount each generated invoice comes to
- **Tax total** — the tax each generated invoice includes
- **Listed in Archived** — whether the recurring invoice is listed under Archived

## States

### Draft

Saved but not generating invoices.

### Active

Generating invoices on matching dates.

### Paused

Temporarily not generating; the schedule is kept.

### Complete

The schedule reached its end date or number of occurrences.

### Cancelled

Stopped by the company; no more invoices are generated.

### Archived

Put away from the recurring invoice's own page.
