---
domain: custom-fields
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/SettingsBundle/Action/CustomField/ReorderAction.php
- kind: code
  role: implementation
  target: src/CoreBundle/Action/Api/CustomFieldReorderAction.php
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
---

# Reorder custom fields

Change the order fields appear in on forms and PDFs.
