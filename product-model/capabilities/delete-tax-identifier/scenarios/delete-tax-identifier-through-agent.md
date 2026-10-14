---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to remove a tax identifier from a client
  kind: actor
  actor: ai-agent
  entities:
  - {entity: tax-identifier, effect: reads, facts: []}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product removes the tax identifier
  kind: product
  actor: ai-agent
  entities:
  - {entity: tax-identifier, effect: removes}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Mcp/ClientWriteTools.php
---

# Remove a client tax identifier through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The number is gone.
