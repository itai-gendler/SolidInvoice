---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to activate a draft recurring invoice
  kind: actor
  actor: ai-agent
  entities:
  - {entity: recurring-invoice, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product activates the recurring invoice
  kind: product
  actor: ai-agent
  entities:
  - {entity: recurring-invoice, effect: changes, from: Draft, to: Active, facts: []}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/InvoiceWriteTools.php
---

# Activate a recurring invoice through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The recurring invoice is Active.
