---
domain: clients
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Action/Add.php
- kind: code
  role: implementation
  target: src/ClientBundle/Twig/Components/ClientForm.php
- kind: doc
  role: intent
  target: docs/docs/managing-clients/create-new-client.md
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

# Create a client

Add a client with its details and at least one contact, ready to be billed.
