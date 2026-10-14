---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to clone an invoice
  kind: actor
  actor: ai-agent
  entities:
  - {entity: invoice, as: original, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product creates a draft copy of the invoice with a new invoice number
  kind: product
  actor: ai-agent
  entities:
  - {entity: invoice, as: copy, effect: creates, to: Draft, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Balance, Currency]}
  - {entity: invoice, as: original, effect: reads, facts: [Line items]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/InvoiceWriteTools.php
---

# Clone an invoice through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

A new Draft invoice exists alongside the original.
