---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to summarise a client
  kind: actor
  actor: ai-agent
  entities:
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product returns the client with its totals invoiced, outstanding and paid, its counts and its tax identifiers
  kind: product
  actor: ai-agent
  entities:
  - {entity: client, effect: reads, facts: [Name, Currency]}
  - {entity: invoice, effect: reads, facts: [Total, Balance]}
  - {entity: tax-identifier, effect: reads, facts: [Type, Number]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Mcp/ClientReadTools.php
---

# Read a client summary through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The agent has the client's summary.
