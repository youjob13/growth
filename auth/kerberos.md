Kerberos solves **authentication** problem (approve client identity)

<img width="1024" height="683" alt="image" src="https://github.com/user-attachments/assets/9b2a08b8-35f6-46da-8be2-2d8f54802191" />

## Where is Kerberos used?

- Windows Active Directory (Windows Server and client OS)
- SSO systems
- Linux and Unix-system
- Apple macOS (windows coporative domains integration via Kerberos)
- HTTP/HTTPS
- LDAP
- RPC

## How does Kerberos work?

### Tickets

Ticket is an encrypted data structure

Two ticket types:
1) Ticket Granting Ticket (TGT) - main ticket. User gets during first authentication. This ticket is used for requesting certain service authentication. TGT is encrypted by KDC (Key Distribution Center) and contains user info (UserID, security groups, session key)
2) Service Ticket (ST) - special ticket for concrete service access. Every Service Ticket is encrypted by unique key of target service and can be decrypted only by them. 
This ticket contains all necessary info for user authentication on target service.

All Kerberos tickets have strict TTL (replay attacks protection)

## Key Distribution Center (KDC)

KDC is a trusted center which knows all secret keys of all network members (users and services).

KDC is splited into two components:
1) Authentication Server (AS) is responsible for the first user authentication and granting TGT.
2) Ticket Granting Server (TGS) accepts receiving Service Tickets requests. User shows his valid TGT and specify to which service he would like to receive access. TGS validates TGT and grants related Service Ticket.

## Authentication process schema

| Step | Message | Description |
|------|---------|-------------|
| 1 | AS-REQ | Client requests TGT from Authentication Server |
| 2 | AS-REP | AS returns encrypted TGT and session key |
| 3 | TGS-REQ | Client requests Service Ticket (with his TGT) |
| 4 | TGS-REP | TGS grants Service Ticket for target service |
| 5 | AP-REQ | Client sends Service Ticket to target service |
| 6 | AP-REP | Service approves successful authentication |
