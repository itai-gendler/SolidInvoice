---
domain: quotes
relations:
- {entity: contact, verb: is-sent-to, cardinality: many-to-many}
- {entity: invoice, verb: becomes, cardinality: one-to-one}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Entity/Quote.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Enum/QuoteStatus.php
- kind: code
  role: implementation
  target: config/packages/workflow.php
---

# Quote

A priced proposal for one client. A quote the client agrees to is accepted on its behalf and becomes an invoice.

## Information kept

- **Quote number** — the number generated from the company's quote number format
- **Line items** — the items billed, each with a name, description, unit price, quantity to six decimal places and any number of line taxes; each line tax copies the tax rate's name, rate, category, type and compounding when it is chosen
- **Discount** — a discount on the whole quote, as a percentage or a fixed amount
- **Withholding and adjustments** — taxes applied to the whole document, each additive, deductive or informational, with an optional note and the rate's name, rate and category copied onto the document
- **Terms** — terms and conditions shown to the client
- **Notes** — internal notes that are never shown to the client
- **Custom field values** — values for the company's quote custom fields; client-visible ones appear on the quote
- **Total** — the amount the quote comes to after discount and taxes
- **Tax total** — the tax the quote includes
- **Currency** — the client's currency while the quote is a draft, fixed once it is issued
- **Listed in Archived** — whether the quote is listed under Archived instead of the active quotes

## States

### Draft

Saved and still being prepared; not yet issued to the client.

### Pending

Issued to the client and waiting for a decision.

### Accepted

The client agreed; the quote has become an invoice.

### Declined

The client said no.

### Cancelled

Withdrawn by the company.

### Archived

Put away from the quote's own page; no further changes.
