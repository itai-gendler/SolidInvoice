---
domain: tax-rates
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/TaxBundle/Action/Add.php
- kind: code
  role: implementation
  target: src/TaxBundle/Form/Type/TaxType.php
- kind: doc
  role: intent
  target: docs/docs/taxes/tax-rates.md
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: code
  role: implementation
  target: src/TaxBundle/Entity/Tax.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/McpScopeGuard.php
- kind: code
  role: implementation
  target: src/TaxBundle/Mcp/TaxWriteTools.php
---

# Add a tax rate

Create a tax rate the company can apply to line items and whole documents.
