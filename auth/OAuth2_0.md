## What is OAuth 2.0?

OAuth 2.0 is an open source **authorization** protocol which allows user (client) get limited access to his data on another service without sharing his login and password (via access and refresh tokens).

```md
e.g. login to site via social media account
e.g. REST API. Client attaches access token to HTTP Authorization header, Resource server validates token and returns data
```
```sh
curl -X GET https://api.example.com/profile -H "Authorization: Bearer ACCESS_TOKEN"
```

## Roles

- Resource Owner - user is giving access to his data
- Client - application (web site, mobile app) which request access
- Authorization Server - gives tokens after login check and user approval
- Resources Server - stores user data, validates tokens and returns data

## How does it work?

1. User clicks "Sign in via Google"
2. Application redirect to *Authorization Server*
3. User enter login and password
4. User approves *scopes*
5. Authorization server gives temporary *authorization code* and invokes *redirect callback*
6. Client *exchange authorization code to access token* via Authorization Server
7. Authorization server returns *access and refresh tokens*
8. Application sends access token to *Resource Server API* (via cookies or Authorization header)
9. Resource Server validates access token and returns data

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/c795278a-ff29-4318-ac45-20e59d7a40de" />

## Grant Types

| Grant Type | When to use | Recommendation |
|------------|-------------|----------------|
| Authorization Code Flow | Web applications with server side | Main safe option. Use *authorization code* + *client_secret* |
| Authorization Code + PKCE | SPA and mobile applications | Recommended for *public clients*. Protect from authorization code to be stolen |
| Client Credentials | Service-to-service (without user) | For backend integrations |
| Implicit Flow | Old SPA | Deprecated. Unsafe. Never use |
| Password Grant | Legacy systems | Not recommended. User shares password directly to client |

### Authorization Code Flow

e.g. Google OAuth, GitHub OAuth, banking integrations

OAuth tokens:

Usually OAuth tokens is a JWT tokens.

| Token | Purpose | Lifetime | Risks |
|-------|---------|----------|-------|
| Access token | Access to API (via header Authorization: Bearer ACCESS_TOKEN) | minutes / hours | When access token is stolen attackers may send request until token will be expired |
| Refresh token | Get new access token | days / months | When refresh token is stolen attackers may get new access tokens long time |

```sh
curl -X POST https://auth.example.com/token \
-d "grant_type=authorization_code" \
-d "client_id=CLIENT_ID" \
-d "client_secret=CLIENT_SECRET" \
-d "code=AUTH_CODE"
```

## Scopes

Scope is an access limitation that defines which actions allowed for application

| Scope | Permission |
|-------|------------|
| email | Read user email |
| profile | Profile access |
| read_orders | Read orders access |
| write_posts | Creating posts |
