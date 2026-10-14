---
kind: alternative
routes:
  web: Web
steps:
- text: The Visitor chooses Login with Google and approves at Google
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::sign-in::sign-in-page'}
- text: The Product signs in the account linked to that Google identity, or the account with the same email after linking it
  kind: product
  actor: visitor
  entities:
  - {entity: user, effect: changes, facts: [Google account]}
  contexts:
    web: {place: 'web::sign-in::sign-in-page'}
---

# Sign in with Google

## Trigger

Someone prefers their Google account.

## Outcome

The person is signed in.

## Edge cases

- Without a matching account, a new account is created while registration is allowed; otherwise sign-in is refused.
