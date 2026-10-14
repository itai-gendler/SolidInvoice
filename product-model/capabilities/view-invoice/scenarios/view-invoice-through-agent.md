---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to list invoices by status, list overdue ones or read one invoice
  kind: actor
  actor: ai-agent
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product returns the matching invoices
  kind: product
  actor: ai-agent
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Total, Balance, Due date]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/InvoiceReadTools.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/Tool/ResourceQueryTools.php
---

# Read invoices through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The agent has the invoices.
