---
entities:
- entity: user
  shows:
  - Notification preferences
  collects:
  - Notification preferences
- entity: notification-channel
  shows:
  - Name
  - Service
  collects:
  - Name
  - Service
  - Settings
references:
- kind: code
  role: implementation
  target: src/UserBundle/Twig/Components/UserNotification.php
- kind: code
  role: implementation
  target: src/NotificationBundle/Twig/Components/NotificationTransportConfiguration.php
---

# Notification settings

Which events notify the User and through which channels, and the User's own SMS and chat channels.
