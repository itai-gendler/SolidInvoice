---
kind: primary
routes:
  web: Web
steps:
- text: The Contact follows the link in the quote email
  kind: actor
  actor: contact
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: 'web::shared-documents::shared-quote'}
- text: The Product shows the quote with the company's and the client's details, without its internal notes
  kind: product
  actor: contact
  entities:
  - {entity: quote, effect: reads, facts: [Quote number, Line items, Discount, Withholding and adjustments, Terms, Total, Tax total, Currency]}
  - {entity: client, effect: reads, facts: [Name]}
  - {entity: address, effect: reads, facts: [Street, City, Country]}
  - {entity: tax-identifier, effect: reads, facts: [Type, Number]}
  - {entity: company, effect: reads, facts: [Name, Address]}
  contexts:
    web: {place: 'web::shared-documents::shared-quote'}
---

# A contact opens a quote from its email

## Trigger

A contact received a quote by email.

## Outcome

The contact sees the quote and can download it as a PDF.

## Edge cases

- A signed-in User who follows the link is taken to the quote in the company workspace instead.
