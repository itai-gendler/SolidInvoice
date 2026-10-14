---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses to add a new client and enters its name and a contact's first name, last name and email
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: []}
  - {entity: contact, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::quote-editor'}
- text: The User enters line items with their taxes, a discount, withholding and adjustments, terms and notes
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::quote-editor'}
- text: The User chooses Save as Draft
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::quote-editor'}
- text: The Product creates the client with that contact
  kind: product
  actor: user
  entities:
  - {entity: client, effect: creates, to: Active, facts: [Name, Credit balance]}
  - {entity: contact, effect: creates, facts: [First name, Last name, Email], with: client}
  contexts:
    web: {place: 'web::company-workspace::quote-editor'}
- text: The Product creates the quote for the new client as a Draft
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: creates, to: Draft, facts: [Quote number, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Currency]}
  - {entity: client, effect: reads, facts: []}
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

# Create a quote for a new client

## Trigger

The quote is for someone who is not a client yet.

## Outcome

The new client and its contact exist, and the Draft quote is addressed to that contact.
