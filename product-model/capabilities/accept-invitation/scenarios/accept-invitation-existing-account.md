---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor follows the invitation link
  kind: actor
  actor: visitor
  entities:
  - {entity: invitation, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'web::sign-in'}
- text: The Product adds the inviting company to the account with that email and uses up the invitation
  kind: product
  actor: visitor
  entities:
  - {entity: user, effect: changes, facts: [Companies]}
  - {entity: invitation, effect: removes, from: Pending}
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::sign-in'}
- text: The Product asks the person to sign in
  kind: product
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::sign-in::sign-in-page'}
---

# Accept an invitation with an existing account

## Trigger

An invited person already has an account.

## Outcome

The person belongs to the inviting company too.

## Edge cases

- Without an account for that email, the person is taken to registration from the invitation.
