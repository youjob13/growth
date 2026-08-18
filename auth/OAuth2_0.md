## What is OAuth 2.0?

OAuth 2.0 is an open source **authorization** protocol which allows user (client) get limited access to his data on another service without sharing his login and password (via access and refresh tokens).

```md
e.g. login to site via social media account
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
