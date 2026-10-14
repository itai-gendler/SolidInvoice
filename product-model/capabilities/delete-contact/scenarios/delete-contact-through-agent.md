---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to delete one of a client's contacts
  kind: actor
  actor: ai-agent
  entities:
  - {entity: client, effect: reads, facts: []}
  - {entity: contact, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product removes the contact
  kind: product
  actor: ai-agent
  entities:
  - {entity: contact, effect: removes}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/Tool/ResourceWriteTools.php
---

# Delete a contact through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The contact is gone.
