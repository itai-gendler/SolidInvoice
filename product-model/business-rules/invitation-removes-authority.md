---
appliesTo:
- type: entity
  id: invitation
  effect: removes
permits:
- related:
  - {verb: keeps, entity: company}
  - {verb: belongs-to, entity: user}
- actors:
  - visitor
references:
- kind: code
  role: implementation
  target: src/UserBundle/Action/DeleteUserInvite.php
- kind: code
  role: implementation
  target: src/UserBundle/Action/AcceptInvitation.php
---

# Users of the inviting company delete an invitation; the invited person uses it up

An invitation ends when the company deletes it or when the person it was sent to accepts it or registers from it.
