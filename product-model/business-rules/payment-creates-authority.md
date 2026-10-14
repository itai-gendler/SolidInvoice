---
appliesTo:
- type: entity
  id: payment
  effect: creates
permits:
- related:
  - &id001 {verb: receives, entity: invoice}
  - &id002 {verb: keeps, entity: company}
  - &id003 {verb: belongs-to, entity: user}
  when:
  - entity: payment-method
    fact: Enabled
    is: 'Yes'
- related:
  - *id001
  - *id002
  - *id003
  - {verb: connects, entity: ai-agent}
  when:
  - entity: ai-agent
    fact: Write access
    is: 'Yes'
- actors:
  - contact
  when:
  - entity: payment-method
    fact: Enabled
    is: 'Yes'
  - entity: payment-method
    fact: Internal
    is: 'No'
references:
- kind: code
  role: implementation
  target: src/PaymentBundle/Action/Prepare.php
- kind: code
  role: implementation
  target: src/PaymentBundle/Repository/PaymentMethodRepository.php
- kind: code
  role: implementation
  target: src/PaymentBundle/Form/Type/PaymentType.php
---

# Users of the owning company pay an invoice with any enabled method; a contact pays only with an enabled method that is not internal

Users may record payments with every enabled method, internal ones such as cash, bank transfer or client credit included; through the REST API, and a connected agent with write access through the MCP server, they record offline payments. The payment page reached from an emailed link offers only enabled methods that are not internal, and refuses an internal one.
