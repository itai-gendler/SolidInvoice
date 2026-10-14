---
appliesTo:
- type: entity
  id: notification-channel
  effect: removes
permits:
- related:
  - {verb: owns, entity: user}
references:
- kind: code
  role: implementation
  target: src/NotificationBundle/Entity/TransportSetting.php
---

# Only its owner deletes a notification channel

A notification channel belongs to one User; nobody else sees or changes it.
