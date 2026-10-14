---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to reopen a cancelled invoice
  kind: actor
  actor: ai-agent
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product returns the invoice to draft
  kind: product
  actor: ai-agent
  entities:
  - {entity: invoice, effect: changes, from: Cancelled, to: Draft, facts: []}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/InvoiceWriteTools.php
---

# Reopen an invoice through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The invoice is a Draft again.
