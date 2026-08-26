## What is stand for XSS?

XSS (Cross-site scripting) attack is one in which an attacker is able to execute their code in the context of the target website. This code is then able to do anything that the website's own code could do:

- access or modify the content of the site's loaded pages
- access or modify content in local storage
- make HTTP requests with the user's credentials, enabling them to impersonate the user or access sensitive data

An XSS attack is possible when a website accepts some input which might have been crafted by an attacker (e.g. URL parameters, comments section)

## Ways to protect against XSS

1) Sanitize user input
2) Use CSP to verify that input has been sanitized
3) Use CSP to control resources to be loaded
