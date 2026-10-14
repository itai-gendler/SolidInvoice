---
kind: primary
routes:
  web: Web
steps:
- text: A pending export is waiting
  kind: condition
  unattended: true
  entities:
  - {entity: data-export, effect: reads, facts: [Format]}
  contexts:
    web: {place: 'web::company-workspace::data-exports'}
- text: The Product packages the company's clients, contacts, quotes, invoices, payments and other records into one archive
  kind: product
  entities:
  - {entity: data-export, effect: changes, from: Pending, to: Completed, facts: [Archive, Completed at]}
  - {entity: payment, effect: reads, facts: []}
  - {entity: invoice, effect: reads, facts: []}
  - {entity: quote, effect: reads, facts: []}
  - {entity: client, effect: reads, facts: []}
  - {entity: contact, effect: reads, facts: []}
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::data-exports'}
- text: The Product emails the User who asked that the export is ready
  kind: product
  entities:
  - {entity: data-export, effect: reads, facts: [Format]}
  - {entity: user, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'web::company-workspace::data-exports'}
---

# Prepare a requested export

## Trigger

An export was requested.

## Outcome

The export is Completed and can be downloaded.
