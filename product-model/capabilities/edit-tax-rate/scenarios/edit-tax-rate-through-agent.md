---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to change some of a tax rate's values
  kind: actor
  actor: ai-agent
  entities:
  - {entity: tax-rate, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product saves the tax rate
  kind: product
  actor: ai-agent
  entities:
  - {entity: tax-rate, effect: changes, facts: [Name, Rate, Type, Category, Compound]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/TaxBundle/Mcp/TaxWriteTools.php
---

# Edit a tax rate through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

Line taxes chosen from now on use the new values.
