---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to reopen a cancelled quote
  kind: actor
  actor: ai-agent
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product returns the quote to draft
  kind: product
  actor: ai-agent
  entities:
  - {entity: quote, effect: changes, from: Cancelled, to: Draft, facts: []}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Mcp/QuoteWriteTools.php
---

# Reopen a quote through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The quote is a Draft again.
