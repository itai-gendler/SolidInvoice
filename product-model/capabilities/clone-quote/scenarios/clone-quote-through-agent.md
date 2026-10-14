---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to clone a quote
  kind: actor
  actor: ai-agent
  entities:
  - {entity: quote, as: original, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product creates a draft copy of the quote with a new quote number
  kind: product
  actor: ai-agent
  entities:
  - {entity: quote, as: copy, effect: creates, to: Draft, facts: [Quote number, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Currency]}
  - {entity: quote, as: original, effect: reads, facts: [Line items]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Mcp/QuoteWriteTools.php
---

# Clone a quote through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

A new Draft quote exists alongside the original.
