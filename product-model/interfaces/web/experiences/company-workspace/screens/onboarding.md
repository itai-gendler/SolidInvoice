---
entities:
- entity: company
  collects:
  - Name
  - Currency
- entity: client
  collects:
  - Name
- entity: contact
  collects:
  - Email
- entity: invoice
  collects:
  - Line items
references:
- kind: code
  role: implementation
  target: src/UserBundle/Onboarding/Action/Onboarding.php
- kind: code
  role: implementation
  target: src/UserBundle/Onboarding/Manager/OnboardingManager.php
---

# Onboarding

The guided setup a new User goes through: their company, a first client and a first invoice.
