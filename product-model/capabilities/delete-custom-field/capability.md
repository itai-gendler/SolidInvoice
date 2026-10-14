---
domain: custom-fields
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/SettingsBundle/Action/CustomField/DeleteAction.php
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: code
  role: implementation
  target: src/CoreBundle/Entity/CustomField/CustomField.php
---

# Delete a custom field

Remove a custom field and every value kept for it.
