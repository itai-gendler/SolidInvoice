---
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/TaxBundle/Entity/TaxIdentifier.php
- kind: code
  role: implementation
  target: src/TaxBundle/Form/Type/TaxIdentifierType.php
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/McpScopeGuard.php
- kind: code
  role: implementation
  target: src/ClientBundle/Mcp/ClientWriteTools.php
---

# Delete a tax identifier

Remove a recorded tax registration number.
