---
id: solidinvoice
summary: 'Open-source invoicing for freelancers and small businesses: clients, quotes, invoices, recurring invoices, taxes and online payments.'
category: invoicing
tags:
- invoicing
- billing
- self-hosted
authors:
- name: SolidInvoice
  url: https://github.com/SolidInvoice/SolidInvoice
license: MIT
languages:
- en
limitations:
- Everyone who belongs to a company works with all of that company's clients, quotes, invoices and settings; there are no roles inside a company.
- Card details are entered at the payment gateway a company connects; SolidInvoice keeps no card data.
- 'Amounts are never converted between currencies: each client is billed in one currency and totals stay per currency.'
- A client's credit is one running balance; individual adjustments are not kept as a history.
- Overdue reminders follow a fixed schedule of 1, 7 and 14 days after the due date.
references:
- kind: doc
  role: context
  target: README.md
- kind: doc
  role: context
  target: PRODUCT.md
- kind: doc
  role: context
  target: docs/docs/intro.mdx
---

# SolidInvoice

SolidInvoice runs a small business's billing. People in a company keep their clients and each client's contacts, prepare quotes and invoices with line items, taxes and discounts, and email them to the contacts they choose. Contacts open the documents from the email without an account and pay invoices online through the gateways the company connects. Accepted quotes become invoices, recurring invoices issue new invoices on a schedule, and invoices move through draft, pending, overdue and paid on their own state machine, with tax rates and currency fixed when a document is issued and reminders sent as due dates pass. The same billing is open to integrations through a REST API and to AI agents through a built-in MCP server, each bound to one company.

## Intent

SolidInvoice is open-source, self-hostable invoicing for freelancers and small businesses who do not want enterprise accounting software. Its job is to get them paid faster with less friction: an invoice goes out in under a minute, a payment is recorded without ambiguity, and the totals can be trusted, while the business keeps ownership of its data.
