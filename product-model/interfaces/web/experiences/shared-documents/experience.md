---
actors:
- contact
access: public
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Action/ViewBilling.php
- kind: code
  role: implementation
  target: config/packages/security.php
---

# Shared documents

The pages a client's Contact reaches from the link in a quote or invoice email, without an account: the quote or invoice itself, its PDF, and the payment page of an invoice.
