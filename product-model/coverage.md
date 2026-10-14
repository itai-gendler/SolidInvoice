---
scope: 'The invoicing application across the web, the REST API and the MCP server: accounts and companies, clients, quotes, invoices, recurring invoices, payments, taxes, custom fields, settings, exports, notifications, search and the hosted-service gates on them.'
method: Static inspection of routes, actions, live components, API resources and processors, MCP tools, workflows, listeners, scheduled commands and templates, with the user documentation as a lead.
covered:
- description: Client, contact, address and credit code.
  paths:
  - src/ClientBundle/
- description: Quote code.
  paths:
  - src/QuoteBundle/
- description: Invoice, recurring invoice, reminder and overdue code.
  paths:
  - src/InvoiceBundle/
- description: Payment and payment method code.
  paths:
  - src/PaymentBundle/
- description: Tax rate, tax identifier and tax snapshot code.
  paths:
  - src/TaxBundle/
- description: REST and GraphQL API.
  paths:
  - src/ApiBundle/
  - config/routes/api_platform.php
  - config/packages/api_platform.php
- description: MCP server, agent consent and connected apps.
  paths:
  - src/McpBundle/
- description: Accounts, sign-in, registration, two-factor authentication, invitations, profile, API tokens and onboarding.
  paths:
  - src/UserBundle/
- description: Notification settings and channels.
  paths:
  - src/NotificationBundle/
- description: Dashboard.
  paths:
  - src/DashboardBundle/
- description: List export.
  paths:
  - src/DataGridBundle/
- description: Settings and custom fields.
  paths:
  - src/SettingsBundle/
- description: Companies, shared document pages, search, data export, custom field storage, company scoping and currency freezing.
  paths:
  - src/CoreBundle/Action/
  - src/CoreBundle/Export/
  - src/CoreBundle/Search/
  - src/CoreBundle/Doctrine/Filter/
  - src/CoreBundle/Entity/
  - src/CoreBundle/Service/CustomField/
  - src/CoreBundle/Listener/FreezeCurrencyListener.php
  - src/CoreBundle/Traits/Entity/HasFrozenCurrency.php
  - src/CoreBundle/Config/SystemConfigProvider.php
- description: Document state machines, routes, access control and feature switches.
  paths:
  - config/packages/workflow.php
  - config/packages/security.php
  - config/packages/toggler.php
  - config/routes.php
- description: Hosted-service gates on invoices, recurring invoices, the API and MCP.
  paths:
  - src/SaasBundle/EventSubscriber/RecurringInvoiceFeatureGuardListener.php
  - src/SaasBundle/EventSubscriber/RecurringInvoiceVerificationGuardListener.php
  - src/SaasBundle/Security/Voter/SubscriptionVoter.php
- description: Email settings.
  paths:
  - src/MailerBundle/Config/ConfigProvider.php
exclusions:
- description: 'Build, packaging and deployment: how SolidInvoice is shipped, not how it is used.'
  paths:
  - docker/
  - helm/
  - packaging/
  - frankenphp/
  - scripts/
  - bin/
  - docker-bake.hcl
  - docker-compose.yml
  - Caddyfile
- description: 'Front-end assets and document designs: look and layout, which the model leaves to design.'
  paths:
  - assets/
  - public/
  - templates/
  - src/InvoiceBundle/Resources/views/Templates/
  - src/QuoteBundle/Resources/views/Templates/
- description: 'Database migrations: storage history, not behavior.'
  paths:
  - migrations/
- description: 'Documentation site: read as a lead, not product code.'
  paths:
  - docs/
- description: 'Anonymous usage telemetry: reporting to the maintainers, not a feature people use.'
  paths:
  - src/CoreBundle/Telemetry/
- description: 'Demo data loading: development tooling.'
  paths:
  - src/CoreBundle/Command/LoadDummyDataCommand.php
- description: 'Mail transport plumbing and the cron runner: infrastructure behind modelled emails and schedules.'
  paths:
  - src/MailerBundle/Configurator/
  - src/MailerBundle/Factory/
  - src/CronBundle/
- description: Repository-level tests and tooling.
  paths:
  - tests/
  - mate/
  - ai/
unmapped:
- description: 'Hosted-service subscriptions, plans, trials and onboarding emails: billing for the hosted offering itself, not the product people use to bill.'
  paths:
  - src/SaasBundle/Action/
  - src/SaasBundle/Controller/
  - src/SaasBundle/Onboarding/
  - src/SaasBundle/Service/
  - src/SaasBundle/Plan/
- description: 'Hosted plan gates on quotes, online payments, multi-currency, branding, templates, custom domains and custom fields: plan packaging of behavior the model already describes.'
  paths:
  - src/SaasBundle/Feature/
- description: 'Hosted email-verification gate on emails to clients: it governs sending emails, which the format records as reads, not as an operation a grant can hold.'
  paths:
  - src/SaasBundle/Email/SaasEmailVerificationGate.php
- description: 'Installation wizard: one-time setup by whoever operates an install.'
  paths:
  - src/InstallBundle/
- description: 'Deleting a company: an account-administration step outside daily billing, described in the user documentation.'
  paths:
  - src/CoreBundle/Action/DeleteCompany.php
- description: 'Hand-off from registration into onboarding: the person is signed in partway, which a Journey cannot express.'
  paths:
  - src/UserBundle/Onboarding/EventSubscriber/OnboardingLoginListener.php
- description: 'Dashboard onboarding checklist: a dismissible helper beside the dashboard.'
  paths:
  - src/DashboardBundle/Checklist/
limitations:
- description: Cloning a recurring invoice from the web and the MCP server.
  paths:
  - src/InvoiceBundle/Action/CloneRecurringInvoice.php
  - src/InvoiceBundle/Cloner/InvoiceCloner.php
- description: Activating an archived recurring invoice from the Archived tab.
  paths:
  - src/InvoiceBundle/DataGrid/ArchivedRecurringInvoiceGrid.php
- description: Deleting a tax rate and recalculating documents that used it.
  paths:
  - src/TaxBundle/Repository/TaxRepository.php
  - src/InvoiceBundle/Repository/LineRepository.php
- description: Invoice cancellation and acceptance listeners.
  paths:
  - src/InvoiceBundle/Listener/InvoiceCancelListener.php
  - src/InvoiceBundle/Listener/Mailer/InvoiceMailerListener.php
- description: Converting a quote to an invoice through the API and MCP server, beside acceptance.
  paths:
  - src/ApiBundle/State/Processor/QuoteToInvoiceProcessor.php
---

# Coverage
