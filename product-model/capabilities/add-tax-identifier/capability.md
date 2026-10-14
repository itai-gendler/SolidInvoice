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
- kind: doc
  role: intent
  target: docs/docs/taxes/client-tax-identifiers.md
- kind: doc
  role: intent
  target: docs/docs/taxes/company-tax-identifiers.md
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

# Add a tax identifier

Record a tax registration number for a client or for the company itself.
