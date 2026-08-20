## What is SAML mean?

SAML 2.0 is a similar specification to OIDC but a lot older and more mature.

SAML 2.0 is primarily an authentication protocol that works by exchanging XML documents between the authentication server and the application.

## SAML Bindings

SAML defines a few different ways to exchange XML documents when executing the authentication protocol. The Redirect and POST bindings cover browser based applications.
The ECP binding covers REST invocations.
There are other binding types also.

### Redirect Binding

1. The user visits the app and the app finds the user is not authenticated. It generates an XML authentication request document and encodes it as a query param in a URI that is used to redirect to the Keycloak server.
XML document can be digitally sign to validate the client that sent this request.
2. The browser is redirected to OdP (e.g. Keycloak). The server extracts the XML auth request document and verifies the digital signature if required. The user enters credentials.
3. After authentication, the server generates an XML authentication response document. This document contains a SAML assertion that holds metadata about the user like name, address, email and role mappings. This document digitally signed using XML signature and may be encrypted
4. The XML auth response document is then encoded as a query param in a redirect URI that brings the browser back to the app. The digital signature is also included as a query param.
5. The app receives the redirect URI and extract the XML document and verifies the realm's signature to make sure it is receiving a valid auth response. The info inside the SAML assertion is then used to make access decisions or display user data.

### POST Binding

The SAML *POST* binding works almost the exact same way as the *Redirect* binding.
But instead of GET requests, XML documents are exchanged by POST requests.
The *POST* Binding uses JavaScript to trick the browser into making a POST request to the Keycloak server or application when exchanging documents.

### ECP

ECP stands for "Enhanced Client or Proxy" a SAML v2.0 profile which allows for the exchange of SAML attributes outside the context of a web browser.
