---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to apply the pay transition to a pending invoice
  kind: actor
  actor: ai-agent
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product marks the invoice paid with today as its paid date
  kind: product
  actor: ai-agent
  entities:
  - {entity: invoice, effect: changes, from: Pending, to: Paid, facts: [Paid date]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/InvoiceWriteTools.php
---

# Mark an invoice paid through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The invoice is Paid.
