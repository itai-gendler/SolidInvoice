---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to archive a cancelled recurring invoice
  kind: actor
  actor: ai-agent
  entities:
  - {entity: recurring-invoice, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product archives the recurring invoice
  kind: product
  actor: ai-agent
  entities:
  - {entity: recurring-invoice, effect: changes, from: Cancelled, to: Archived, facts: [Listed in Archived]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/InvoiceWriteTools.php
---

# Archive a recurring invoice through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The recurring invoice is Archived.
