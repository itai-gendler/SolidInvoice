---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to change a client's name, website or currency
  kind: actor
  actor: ai-agent
  entities:
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product saves the client's details
  kind: product
  actor: ai-agent
  entities:
  - {entity: client, effect: changes, facts: [Name, Website, Currency]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/Tool/ResourceWriteTools.php
---

# Edit a client through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The client shows the new details.
