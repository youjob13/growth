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

### Authorization Code Flow

This is recommended browser-based protocol.

1. Browser visits app. The app redirects (with redirect URL query parameter) to the Keycloak to be authenticated.
2. Keycloak authenticates the user and create one-time very short lived temporary **authorization code**. Keycloak redirects back to the app using the provided redirect URL and additionally adds the temporary code as query parameter.
3. The app extracts the temporary code and makes a background out of band REST invocation to Keycloak to exchange the authorization code for an *identity*, *access* and *refersh* tokens.

**NOTE**: Authorization Code Flow can be used with both a *confidential* and a *public* clients

| Client type | Description |
|-------------|-------------|
| Confidential client | Are required to provide a *client secret* when they exchange the temporary authorization code for tokens. Confidential client still may use PKCE for additional security |
| Public client | Are not required to provide this client secret. There is no way to safely store client secret for public clients. Public client must use PKCE |

#### PKCE (Proof Key for Code Exchange)

PKCE is designed to prevent authorization code interception and injection attacks. (HELPS OpenID Provider to identify Client) It ensures that only the client that requested the authorization code can use it. PKCE allows public clients (mobile and SPA) to use the Authorization Code Flow securely.

Request with PKCE must contain *code_challenge* and *code_challenge_method*.

1. Before making the request, the client generates a high-entropy cryptographic random string known as the *code_verifier*. 
2. The *code_challenge* is then derived by hashing the *code_verifier* using the specified *code_challenge_method*.
3. *code_challnge* is sent with the initial authorization request, ensuring that the *code_verifier* is used later to prove that the true originator of the authorization request is asking for a token in exchange for the authorization code.

### Implicit Flow

This is browser-based protocol (not recommended, less secure)

1. Browser visits app. The app redirects (with redirect URL query parameter) to the Keycloak to be authenticated.
2. Keycloak authenticates the user and creates *identity* and *access* tokens. Keycloak redirects back to the app using the provided redirect URL and additionally adds the *identity* and *access* tokens as query parameters.
3. The app extracts the *identity* and *access* tokens from the URL.

### Resource Owner Password Credentials Grant (Direct Access Grants)

This is used by REST clients that want to obtain a token on behalf of a user.

1. It's one **HTTP POST** request that contains the credentials of the user as well as the id of the client and the client's secret (if it's a confidential client).
2. The HTTP response contains *identity*, *access* and *refresh* tokens.

### Client Credentials Grant

This is used by REST clients.

The main difference from the Direct Access Grant is that token is created based on the metadata and permissions of a *service account* that is associated with the client (not on behalf of a user).
