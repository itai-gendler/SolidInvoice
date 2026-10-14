---
appliesTo:
- type: entity
  id: invitation
  effect: changes
  to: Expired
permits:
- actors:
  - visitor
references:
- kind: code
  role: implementation
  target: src/UserBundle/Action/AcceptInvitation.php
- kind: code
  role: implementation
  target: src/UserBundle/Action/Register.php
---

# An invitation followed after it expired is marked expired

Following an invitation link past its expiry marks it expired and refuses it.
