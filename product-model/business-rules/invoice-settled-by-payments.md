---
appliesTo:
- type: entity
  id: invoice
  effect: changes
  to: Paid
permits:
- related:
  - &id001 {verb: keeps, entity: company}
  - &id002 {verb: belongs-to, entity: user}
- actors:
  - contact
- related:
  - *id001
  - *id002
  - {verb: connects, entity: ai-agent}
  when:
  - entity: ai-agent
    fact: Write access
    is: 'Yes'
references:
- kind: code
  role: implementation
  target: src/PaymentBundle/Listener/PaymentCompleteListener.php
---

# Only users of the owning company, a contact paying from the link or a connected agent with write access mark an invoice paid

A captured payment that covers the total marks the invoice paid, whoever made it. Users of the company may also mark an invoice paid through the REST API, and a connected agent with write access through the MCP server.
