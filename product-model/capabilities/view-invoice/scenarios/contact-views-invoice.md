---
kind: primary
routes:
  web: Web
steps:
- text: The Contact follows the link in the invoice email
  kind: actor
  actor: contact
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::shared-documents::shared-invoice'}
- text: The Product shows the invoice with the company's and the client's details, without its internal notes
  kind: product
  actor: contact
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Total, Tax total, Balance, Currency]}
  - {entity: client, effect: reads, facts: [Name]}
  - {entity: address, effect: reads, facts: [Street, City, Country]}
  - {entity: tax-identifier, effect: reads, facts: [Type, Number]}
  - {entity: company, effect: reads, facts: [Name, Address]}
  contexts:
    web: {place: 'web::shared-documents::shared-invoice'}
---

# A contact opens an invoice from its email

## Trigger

A contact received an invoice by email.

## Outcome

The contact sees the invoice, can download it as a PDF, and is offered payment while it can be paid.

## Edge cases

- A signed-in User who follows the link is taken to the invoice in the company workspace instead.
