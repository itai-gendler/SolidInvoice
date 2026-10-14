---
domain: profile
availability:
- {place: 'web::sign-in'}
references:
- kind: code
  role: implementation
  target: src/UserBundle/Action/Security/VerifyEmail.php
- kind: doc
  role: intent
  target: docs/docs/using-solidinvoice/email-verification.md
---

# Verify an email address

Confirm an account's email address through the emailed link.
