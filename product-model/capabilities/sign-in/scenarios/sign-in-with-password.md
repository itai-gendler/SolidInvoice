---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor enters their email and password
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::sign-in::sign-in-page'}
- text: The Product finds the account and the password matches
  kind: condition
  actor: visitor
  entities:
  - {entity: user, effect: reads, facts: [Email, Password]}
  contexts:
    web: {place: 'web::sign-in::sign-in-page'}
- text: The Product signs the person in and takes them to their company, or to the company picker when they have several
  kind: product
  actor: visitor
  entities:
  - {entity: user, effect: reads, facts: [Companies]}
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::sign-in::sign-in-page'}
---

# Sign in with email and password

## Trigger

Someone with an account wants to work.

## Outcome

The person is signed in.
