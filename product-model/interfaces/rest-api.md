---
type: api
actors:
- user
references:
- kind: code
  role: implementation
  target: config/routes/api_platform.php
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: doc
  role: context
  target: docs/docs/api/rest-api.md
---

# REST API

The HTTP API at `/api` that mirrors the web application for integrations: clients and their contacts, addresses and tax identifiers, quotes, invoices, recurring invoices, payments, tax rates, custom fields and the User's API tokens. The same resources can also be queried and changed through GraphQL at `/api/graphql`. Every request carries a User's API token and acts as that User in the one company the token was created in.
