---
appliesTo:
- type: capability
  id: send-invoice
- type: capability
  id: send-quote
- type: capability
  id: send-payment-reminder
- type: capability
  id: send-automatic-payment-reminders
- type: capability
  id: create-invoice
- type: capability
  id: create-quote
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Listener/Mailer/InvoiceReceiverListener.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Listener/Mailer/QuoteReceiverListener.php
- kind: code
  role: implementation
  target: src/InvoiceBundle/Listener/Mailer/ReminderReceiverListener.php
---

# Document emails and reminders go to the contacts chosen on the document

Each quote, invoice and recurring invoice names the client contacts it is sent to; emails and reminders go to those contacts, plus the company's BCC address for invoice and quote emails when one is set. With no contacts chosen, nothing is sent.
