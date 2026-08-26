## What is CSP mean?

CSP (Content Security Policy) is a feature that helps to prevent or minimize the risk of certain types of security threats.
CSP is a series of instructions from a website to a browser, which instruct the browser to place restrictions on the things that the code comprising the site is allowed to do.

The primary use case for CSP is to control which resources, in particular JavaScript resources a document is allowed to load.
This is mainly used as a defense against XSS (cross-site scripting) attacks in which an attacker is able to inject malicious code into the victim's site and clickjacking in which attacker creates a decoy site which embeds the user's target side inside an iframe and when user interact with decoy elements they are inadvertently interacting with the target site instead.
