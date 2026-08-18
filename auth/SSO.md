## What is SSO mean?

SSO (Single Sign-On) - single authentication mechanism. User enters once and receives access to all related services without enters credentials again.

SSO is a centralized way to manage access via Identity Provider (IdP).

## How does SSO work?

*SP* - Service Provider
*IdP* - Identity Provider

| Step | What happens | Members |
|------|--------------|---------|
| 1 | User opens an app (e.g. CRM) | User -> SP |
| 2 | SP redirects request to the IdP | SP -> IdP |
| 3 | User enters login/password (MFA) | User -> IdP |
| 4 | IdP validates data and issues token (JWT/SAML Assertion) | IdP |
| 5 | A token is returned to the app via secure chanel | IdP -> SP |
| 6 | The app validates the token signature and opens access | SP |
| 7 | When opens another app, repeated login is not required | User -> another SP |
