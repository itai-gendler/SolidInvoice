---
domain: tax-rates
references:
- kind: code
  role: implementation
  target: src/TaxBundle/Entity/Tax.php
- kind: code
  role: implementation
  target: src/TaxBundle/Enum/TaxType.php
- kind: code
  role: implementation
  target: src/TaxBundle/Enum/TaxCategory.php
- kind: doc
  role: context
  target: docs/docs/taxes/tax-rates.md
---

# Tax rate

A tax the company applies to line items or to a whole document.

## Information kept

- **Name** — a short label such as VAT, unique within the company and at most 32 characters
- **Rate** — the percentage, or for a flat rate the fixed amount
- **Type** — Inclusive (contained in the price), Exclusive (added on top) or Flat rate
- **Category** — Standard, Zero-rated, Exempt, Out of scope or Reverse charge
- **Compound** — whether it is calculated on the line amount including the line's earlier taxes
