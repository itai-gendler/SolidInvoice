---
domain: tax-rates
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/TaxBundle/Action/Edit.php
- kind: code
  role: implementation
  target: src/TaxBundle/Entity/LineTax.php
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

# Edit a tax rate

Change a tax rate for documents prepared from now on.
