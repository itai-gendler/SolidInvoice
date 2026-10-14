---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Clone on a quote
  kind: actor
  actor: user
  entities:
  - {entity: quote, as: original, effect: reads, facts: [Quote number]}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
- text: The Product creates a draft quote with the same client, recipients, line items, discount, taxes, terms and notes and a new quote number
  kind: product
  actor: user
  entities:
  - {entity: quote, as: copy, effect: creates, to: Draft, facts: [Quote number, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Currency]}
  - {entity: quote, as: original, effect: reads, facts: [Line items, Discount, Withholding and adjustments, Terms, Notes]}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
- text: The Product shows the new quote
  kind: product
  actor: user
  entities:
  - {entity: quote, as: copy, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
---

# Clone a quote

## Trigger

The User wants a similar quote without retyping it.

## Outcome

A new Draft quote exists alongside the original.
