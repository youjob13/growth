## What is OpenID?

OpenID - is an open source standard which allows to create single account for multiple web sites and services using external providers. 
It allows to assert user identity without registering on each service.

*Identity Layer* is used on top of base protocol (e.g. OAuth 2.0)

| An *Identity Layer* provides:  |  |
| -----------------------------|----------|
| Who | is the user that got authenticated |
| Where | was he authenticated |
| When | was he authenticated |
| How | was he authenticated |
| What | attributes he can give you |
| Why | he is providing them |

### Interoperable

- Standard scopes - openid, profile, email, address, phone
- Method to ask for more granular claims - request object and claims
- ID Token - Info about the authenticated user
- UserInfo endpoint - get attributes about the user; translate the tokens

### Simple & Mobile Friendly

- JSON Based
- REST Friendly
- In simples cases, just copy and paste
- Mobile & App Friendly

### Secure

- ISO/IEC 29115 Entity Authentication Assurance
- Choice of crypto

### Flexible

- Granular Request - through request object JSON; data minimization
- Aggregated Claims - does not disclose data recipients to data sources
- Distributed Claims - decentralized data storage

| Signed Request | ID Token |
|----------------|----------|
| Works only with a single identity provider | Works with multiple identity providers |
| Proprietary signature format | IETF JSON Web Signature |
