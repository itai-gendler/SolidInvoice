---
domain: payment-methods
relations:
- {entity: payment, verb: processes, cardinality: one-to-many}
references:
- kind: code
  role: implementation
  target: src/PaymentBundle/Entity/PaymentMethod.php
- kind: code
  role: implementation
  target: src/PaymentBundle/Form/Type/PaymentMethodType.php
---

# Payment method

A way invoices are paid: an online gateway such as Stripe or PayPal, or an offline method such as cash, bank transfer or client credit.

## Information kept

- **Name** — the name shown when choosing how to pay
- **Gateway** — the gateway or offline method it uses
- **Enabled** — whether it is offered when paying
- **Internal** — whether only signed-in Users may use it; contacts paying from a link never see it
- **Gateway settings** — the credentials and options the gateway needs
