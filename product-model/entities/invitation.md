---
references:
- kind: code
  role: implementation
  target: src/UserBundle/Entity/UserInvitation.php
---

# Invitation

An emailed invitation for someone to join a company.

## Information kept

- **Email** — who is invited
- **Expires at** — when the invitation stops working

## States

### Pending

Sent and waiting to be accepted.

### Expired

Past its expiry without being accepted.
