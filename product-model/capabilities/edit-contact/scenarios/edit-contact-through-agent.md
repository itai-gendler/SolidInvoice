---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to change a contact's name or email
  kind: actor
  actor: ai-agent
  entities:
  - {entity: contact, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product saves the contact
  kind: product
  actor: ai-agent
  entities:
  - {entity: contact, effect: changes, facts: [First name, Last name, Email]}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/Tool/ResourceWriteTools.php
---

# Edit a contact through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The contact shows the new details.
