---
domain: invoices
availability:
- {place: 'web::shared-documents'}
- {place: 'web::company-workspace'}
- {place: rest-api}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/PaymentBundle/Action/Prepare.php
- kind: code
  role: implementation
  target: src/PaymentBundle/Action/Done.php
- kind: code
  role: implementation
  target: src/PaymentBundle/Listener/PaymentCompleteListener.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Listener/InvoicePaidListener.php
- kind: doc
  role: intent
  target: docs/docs/managing-clients/client-credit.md
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/RecordPaymentProcessor.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/McpScopeGuard.php
- kind: code
  role: implementation
  target: src/PaymentBundle/Mcp/PaymentWriteTools.php
---

# Pay an invoice

Pay a pending or overdue invoice in full or in part: online by the client's contact, or recorded by a User with any method, including the client's credit.
