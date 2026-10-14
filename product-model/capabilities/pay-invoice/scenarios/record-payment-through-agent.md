---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to record an offline payment of the full balance of a pending invoice, in its currency
  kind: actor
  actor: ai-agent
  entities:
  - {entity: payment, effect: reads, facts: []}
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product records the payment as captured and marks the invoice paid
  kind: product
  actor: ai-agent
  entities:
  - {entity: payment, effect: creates, to: Captured, facts: [Amount, Currency, Reference, Notes, Completed at]}
  - {entity: invoice, effect: changes, from: Pending, to: Paid, facts: [Paid date]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/PaymentBundle/Mcp/PaymentWriteTools.php
---

# Record a payment through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The payment is Captured and the invoice is Paid.

## Edge cases

- An amount above the invoice balance is refused.
