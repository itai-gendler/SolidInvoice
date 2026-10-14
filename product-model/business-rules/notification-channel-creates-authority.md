---
appliesTo:
- type: entity
  id: notification-channel
  effect: creates
permits:
- related:
  - {verb: owns, entity: user}
references:
- kind: code
  role: implementation
  target: src/NotificationBundle/Entity/TransportSetting.php
---

# Only its owner adds a notification channel

A notification channel belongs to one User; nobody else sees or changes it.
