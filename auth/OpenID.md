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

| Signed Request | ID Token |
|----------------|----------|
| Works only with a single identity provider | Works with multiple identity providers |
| Proprietary signature format | IETF JSON Web Signature |
