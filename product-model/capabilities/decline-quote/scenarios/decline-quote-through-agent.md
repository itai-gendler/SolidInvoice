---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to decline a pending quote
  kind: actor
  actor: ai-agent
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product marks the quote declined
  kind: product
  actor: ai-agent
  entities:
  - {entity: quote, effect: changes, from: Pending, to: Declined, facts: []}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Mcp/QuoteWriteTools.php
---

# Decline a quote through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The quote is Declined.
