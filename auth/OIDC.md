## What is the OIDC?

OpenID Connect (OIDC) - is a full-fledged **authentication** and **authorization** (OAuth 2.0) protocol for asserting user identity. It extends OAuth 2.0 (authorization protocol). OIDC works on top of OAuth 2.0

OIDC uses an identity token (user info: username, email etc.) and access token (user access info: user roles, groups etc.).

OIDC verify if user is the right user (not impersonated user)

## Two use cases of OIDC

1. Authenticate user to use the application
2. app1 can request app2 API on behalf of the user

## OIDC components

- Identity validation
- Client - software (website or application) that requesting tokens for identity validation or resource access
- ID Token - contains data, including result of the identity validation, user id and date when the user asserted identity check
- Access Token - contains user access info: user roles, groups etc.
- OpenID Provider - applications that already have user account. Provider validates user identity and shares this info with validating side.
- Users - users or services which try to receive access to the application without creating new account

<img width="1258" height="701" alt="image" src="https://github.com/user-attachments/assets/21a07bbb-88cc-4a0b-994a-f3ab11b758ff" />

## OIDC Auth Flows

