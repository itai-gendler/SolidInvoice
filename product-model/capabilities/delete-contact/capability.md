---
domain: clients
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Twig/Components/ContactCollection.php
- kind: code
  role: implementation
  target: src/ClientBundle/Entity/Client.php
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: code
  role: implementation
  target: src/ClientBundle/Entity/Contact.php
- kind: code
  role: implementation
  target: src/ClientBundle/Api/Processor/ContactPersistProcessor.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/McpScopeGuard.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/Tool/ResourceWriteTools.php
---

# Delete a contact

Remove a person from a client.
