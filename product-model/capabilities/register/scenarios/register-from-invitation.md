---
kind: alternative
routes:
  web: Web
steps:
- text: The Visitor follows an invitation and chooses a password; the email is the invited one
  kind: actor
  actor: visitor
  entities:
  - {entity: invitation, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'web::sign-in::registration'}
- text: The Product creates the account in the inviting company and uses up the invitation
  kind: product
  actor: visitor
  entities:
  - {entity: user, effect: creates, facts: [Email, Password, Email verified, Companies]}
  - {entity: invitation, effect: removes, from: Pending}
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::sign-in::registration'}
---

# Register from an invitation

## Trigger

An invited person has no account yet.

## Outcome

The person has an account in the company that invited them and skips onboarding.
