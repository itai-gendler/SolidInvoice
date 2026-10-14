---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the recipients, line items, discount, withholding and adjustments, terms or notes and saves
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Line items, Discount, Withholding and adjustments, Terms, Notes]}
  contexts:
    web: {place: 'web::company-workspace::quote-editor'}
- text: The Product saves the quote and recalculates its totals
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: changes, facts: [Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total]}
  contexts:
    web: {place: 'web::company-workspace::quote-editor'}
- text: The Product shows the quote
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
---

# Edit a quote

## Trigger

A quote needs correcting.

## Outcome

The quote carries the new content; its status is unchanged.
