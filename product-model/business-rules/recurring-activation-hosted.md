---
appliesTo:
- type: entity
  id: recurring-invoice
  effect: changes
  from: Draft
  to: Active
permits:
- related:
  - {verb: keeps, entity: company}
  - {verb: belongs-to, entity: user}
  when:
  - entity: company
    fact: Plan includes recurring invoices
    is: 'Yes'
  - entity: user
    fact: Email verified
    is: 'Yes'
references:
- kind: code
  role: implementation
  target: src/SaasBundle/EventSubscriber/RecurringInvoiceFeatureGuardListener.php
- kind: code
  role: implementation
  target: src/SaasBundle/EventSubscriber/RecurringInvoiceVerificationGuardListener.php
---

# On the hosted service, only a user with a verified email activates a recurring invoice, and only on a plan that includes recurring invoices

Activating a draft recurring invoice is blocked while the company's plan does not include recurring invoices or the User has not verified their email address. Save and Enable on a new recurring invoice goes through the same check.
