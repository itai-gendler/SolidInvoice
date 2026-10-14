---
references:
- kind: code
  role: implementation
  target: src/NotificationBundle/Entity/TransportSetting.php
- kind: code
  role: implementation
  target: src/NotificationBundle/Twig/Components/NotificationTransportConfiguration.php
---

# Notification channel

A User's own connection to an SMS or chat service, such as Discord or an SMS gateway, through which the Product can notify them.

## Information kept

- **Name** — the name the User gives it
- **Service** — the SMS or chat service
- **Settings** — the credentials and options the service needs
