---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to cancel a pending invoice
  kind: actor
  actor: ai-agent
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product cancels the invoice
  kind: product
  actor: ai-agent
  entities:
  - {entity: invoice, effect: changes, from: Pending, to: Cancelled, facts: []}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/InvoiceWriteTools.php
---

# Cancel an invoice through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The invoice is Cancelled.
