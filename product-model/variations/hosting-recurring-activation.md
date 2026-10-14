---
kind: configuration
of: business-rule
takesEffect: Fixed by how SolidInvoice is deployed. On the hosted service the plan and the User's email verification are checked each time a recurring invoice is activated.
stability: An install does not move between the two. On the hosted service, recurring invoices already active keep running when the check would now fail; only new activations are blocked.
alternatives:
- id: recurring-activation-self-hosted
  selectedWhen: Selected when the install runs as the self-hosted product, the default for every download, package, container and binary.
- id: recurring-activation-hosted
  selectedWhen: Selected when the install runs as the hosted SolidInvoice service.
references:
- kind: code
  role: implementation
  target: src/SaasBundle/SolidInvoiceSaasBundle.php
- kind: code
  role: implementation
  target: src/SaasBundle/EventSubscriber/RecurringInvoiceFeatureGuardListener.php
---

# Recurring activation by hosting

Self-hosted installs let any User activate recurring billing; the hosted service makes it part of a plan and requires a verified email first.
