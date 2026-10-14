---
entities:
- entity: ai-agent
  shows:
  - Name
  - Write access
  collects:
  - Write access
- entity: company
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: src/McpBundle/Action/ConnectedAppsList.php
- kind: code
  role: implementation
  target: src/McpBundle/Action/Authorize.php
---

# Connected apps

The AI agents the User has connected, and where access is approved.
