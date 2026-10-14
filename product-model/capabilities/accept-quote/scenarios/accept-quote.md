---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Accept on a pending quote
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number, Total]}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
- text: The Product marks the quote accepted
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: changes, from: Pending, to: Accepted, facts: []}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
- text: The Product creates a draft invoice for the client from the quote, with its recipients, line items, discount, taxes, terms and notes and the client's or company's due terms
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: creates, to: Draft, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes, Total, Tax total, Balance, Currency]}
  - {entity: quote, effect: reads, facts: [Line items, Discount, Withholding and adjustments, Terms, Notes]}
  - {entity: client, effect: reads, facts: []}
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
- text: The Product takes the User to the new invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# Accept a pending quote

## Trigger

The client agrees to the quote.

## Outcome

The quote is Accepted and links to a new Draft invoice dated today, which the User is now looking at.
