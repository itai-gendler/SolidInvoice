---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to send a draft quote
  kind: actor
  actor: ai-agent
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product issues the quote and emails it to the contacts chosen on it
  kind: product
  actor: ai-agent
  entities:
  - {entity: quote, effect: changes, from: Draft, to: Pending, facts: []}
  - {entity: contact, effect: reads, facts: [Email]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Mcp/QuoteWriteTools.php
---

# Send a quote through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The quote is Pending and its contacts have it by email.
