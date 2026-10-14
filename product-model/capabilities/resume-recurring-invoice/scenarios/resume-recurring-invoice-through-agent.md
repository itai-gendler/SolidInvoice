---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to resume a paused recurring invoice
  kind: actor
  actor: ai-agent
  entities:
  - {entity: recurring-invoice, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product makes the recurring invoice active again
  kind: product
  actor: ai-agent
  entities:
  - {entity: recurring-invoice, effect: changes, from: Paused, to: Active, facts: []}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/InvoiceWriteTools.php
---

# Resume a recurring invoice through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The recurring invoice is Active.
