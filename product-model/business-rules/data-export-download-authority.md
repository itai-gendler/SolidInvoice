---
appliesTo:
- type: entity
  id: data-export
  effect: reads
  facts:
  - Archive
permits:
- related:
  - {verb: requests, entity: user}
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Export/Security/Voter/ExportJobVoter.php
---

# Only the User who requested an export downloads it

An export is downloaded only by the User who asked for it, while that company is the active one.
