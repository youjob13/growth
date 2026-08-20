## Replay attacks

When malicious user intercepts valid message and tries to use it again.

e.g. Kerberos solves this problem via time markers system and authenticators.

Every message contains time created marker. KDC and services log all recently received authenticators. If message arrived with already used time marker and the same data, request will be declined.
