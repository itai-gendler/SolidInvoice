---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to create a client with a name, website and currency
  kind: actor
  actor: ai-agent
  entities:
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product creates the active client
  kind: product
  actor: ai-agent
  entities:
  - {entity: client, effect: creates, to: Active, facts: [Name, Website, Currency, Credit balance]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/Tool/ResourceWriteTools.php
---

# Create a client through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The client exists in the company the agent is connected to.
