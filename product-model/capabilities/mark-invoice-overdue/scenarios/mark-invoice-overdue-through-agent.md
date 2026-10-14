---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to apply the overdue transition to a pending invoice
  kind: actor
  actor: ai-agent
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product marks the invoice overdue
  kind: product
  actor: ai-agent
  entities:
  - {entity: invoice, effect: changes, from: Pending, to: Overdue, facts: []}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/InvoiceWriteTools.php
---

# Mark an invoice overdue through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The invoice is Overdue.
