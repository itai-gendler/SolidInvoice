---
references:
- kind: code
  role: implementation
  target: src/TaxBundle/Entity/TaxIdentifier.php
- kind: doc
  role: context
  target: docs/docs/taxes/client-tax-identifiers.md
- kind: doc
  role: context
  target: docs/docs/taxes/company-tax-identifiers.md
---

# Tax identifier

A tax registration number of a client or of the company itself, printed on the documents that involve it.

## Information kept

- **Type** — VAT, GSTIN, TIN, ABN, CNPJ, TRN or Other
- **Number** — the registration number
- **Primary** — whether it is the one emphasised on documents when there are several
