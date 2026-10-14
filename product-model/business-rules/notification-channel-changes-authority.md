---
appliesTo:
- type: entity
  id: notification-channel
  effect: changes
permits:
- related:
  - {verb: owns, entity: user}
references:
- kind: code
  role: implementation
  target: src/NotificationBundle/Entity/TransportSetting.php
---

# Only its owner changes a notification channel

A notification channel belongs to one User; nobody else sees or changes it.
