---
appliesTo:
- type: capability
  id: publish-invoice
- type: capability
  id: send-invoice
- type: capability
  id: publish-quote
- type: capability
  id: send-quote
- type: capability
  id: edit-client
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Listener/FreezeCurrencyListener.php
- kind: code
  role: implementation
  target: src/CoreBundle/Traits/Entity/HasFrozenCurrency.php
---

# An issued invoice or quote keeps the currency it was issued in

While a document is a draft its currency is the client's current currency. When it leaves draft the currency is fixed on the document, so changing the client's currency, or the company currency the client follows, changes drafts but never an issued document.

## Rationale

Amounts on an issued document must keep meaning what they meant when the client received them.
