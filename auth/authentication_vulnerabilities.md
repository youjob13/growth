## Common Attack Vectors

| Vulnerability | Description | Protection mechanism |
|---------------|-------------|----------------------|
| XSS (Cross-Site Scripting) attacks | Involve injection malicious JavaScript code into an application through input fields, URL parameters or other entry points. | Escape and sanitize input data |
| CSRF (Cross-Site Request Forgery) | Occurs when malicious scripts or browser extensions perform actions on behalf of the user without their consent. Scripts can use the user's session and credentials to carry out unauthorized actions | |
| Dependency Compromise | Occurs when modern web applications rely on numerous external libraries and resources | |
| Browser extension vulnerabilities | Arise when browser extensions, which have access to web app code and user data, are compromised or malicious. | 
| Authorization Code Interception Attack | Occurs when an attacked intercepts authorization codes exposed in the URL during the redirect | |
| Persistent Token Theft | Is a risk when tokens are stored within the browser's storage, making them susceptible to continuous theft by malicious scripts | Do not store tokens in browser storages |
| Acquisition and Extraction of New Tokens | Occurs when a session is active on the OpenID Provider side and malicious JavaScript initiates a silent authentication process in a hidden iframe to obtain new access tokens without the user's knowledge | |
| Proxying Requests via the User's Browser | Occurs when malicious JavaScript exploits an authenticated session by simulating user actions within the app, sending unauthorized requests to the Protected Resource on behalf of the user. | |
