---
domain: clients
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Action/View.php
- kind: doc
  role: intent
  target: docs/docs/managing-clients/viewing-a-client.md
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
  target: src/ClientBundle/Mcp/ClientReadTools.php
---

# View a client

See a client with its contacts, addresses, credit and billing totals.
