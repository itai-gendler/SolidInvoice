---
kind: alternative
routes:
  web: Web
steps:
- text: The User picks an active client and the contacts to send to
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Name]}
  - {entity: contact, effect: reads, facts: [First name, Last name, Email]}
  contexts:
    web: {place: 'web::company-workspace::quote-editor'}
- text: The User enters line items with their taxes, a discount, withholding and adjustments, terms and notes
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::quote-editor'}
- text: The User chooses Save and Send
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::quote-editor'}
- text: The Product creates the quote and issues it as Pending
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: creates, to: Pending, facts: [Quote number, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Currency]}
  contexts:
    web: {place: 'web::company-workspace::quote-editor'}
- text: The Product emails the quote, with its PDF and a link to view it, to the chosen contacts
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number]}
  - {entity: contact, effect: reads, facts: [Email]}
  - {entity: company, effect: reads, facts: [Quote email subject, Quote BCC address]}
  contexts:
    web: {place: 'web::company-workspace::quote-editor'}
- text: The Product shows the new quote
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
---

# Create and send a quote

## Trigger

The quote is ready to go to the client now.

## Outcome

The quote is Pending and the chosen contacts have it by email.
