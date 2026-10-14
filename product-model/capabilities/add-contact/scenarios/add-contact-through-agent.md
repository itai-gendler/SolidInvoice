---
kind: alternative
routes:
  web: Web
steps:
- text: The AI agent asks to add a contact with an email and optional name to a client
  kind: actor
  actor: ai-agent
  entities:
  - {entity: client, effect: reads, facts: []}
  - {entity: contact, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
- text: The Product adds the contact to the client
  kind: product
  actor: ai-agent
  entities:
  - {entity: contact, effect: creates, facts: [First name, Last name, Email]}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: mcp}
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Mcp/ClientWriteTools.php
---

# Add a contact through an AI agent

## Trigger

A User asks their connected AI agent to do this.

## Outcome

The contact is listed on the client.
