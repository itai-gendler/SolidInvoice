---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to create an invoice for a client with line items, discount, payment terms, recipients and document taxes
  kind: actor
  actor: ai-agent
  entities:
  - {entity: payment, effect: reads, facts: []}
  - {entity: invoice, effect: reads, facts: []}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product creates the invoice as a Draft with the next invoice number and the due date its terms give
  kind: product
  actor: ai-agent
  entities:
  - {entity: invoice, effect: creates, to: Draft, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Balance, Currency]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/InvoiceWriteTools.php
---

# Create an invoice through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

A Draft invoice exists for the client.
