---
relations:
- {entity: client, verb: keeps, cardinality: one-to-many}
- {entity: quote, verb: keeps, cardinality: one-to-many}
- {entity: invoice, verb: keeps, cardinality: one-to-many}
- {entity: recurring-invoice, verb: keeps, cardinality: one-to-many}
- {entity: tax-rate, verb: keeps, cardinality: one-to-many}
- {entity: payment-method, verb: keeps, cardinality: one-to-many}
- {entity: tax-identifier, verb: holds, cardinality: one-to-many}
- {entity: custom-field, verb: keeps, cardinality: one-to-many}
- {entity: invitation, verb: keeps, cardinality: one-to-many}
- {entity: ai-agent, verb: authorizes, cardinality: one-to-many}
- {entity: api-token, verb: keeps, cardinality: one-to-many}
- {entity: data-export, verb: keeps, cardinality: one-to-many}
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Entity/Company.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Config/ConfigProvider.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Config/ConfigProvider.php
- kind: code
  role: implementation
  target: src/TaxBundle/Entity/TaxIdentifier.php
- kind: doc
  role: context
  target: docs/docs/companies/overview.md
---

# Company

A self-contained workspace: its clients, documents, payments, tax rates, payment methods and settings are never visible from another company. Its settings decide how invoices and quotes are numbered, emailed and reminded.

## Information kept

- **Name** — the business name printed on its quotes and invoices
- **Currency** — the default currency for clients that have no currency of their own
- **Logo** — the image shown on its documents and emails
- **Address** — the business address printed on its documents
- **Email address** — the business contact email printed on its documents
- **Phone number** — the business phone number printed on its documents
- **Sender name** — the name emails to clients are sent from
- **Sender address** — the address emails to clients are sent from
- **Mail delivery** — how the company's emails are delivered
- **Default payment terms** — the payment terms new invoices start with when the client has none; Net 30 unless changed
- **Invoice number format** — how invoice numbers are generated, with an optional prefix and suffix
- **Invoice email subject** — the subject of invoice emails, where {id} stands for the invoice number
- **Invoice BCC address** — an address that receives a copy of every invoice email
- **Invoice watermark** — whether invoices show their status as a watermark
- **Automatic reminders** — whether automatic payment reminders are sent at all
- **Pre-due reminders** — whether a reminder is sent before an invoice falls due
- **Pre-due reminder days** — how many days, 0 to 30, before the due date the pre-due reminder is sent; 3 unless changed
- **Quote number format** — how quote numbers are generated, with an optional prefix and suffix
- **Quote email subject** — the subject of quote emails, where {id} stands for the quote number
- **Quote BCC address** — an address that receives a copy of every quote email
- **Quote watermark** — whether quotes show their status as a watermark
- **Plan includes recurring invoices** — on the hosted service, whether the company's plan includes recurring invoices
- **Monthly invoice limit** — on the hosted service, how many invoices the company's plan allows it to create in a calendar month
- **Invoices created this month** — how many invoices the company has created in the current calendar month
- **Plan includes REST API** — on the hosted service, whether the company's plan includes the REST API
- **Plan includes MCP** — on the hosted service, whether the company's plan includes connecting AI agents
