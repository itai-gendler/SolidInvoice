---
kind: person
acts: external
domain: clients
references:
- kind: code
  role: implementation
  target: src/ClientBundle/Entity/Contact.php
- kind: code
  role: implementation
  target: src/ClientBundle/Form/Type/ContactType.php
- kind: doc
  role: context
  target: docs/docs/managing-clients/viewing-a-client.md
---

# Contact

A person at a client who receives the quotes, invoices and reminders they are chosen for, and who opens and pays them from the emailed link without an account.

## Information kept

- **First name** — the contact's first name
- **Last name** — the contact's last name
- **Email** — where documents and reminders are sent
- **Additional contact details** — further typed ways to reach the contact, such as phone or mobile
- **Custom field values** — values for the company's contact custom fields
