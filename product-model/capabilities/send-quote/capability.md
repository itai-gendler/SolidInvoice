---
domain: quotes
availability:
- {place: 'web::company-workspace'}
- {place: rest-api}
- {place: mcp}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Action/Transition/Send.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Mailer/QuoteMailer.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Listener/WorkFlowSubscriber.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Listener/Mailer/QuoteReceiverListener.php
- kind: code
  role: implementation
  target: src/ApiBundle/Security/ApiTokenAuthenticator.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Entity/Quote.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/QuoteTransitionProcessor.php
- kind: code
  role: implementation
  target: src/McpBundle/Mcp/McpScopeGuard.php
- kind: code
  role: implementation
  target: src/QuoteBundle/Mcp/QuoteWriteTools.php
---

# Send a quote

Email a quote to the contacts chosen on it.
