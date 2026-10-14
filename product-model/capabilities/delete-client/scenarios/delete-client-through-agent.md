---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to delete a client
  kind: actor
  actor: ai-agent
  entities:
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product deletes the client with its contacts, addresses and tax identifiers
  kind: product
  actor: ai-agent
  entities:
  - {entity: client, effect: removes, from: Active}
  - {entity: contact, effect: removes, with: client}
  - {entity: address, effect: removes, with: client}
  - {entity: tax-identifier, effect: removes, with: client}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/Tool/ResourceWriteTools.php
---

# Delete a client through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The client and everything kept for it are gone.
