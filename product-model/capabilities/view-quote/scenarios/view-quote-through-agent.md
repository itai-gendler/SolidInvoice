---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to list quotes by status or read one quote
  kind: actor
  actor: ai-agent
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product returns the matching quotes
  kind: product
  actor: ai-agent
  entities:
  - {entity: quote, effect: reads, facts: [Quote number, Line items, Total]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Mcp/QuoteReadTools.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/Tool/ResourceQueryTools.php
---

# Read quotes through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The agent has the quotes.
