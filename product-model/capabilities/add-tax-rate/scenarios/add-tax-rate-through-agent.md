---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to create a tax rate with its name, rate, type, category and compounding
  kind: actor
  actor: ai-agent
  entities:
  - {entity: tax-rate, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product creates the tax rate
  kind: product
  actor: ai-agent
  entities:
  - {entity: tax-rate, effect: creates, facts: [Name, Rate, Type, Category, Compound]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/TaxBundle/Mcp/TaxWriteTools.php
---

# Add a tax rate through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The rate is offered on documents.
