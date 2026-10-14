---
domain: quotes
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Twig/Components/CreateQuote.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Manager/QuoteFormManager.php
- kind: code
  role: implementation
  target: config/packages/workflow.php
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Entity/Quote.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/QuoteTransitionProcessor.php
---

# Edit a quote

Change a quote's recipients, items, discount, taxes, terms and notes.
