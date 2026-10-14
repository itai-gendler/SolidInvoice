---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to pause an active recurring invoice
  kind: actor
  actor: ai-agent
  entities:
  - {entity: recurring-invoice, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product pauses the recurring invoice
  kind: product
  actor: ai-agent
  entities:
  - {entity: recurring-invoice, effect: changes, from: Active, to: Paused, facts: []}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/InvoiceWriteTools.php
---

# Pause a recurring invoice through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The recurring invoice is Paused.
