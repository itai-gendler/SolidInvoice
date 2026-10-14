---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to get outstanding and overdue totals, invoice counts by status or revenue by period
  kind: actor
  actor: ai-agent
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product returns the figures per currency
  kind: product
  actor: ai-agent
  entities:
  - {entity: invoice, effect: reads, facts: [Balance, Total]}
  - {entity: payment, effect: reads, facts: [Amount]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/DashboardBundle/Mcp/AnalyticsTools.php
---

# Read the company's figures through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The agent has the figures.
