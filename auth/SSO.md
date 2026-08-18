## What is SSO mean?

SSO (Single Sign-On) - single authentication mechanism. User enters once and receives access to all related services without enters credentials again.

SSO is a centralized way to manage access via Identity Provider (IdP).

SSO is a part of the IAM-architecture (Identity and Access Management).

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

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/b1f20bf3-cb60-4bdd-8eca-d7b2f0cacb54" />

## What is IAM mean?

IAM (Identity and Access Management) - complex system is responsible for:
- Identification - who (accounts, catalogs)
- Authentication - identity assertion (password, MFA, SSO)
- Authorization - what allowed (roles, policy)
- Lifecycle management - creating, blocking, deleting accounts

| IAM component | Function |
|---------------|----------|
| SSO | single enter, token issuing |
| MFA | multi factor protection |
| RBAC | roles and access policy |
| Policy Engine | access rules |
| Directory (AD/LDAP) | stores accounts |

## Identity Federation

Identity Federation - is a trust mechanism between different Identity Providers. It allows user from one organization accesses another organization applications without creating new account.

Identity Federation can be implemented via SAML 2.0 metadata, OIDC federation, mutual SSL/TLS.

| Scenario | Result |
|----------|--------|
| Company A uses Keycloak, company B - Azure AD | Federation -> employees A enters into services B via their accounts |
| United Corporative Group | Single endpoint via IdP Federation |
| B2B-portal | Partners enter without new password registration |

## SSO protocols: SAML, OAuth, OpenID Connect

| Protocol | Purpose | Data Format | Use case |
|----------|---------|-------------|----------|
| SAML 2.0 | Enterprise SSO (authentication + authorization ) | XML (Assertion) | Corporative web-applications, Active Directory, goverment |
| OAuth 2.0 | API access delegating | JSON / Bearer Token | Sign in via Google |
| OpenId Connect (OIDC) | Authentication on top of OAuth 2.0 | JWT (ID Token) | Modern SPA, mobile apps |

## SSO-session lifecycle

| Step | Description |
|------|-------------|
| Login | User enters login/password + MFA |
| Token issuance | IdP issues token (JWT, SAML Assertion) |
| Active session | User works with apps |
| Refresh | Updates the token without new login (refresh token) |
| Revocation | Administrator revokes the access or expiration happens |
| Logout | Session Logout |

## Failure Modes and solutions

| Problem | Consequence | Solution |
|---------|-------------|----------|
| IdP unavailable | All services crashing | Clustering, backup, offline-tokens |
| Token expired | Immediately access loosing | Auto update via refresh token |
| Clock skew | SAML Assertion errors | Time sync (NTP), range 2-5 mins |
| IdP certificate expired | Token signature issue | Certificates auto rotation |
| MFA unavailable | User blocked | Fallback MFA (backup method or temporary turning off with logging) |

## Security recommendations

- MFA - (TOTP, push-notification, security keys) - reduce compromise risk on 99%
- Short token lifetime
- Conditional Access - access only from trusted devices and via geolocation
- Logins and revocation audit - centralized logging system
- Backup IdP or cached sessions for offline-access
