---
domain: clients
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Action/Delete.php
- kind: code
  role: implementation
  target: src/ClientBundle/DataGrid/BaseClientGrid.php
- kind: doc
  role: intent
  target: docs/docs/managing-clients/client-list.md
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: code
  role: implementation
  target: src/ClientBundle/Entity/Client.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/McpScopeGuard.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/Tool/ResourceWriteTools.php
---

# Delete a client

Remove a client permanently together with everything kept for it.
