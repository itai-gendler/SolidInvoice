---
entities:
- entity: tax-identifier
  shows: &id001
  - Type
  - Number
  - Primary
  collects: *id001
- entity: company
  shows:
  - Name
  - Currency
  collects:
  - Name
  - Currency
  - Logo
  - Address
  - Email address
  - Phone number
  - Sender name
  - Sender address
  - Mail delivery
  - Default payment terms
  - Invoice number format
  - Invoice email subject
  - Invoice BCC address
  - Invoice watermark
  - Automatic reminders
  - Pre-due reminders
  - Pre-due reminder days
  - Quote number format
  - Quote email subject
  - Quote BCC address
  - Quote watermark
references:
- kind: code
  role: implementation
  target: src/SettingsBundle/Action/Index.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Config/ConfigProvider.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Config/ConfigProvider.php
---

# Settings

The company's settings: company details and tax identifiers, invoices, quotes and email.
