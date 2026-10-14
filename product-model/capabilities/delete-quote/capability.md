---
domain: quotes
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/DataGrid/BaseQuoteGrid.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Repository/QuoteRepository.php
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

# Delete a quote

Remove quotes permanently.
