---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Download on a completed export
  kind: actor
  actor: user
  entities:
  - {entity: data-export, effect: reads, facts: [Format, Completed at]}
  contexts:
    web: {place: 'web::company-workspace::data-exports'}
- text: The Product downloads the archive
  kind: product
  actor: user
  entities:
  - {entity: data-export, effect: reads, facts: [Archive]}
  contexts:
    web: {place: 'web::company-workspace::data-exports'}
---

# Download a completed export

## Trigger

The export is ready.

## Outcome

The User has the archive.

## Edge cases

- An export that is not completed yet returns the User to the list.
