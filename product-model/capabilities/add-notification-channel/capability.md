---
domain: profile
availability:
- {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/NotificationBundle/Twig/Components/NotificationTransportConfiguration.php
- kind: code
  role: implementation
  target: src/NotificationBundle/Entity/TransportSetting.php
---

# Add a notification channel

Connect an SMS or chat service the User can be notified through.
