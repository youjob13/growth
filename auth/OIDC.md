## What is the OIDC?

OpenID Connect (OIDC) - is a protocol for asserting user identity.
It extends OAuth 2.0.

OIDC verify if user is the right user (not impersonated user)

## OIDC components

- Identity validation
- Client - software (website or application) that requesting tokens for identity validation or resource access
- ID Token - contains data, including result of the identity validation, user id and date when the user asserted identity check
- OpenID Provider - applications that already have user account. Provider validates user identity and shares this info with validating side.
- Users - users or services which try to receive access to the application without creating new account
