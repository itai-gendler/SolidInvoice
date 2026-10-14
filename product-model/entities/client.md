---
domain: clients
relations:
- {entity: contact, verb: has, cardinality: one-to-many}
- {entity: address, verb: has, cardinality: one-to-many}
- {entity: tax-identifier, verb: holds, cardinality: one-to-many}
- {entity: quote, verb: receives, cardinality: one-to-many}
- {entity: invoice, verb: receives, cardinality: one-to-many}
- {entity: recurring-invoice, verb: receives, cardinality: one-to-many}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Entity/Client.php
- kind: code
  role: implementation
  target: src/ClientBundle/Entity/Credit.php
- kind: code
  role: implementation
  target: src/ClientBundle/Entity/Address.php
- kind: code
  role: implementation
  target: src/ClientBundle/Enum/ClientStatus.php
- kind: doc
  role: context
  target: docs/docs/managing-clients/create-new-client.md
- kind: doc
  role: context
  target: docs/docs/managing-clients/client-credit.md
- kind: doc
  role: context
  target: docs/docs/managing-clients/client-currency.md
---

# Client

A business or person the company bills. Quotes, invoices, recurring invoices, payments and credit are always for one client and in that client's currency.

## Information kept

- **Name** — the client's company or trading name, unique within the company
- **Website** — the client's web address
- **Currency** — the currency the client is billed in; without one of its own the client follows the company currency
- **Payment terms** — the payment terms the client's new invoices start with; without them the company default applies
- **Credit balance** — a prepaid amount, in the client's currency, that can pay the client's invoices; it can go below zero
- **Custom field values** — values for the company's client custom fields

## States

### Active

The client can be chosen for new quotes, invoices and recurring invoices.

### Archived

The client is kept with its history but is no longer offered for new documents.
