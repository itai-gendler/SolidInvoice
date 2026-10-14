---
domain: tax-rates
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/TaxBundle/DataGrid/TaxGrid.php
- kind: code
  role: implementation
  target: src/TaxBundle/Repository/TaxRepository.php
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
  target: src/McpBundle/Mcp/Tool/ResourceWriteTools.php
---

# Delete a tax rate

Remove tax rates.
