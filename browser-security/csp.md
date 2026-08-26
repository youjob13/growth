## What is CSP mean?

CSP (Content Security Policy) is a feature that helps to prevent or minimize the risk of certain types of security threats.
CSP is a series of instructions from a website to a browser, which instruct the browser to place restrictions on the things that the code comprising the site is allowed to do.

The primary use case for CSP is to control which resources, in particular JavaScript resources a document is allowed to load.
This is mainly used as a defense against XSS (cross-site scripting) attacks in which an attacker is able to inject malicious code into the victim's site and clickjacking in which attacker creates a decoy site which embeds the user's target side inside an iframe and when user interact with decoy elements they are inadvertently interacting with the target site instead.

example of CSP:
```md
Content-Security-Policy: default-src 'self'; img-src 'self' example.com
```

## Controlling resource loading

### Fetch directives

Are used to specify a particular category of resource that a document is allowed to load - such as JavaScript, CSS, images, fonts etc.

| CSP directive | Purpose |
|---------------|---------|
| default-src | default rule for all resources to be loaded (fallback) |
| img-src | sets allowed sources for image resources to be loaded from |
| script-src | sets allowed sources for JavaScript resources to be loaded from |
| style-src | sets allowed sources for CSS resources to be loaded from |
| child-src | sets allowed sources for web workers and nested browsing context loaded (iframe/frame) |
| connect-src | restricts the URLs which can be loaded using script interfaces |
| font-src | sets allowed sources for fonts loaded using @font-face |
| frame-src | sets allowed sources for nested browsing context loaded into elements such as iframe and frame |
| manifest-src | sets allowed sources for application manifest files |
| media-src | sets allowed sources for loading media using the <audio>, <video> and <track> elements |
| object-src | sets allowed sources for <object> and <embed> elements |
| prefetch-src | sets allowed sources to be prefetched or prerendered |
| script-src-elem | sets allowed sources for JavaScript <script> elements |
| script-src-attr | sets allowed sources for JavaScript inline event handlers |
| worker-src | sets allowed sources for Worker, SharedWorker or ServiceWorker scripts |

| CSP directive value | Description |
|---------------------|-------------|
| 'self' | only load resources that are same-origin with the document |
| example.com or IP | only load resources served from 'example.com' |
| 'none' | resource type should be completely blocked |
| 'trusted-type-eval' | by default, eval(), code arg to setTimeout() or Function() constructor are disabled, trusted-type-eval can be used to undo this protection |
| 'wasm-unsafe-eval' | by default, if a CSP contains a *default-src* or a *script-src* directive then a page won't be allowed to compile WebAssembly using functions like WebAssembly.compileStreaming() |
| 'unsafe-inline' | by default, if a CSP contains a *default-src* or a *script-src* directive then inline JavaScript is not allowed to execute (<script>, inline event handlers attributes, javascript: URLs) |
| 'nonce-<base64>' | resource can be loaded if value from CSP directive match the value in the element attribute (only applicable to <script> and <style> elements) |

