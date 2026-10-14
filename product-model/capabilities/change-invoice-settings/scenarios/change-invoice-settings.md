---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the default due terms, number format, email subject, BCC recipient, watermark or reminder settings and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::settings'}
- text: The Product saves the company's invoice settings
  kind: product
  actor: user
  entities:
  - {entity: company, effect: changes, facts: [Default payment terms, Invoice number format, Invoice email subject, Invoice BCC address, Invoice watermark, Automatic reminders, Pre-due reminders, Pre-due reminder days]}
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::settings'}
---

# Change invoice settings

## Trigger

The company adjusts how it invoices.

## Outcome

New invoices, invoice emails and reminders follow the new settings.
