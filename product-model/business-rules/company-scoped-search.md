---
appliesTo:
- type: capability
  id: search-records
  contexts:
  - {place: 'web::company-workspace'}
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Search/MultiSearchService.php
---

# Search finds only records of the active company

Records of the User's other companies never appear in results.
