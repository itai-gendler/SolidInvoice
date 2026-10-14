---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to create a quote for a client with line items, discount, recipients and document taxes
  kind: actor
  actor: ai-agent
  entities:
  - {entity: quote, effect: reads, facts: []}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product creates the quote as a Draft with the next quote number
  kind: product
  actor: ai-agent
  entities:
  - {entity: quote, effect: creates, to: Draft, facts: [Quote number, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Currency]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Mcp/QuoteWriteTools.php
---

# Create a quote through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

A Draft quote exists for the client.
