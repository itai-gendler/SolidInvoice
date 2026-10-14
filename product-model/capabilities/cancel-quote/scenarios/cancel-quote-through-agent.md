---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to cancel a pending quote
  kind: actor
  actor: ai-agent
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product cancels the quote
  kind: product
  actor: ai-agent
  entities:
  - {entity: quote, effect: changes, from: Pending, to: Cancelled, facts: []}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Mcp/QuoteWriteTools.php
---

# Cancel a quote through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The quote is Cancelled.
