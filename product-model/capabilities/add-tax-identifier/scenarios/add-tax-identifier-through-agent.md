---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to add a tax identifier to a client
  kind: actor
  actor: ai-agent
  entities:
  - {entity: tax-identifier, effect: reads, facts: []}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product adds the tax identifier to the client
  kind: product
  actor: ai-agent
  entities:
  - {entity: tax-identifier, effect: creates, facts: [Type, Number, Primary]}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Mcp/ClientWriteTools.php
---

# Add a client tax identifier through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The number is recorded on the client.
