---
kind: primary
routes:
  web: Web
steps:
- text: The User's integration sends a request to generate an invoice from a recurring invoice
  kind: actor
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: []}
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product creates a draft invoice from the recurring invoice's template, dated today, with its date placeholders filled in
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: creates, to: Draft, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Balance, Currency]}
  - {entity: recurring-invoice, effect: reads, facts: [Line items, Payment terms]}
  contexts:
    web: {place: rest-api}
---

# Generate an invoice from a recurring invoice now

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

A Draft invoice exists among the recurring invoice's generated invoices.

## Edge cases

- A recurring invoice that already has an invoice dated today is refused.
