---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to create a recurring invoice for a client with its line items and a daily, weekly, monthly or yearly schedule
  kind: actor
  actor: ai-agent
  entities:
  - {entity: recurring-invoice, effect: reads, facts: []}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product creates the recurring invoice as a Draft
  kind: product
  actor: ai-agent
  entities:
  - {entity: recurring-invoice, effect: creates, to: Draft, facts: [Start date, Recurring type, Repeat days, End recurrence, End date, End after occurrences, Payment terms, Line items, Discount, Withholding and adjustments, Terms, Notes, Total, Tax total]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Mcp/RecurringInvoiceWriteTools.php
---

# Create a recurring invoice through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

A Draft recurring invoice exists.
