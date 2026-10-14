---
kind: primary
routes:
  web: Web
steps:
- text: The User picks CSV, JSON or XML and chooses Request Export
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::data-exports'}
- text: The Product queues the export
  kind: product
  actor: user
  entities:
  - {entity: data-export, effect: creates, to: Pending, facts: [Format, Requested at]}
  contexts:
    web: {place: 'web::company-workspace::data-exports'}
---

# Request a data export

## Trigger

The User wants all of the company's data.

## Outcome

The export is Pending and is prepared in the background.
