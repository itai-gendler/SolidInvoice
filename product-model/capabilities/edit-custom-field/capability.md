---
domain: custom-fields
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/SettingsBundle/Action/CustomField/EditAction.php
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: code
  role: implementation
  target: src/CoreBundle/Entity/CustomField/CustomField.php
---

# Edit a custom field

Change a custom field's definition.
