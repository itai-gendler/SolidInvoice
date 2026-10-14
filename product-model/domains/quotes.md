---
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Menu/QuoteMenu.php
---

# Quotes

Quotes prepared for clients, from draft to accepted, declined or cancelled.

## Boundary

Owns preparing, sending and deciding quotes. It does not own the invoice an accepted quote becomes, which belongs to Invoices.
