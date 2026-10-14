---
availability:
- {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Action/Search.php
- kind: code
  role: implementation
  target: src/CoreBundle/Action/SearchSuggestions.php
- kind: code
  role: implementation
  target: src/CoreBundle/Search/MultiSearchService.php
- kind: doc
  role: intent
  target: docs/docs/using-solidinvoice/searching.md
---

# Search

Find clients, contacts, quotes, invoices, recurring invoices and payments of the current company from the search bar. Available on the hosted service, and on a self-hosted install once a search engine is configured.
