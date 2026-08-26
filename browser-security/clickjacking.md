## What is the clickjacking mean?

Attacker creates a decoy site which embeds the user's target side inside an iframe and when user interact with decoy elements they are inadvertently interacting with the target site instead.

## How to protect?

Be using CSP **frame-ancestors** directive. It can be used to control which documents if any are allowed to embed this document in a nested browsing context such as an <iframe>.

e.g.
```md
Content-Security-Policy: frame-ancestors 'none'
```
