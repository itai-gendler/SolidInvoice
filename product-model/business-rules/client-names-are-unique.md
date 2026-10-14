---
appliesTo:
- type: capability
  id: create-client
- type: capability
  id: edit-client
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Validator/Constraints/UniqueClientNameValidator.php
- kind: code
  role: implementation
  target: src/ClientBundle/Repository/ClientRepository.php
---

# Client names are unique within a company, archived clients included

Adding or renaming a client to a name another client of the company has, even an archived one, is refused.
