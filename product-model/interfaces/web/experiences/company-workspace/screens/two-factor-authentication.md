---
entities:
- entity: user
  shows:
  - Email authentication
  - Authenticator app
  - Backup codes
  - Trusted device
references:
- kind: code
  role: implementation
  target: src/UserBundle/Twig/Components/TwoFactorSettings.php
---

# Two-factor authentication

The User's second-factor methods, backup codes and trusted device.
