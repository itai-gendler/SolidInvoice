---
domain: custom-fields
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/SettingsBundle/Action/CustomField/CreateAction.php
- kind: code
  role: implementation
  target: src/CoreBundle/Entity/CustomField/CustomField.php
- kind: doc
  role: intent
  target: docs/docs/managing-clients/custom-fields.md
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
---

# Add a custom field

Add an extra field to the company's clients, contacts, invoices or quotes.
