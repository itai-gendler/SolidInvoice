---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to send a reminder for an unpaid invoice
  kind: actor
  actor: ai-agent
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product emails a reminder to the contacts chosen on the invoice
  kind: product
  actor: ai-agent
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Balance, Due date]}
  - {entity: contact, effect: reads, facts: [Email]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/InvoiceWriteTools.php
---

# Send a payment reminder through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The contacts have a reminder.

## Edge cases

- An invoice with no contacts chosen is refused.
