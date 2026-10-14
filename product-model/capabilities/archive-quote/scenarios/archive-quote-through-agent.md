---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to archive an accepted quote
  kind: actor
  actor: ai-agent
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product archives the quote
  kind: product
  actor: ai-agent
  entities:
  - {entity: quote, effect: changes, from: Accepted, to: Archived, facts: [Listed in Archived]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Mcp/QuoteWriteTools.php
---

# Archive a quote through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The quote is Archived.
