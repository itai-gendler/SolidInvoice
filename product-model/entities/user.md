---
kind: person
acts: external
relations:
- {entity: company, verb: belongs-to, cardinality: many-to-many}
- {entity: ai-agent, verb: connects, cardinality: one-to-many}
- {entity: api-token, verb: owns, cardinality: one-to-many}
- {entity: notification-channel, verb: owns, cardinality: one-to-many}
- {entity: data-export, verb: requests, cardinality: one-to-many}
references:
- kind: code
  role: implementation
  target: src/UserBundle/Entity/User.php
- kind: code
  role: implementation
  target: src/CoreBundle/Action/CreateCompany.php
- kind: doc
  role: context
  target: docs/docs/using-solidinvoice/user-profile.md
---

# User

A person with an account who belongs to one or more companies and runs their billing. Everyone in a company has the same abilities there.

## Information kept

- **Name** — the person's first and last name
- **Email** — the address the person signs in with and receives notifications at
- **Email verified** — whether the person has confirmed their email address
- **Mobile** — an optional mobile number
- **Password** — the password the person signs in with
- **Google account** — the Google identity linked to the account, if any
- **Email authentication** — whether a code sent by email is asked for at sign-in
- **Authenticator app** — whether a code from an authenticator app is asked for at sign-in
- **Backup codes** — single-use codes that replace a second-factor code
- **Trusted device** — a device on which the second factor is not asked for 30 days
- **Notification preferences** — for each event, which channels notify the person: email and their own notification channels
- **Companies** — the companies the person belongs to
- **Onboarding** — whether the person has completed or dismissed the guided setup
