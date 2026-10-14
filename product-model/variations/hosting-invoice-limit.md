---
kind: configuration
of: business-rule
takesEffect: Fixed by how SolidInvoice is deployed, before anyone uses it. On the hosted service the limit is checked each time an invoice is created, against the plan the company has at that moment.
stability: An install does not move between the two. A hosted company whose plan changes is held to the new plan's limit from its next invoice; invoices already created are unaffected.
alternatives:
- id: invoice-creation-self-hosted
  selectedWhen: Selected when the install runs as the self-hosted product, the default for every download, package, container and binary.
- id: invoice-creation-hosted
  selectedWhen: Selected when the install runs as the hosted SolidInvoice service, where companies subscribe to plans.
references:
- kind: code
  role: implementation
  target: src/SaasBundle/SolidInvoiceSaasBundle.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Validator/Constraints/WithinPlanInvoiceLimitValidator.php
- kind: doc
  role: context
  target: README.md
---

# Invoice limit by hosting

The same codebase runs self-hosted and as the hosted service; only the hosted service limits how many invoices a company creates each month, according to its plan.
