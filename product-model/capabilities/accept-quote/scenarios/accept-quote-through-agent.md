---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to accept a pending quote
  kind: actor
  actor: ai-agent
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product marks the quote accepted and creates a draft invoice from it
  kind: product
  actor: ai-agent
  entities:
  - {entity: quote, effect: changes, from: Pending, to: Accepted, facts: []}
  - {entity: invoice, effect: creates, to: Draft, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Balance, Currency]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Mcp/QuoteWriteTools.php
---

# Accept a quote through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The quote is Accepted and its invoice is a Draft.
