---
references:
- kind: code
  role: implementation
  target: src/PaymentBundle/Entity/Payment.php
- kind: code
  role: implementation
  target: src/PaymentBundle/Enum/PaymentStatus.php
---

# Payment

Money received, or attempted, against one invoice through one payment method.

## Information kept

- **Amount** — the amount paid, in the invoice's currency; more than zero
- **Currency** — the invoice's currency when the payment was made
- **Reference** — a reference a User records with the payment
- **Notes** — notes a User records with the payment
- **Completed at** — when the payment's outcome was recorded

## States

### New

Started and handed to the payment gateway; no outcome yet.

### Captured

The money was received.

### Failed

The gateway reported that the payment did not go through.
