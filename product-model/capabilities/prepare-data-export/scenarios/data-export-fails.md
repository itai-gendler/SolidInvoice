---
kind: edge
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
- text: Packaging fails and the Product records the export as failed
  kind: product
  entities:
  - {entity: data-export, effect: changes, from: Pending, to: Failed, facts: []}
  contexts:
    web: {place: 'web::company-workspace::data-exports'}
---

# Record a failed export

## Trigger

The export cannot be built.

## Outcome

The export is Failed; a new one can be requested.
