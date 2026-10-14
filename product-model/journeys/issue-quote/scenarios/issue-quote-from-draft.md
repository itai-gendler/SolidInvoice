---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User picks a client and contacts and enters the quote
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Name]}
  - {entity: contact, effect: reads, facts: [First name, Last name, Email]}
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::quote-editor'}
  capability: create-quote
- text: The Product creates the quote as a Draft
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: creates, to: Draft, facts: [Quote number, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Currency]}
  contexts:
    web: {place: 'web::company-workspace::quote-editor'}
  capability: create-quote
- text: The Product takes the User to the new quote
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
  capability: create-quote
- text: The User chooses Send
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number]}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
  capability: send-quote
- text: The Product issues the quote
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: changes, from: Draft, to: Pending, facts: []}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
  capability: send-quote
- text: The Product emails the quote to the contacts chosen on it
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number]}
  - {entity: contact, effect: reads, facts: [Email]}
  - {entity: company, effect: reads, facts: [Quote email subject, Quote BCC address]}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
  capability: send-quote
---

# Draft a quote, then send it

## Trigger

The User offers work to a client.

## Outcome

The client's contacts have the Pending quote.
