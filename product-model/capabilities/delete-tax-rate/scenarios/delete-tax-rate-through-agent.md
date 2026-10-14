---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to delete a tax rate
  kind: actor
  actor: ai-agent
  entities:
  - {entity: tax-rate, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product deletes the tax rate
  kind: product
  actor: ai-agent
  entities:
  - {entity: tax-rate, effect: removes}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/Tool/ResourceWriteTools.php
---

# Delete a tax rate through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The rate is no longer offered.
