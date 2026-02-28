### Authentication & Authorization 
---

#### Table of Contents

1. [Fundamentals](#1-fundamentals)
2. [Authentication](#2-authentication)
3. [Authentication Factors](#3-authentication-factors)
4. [Authentication Protocols & Standards](#4-authentication-protocols--standards)
5. [Password Security](#5-password-security)
6. [Session Management](#6-session-management)
7. [Tokens](#7-tokens)
8. [OAuth 2.0](#8-oauth-20)
9. [OpenID Connect (OIDC)](#9-openid-connect-oidc)
10. [SAML](#10-saml)
11. [Authorization](#11-authorization)
12. [Authorization Models](#12-authorization-models)
13. [Access Control Lists (ACL)](#13-access-control-lists-acl)
14. [Role-Based Access Control (RBAC)](#14-role-based-access-control-rbac)
15. [Attribute-Based Access Control (ABAC)](#15-attribute-based-access-control-abac)
16. [Policy-Based Access Control (PBAC)](#16-policy-based-access-control-pbac)
17. [JWT Deep Dive](#17-jwt-deep-dive)
18. [API Security](#18-api-security)
19. [SSO (Single Sign-On)](#19-sso-single-sign-on)
20. [MFA (Multi-Factor Authentication)](#20-mfa-multi-factor-authentication)
21. [Passwordless Authentication](#21-passwordless-authentication)
22. [Zero Trust Architecture](#22-zero-trust-architecture)
23. [Security Threats & Attacks](#23-security-threats--attacks)
24. [Cryptography in Auth](#24-cryptography-in-auth)
25. [Identity Providers (IdP)](#25-identity-providers-idp)
26. [Federation](#26-federation)
27. [How Everything Connects](#27-how-everything-connects)

---

## 1. Fundamentals

### What is Identity?
Identity is the claim of who or what an entity is. In computing, an identity represents a user, service, device, or application. It is the foundation upon which both authentication and authorization are built.

### Core Concepts

| Concept | Definition |
|---|---|
| **Identity** | Who you are — a unique representation of an entity |
| **Authentication (AuthN)** | Proving you are who you claim to be |
| **Authorization (AuthZ)** | What you are allowed to do once identity is confirmed |
| **Access Control** | Mechanisms that enforce authorization decisions |
| **Principal** | An entity that can be authenticated (user, service, device) |
| **Credential** | Evidence used to authenticate (password, token, certificate) |
| **Subject** | The entity requesting access |
| **Resource** | What is being accessed (API, file, database, endpoint) |
| **Policy** | Rules that define who can access what under which conditions |

### Authentication vs Authorization — Key Distinction

```
User visits a banking app:

  [Authentication]        [Authorization]
  "Are you John?"    →    "John can view accounts"
  "Prove it"         →    "John CANNOT transfer > $10,000"
  John logs in       →    John sees only his own data
       ↓
  Identity confirmed → Permission decisions made
```

Authentication ALWAYS comes before authorization. You cannot make authorization decisions about an unknown identity.

### The CIA Triad (Foundation of Security)

- **Confidentiality** — Data is accessible only to authorized entities
- **Integrity** — Data is not tampered with or altered
- **Availability** — Systems and data are accessible when needed

Authentication and Authorization are the primary mechanisms that enforce Confidentiality and partially Integrity.

---

## 2. Authentication

Authentication is the process of verifying that an entity is who it claims to be. It answers the question: **"Are you really who you say you are?"**

### Authentication Flow (General)

```
1. Identification  →  User claims an identity (username, email)
2. Verification    →  User provides proof (password, OTP, biometric)
3. Validation      →  System checks the proof against stored record
4. Decision        →  Grant or deny access
5. Session/Token   →  Issue a session or token for subsequent requests
```

### Types of Authentication

#### 1. Knowledge-Based Authentication (KBA)
Something the user **knows**.
- Passwords
- PINs
- Security questions
- Passphrases

#### 2. Possession-Based Authentication
Something the user **has**.
- Hardware token (YubiKey, RSA SecurID)
- Authenticator app (Google Authenticator, Authy)
- SMS OTP
- Smart card / CAC card
- Email magic link

#### 3. Inherence-Based Authentication
Something the user **is**.
- Fingerprint scan
- Face recognition
- Iris / retina scan
- Voice recognition
- Behavioral biometrics (typing rhythm, mouse movement)

#### 4. Location-Based Authentication
**Where** the user is.
- IP address check
- GPS location
- Geofencing
- Network-based (e.g., only from corporate VPN)

#### 5. Behavior-Based Authentication
**How** the user behaves.
- Continuous authentication using behavioral patterns
- Device fingerprinting
- Anomaly detection on usage patterns

### Authentication Strength Levels

```
Weak    ──────────────────────────────────────  Strong
  │                                               │
Single password   MFA   Certificate   Biometric+MFA
  │                │         │              │
Easy to attack   Better   Very strong   Very strong
```

---

## 3. Authentication Factors

### Single Factor Authentication (SFA)
Only one factor used — typically a password. Weakest form. Vulnerable to brute force, phishing, credential stuffing.

### Two-Factor Authentication (2FA)
Two different factor types combined:
- Password + OTP (most common)
- Password + Hardware token
- Password + Biometric

### Multi-Factor Authentication (MFA)
Two or more factors from different categories. See [section 20](#20-mfa-multi-factor-authentication) for full detail.

### Step-Up Authentication
Normal access uses weak auth (password), but sensitive operations trigger a stronger authentication challenge:

```
User logs in with password
     ↓
Access general features  ← No step-up needed
     ↓
Attempts to transfer $5000
     ↓
System requires OTP or biometric ← Step-up triggered
     ↓
Transfer allowed after re-verification
```

### Adaptive / Risk-Based Authentication
The authentication requirement changes dynamically based on risk signals:

**Risk signals include:**
- New device or browser
- Unusual location (new country)
- Unusual time (3AM login)
- Many failed attempts before success
- Sensitive resource being accessed
- IP reputation (VPN, TOR, known malicious)

```
Low Risk  → Password only
Med Risk  → Password + OTP
High Risk → Password + OTP + Admin approval
```

---

## 4. Authentication Protocols & Standards

### HTTP Basic Authentication
The simplest form. Credentials sent as Base64-encoded `username:password` in the `Authorization` header.

```http
GET /resource HTTP/1.1
Authorization: Basic dXNlcjpwYXNzd29yZA==
```

- **Problem:** Base64 is NOT encryption — easily decoded. Must always be used with HTTPS.
- **When to use:** Internal tools, testing, simple APIs where HTTPS is guaranteed.

### HTTP Digest Authentication
An improvement over Basic Auth. Server sends a nonce (random value), client hashes credentials with the nonce using MD5.

```
Client → Server: GET /resource
Server → Client: 401 Unauthorized + nonce value
Client → Server: hashed(username:password:nonce)
Server validates hash
```

- **Better than Basic** because credentials are never sent in plain text.
- **Still weak** because MD5 is broken and it's vulnerable to replay attacks.

### API Key Authentication
A static secret string passed in headers or query parameters.

```http
GET /api/data
Authorization: Api-Key abc123xyz789
```

Or as a query param:
```
GET /api/data?api_key=abc123xyz789
```

- **Simple** to implement.
- **Problem:** Not user-specific, hard to rotate, no expiry by default, easily leaked.

### Certificate-Based Authentication (mTLS)
Both client and server present TLS certificates. Client authenticates itself using a public key certificate signed by a trusted Certificate Authority (CA).

```
Client                     Server
  │── TLS Handshake ──────→ │
  │ ←─ Server Certificate ─ │
  │── Client Certificate →  │
  │   Both verified by CA   │
  │═══ Secure Channel ══════│
```

- **Very strong** — used in enterprise, banking, government.
- **Harder to implement** — requires PKI infrastructure.
- **Use cases:** Microservices mTLS, B2B integrations, VPN authentication.

### Kerberos
A ticket-based network authentication protocol developed at MIT. Used heavily in Windows Active Directory environments.

```
1. Client → KDC: "I am Alice, I want access"
2. KDC → Client: Ticket Granting Ticket (TGT) encrypted with Alice's key
3. Client → KDC: Present TGT, request access to service S
4. KDC → Client: Service Ticket for S
5. Client → Service S: Present Service Ticket
6. Service S → Client: Access granted
```

**Key components:**
- **KDC (Key Distribution Center)** — Central authentication server
- **TGT (Ticket Granting Ticket)** — Temporary credential to get service tickets
- **Service Ticket** — Credential for a specific service
- **Realm** — Administrative domain

### LDAP (Lightweight Directory Access Protocol)
A protocol for accessing and maintaining distributed directory information (like Active Directory). Often used to authenticate users against a central directory.

```
Application → LDAP Server: Bind request (username + password)
LDAP Server → Application: Success / Failure
Application: User authenticated against directory
```

- **Not an auth protocol itself** — it's a directory protocol used for authentication.
- **Used by:** Corporate SSO, VPNs, internal apps.

### RADIUS (Remote Authentication Dial-In User Service)
A networking protocol for centralizing authentication, authorization, and accounting (AAA) for network access.

- Used by: VPNs, WiFi, ISPs
- Supports many auth methods (PAP, CHAP, EAP)

---

## 5. Password Security

### Password Hashing
Passwords must NEVER be stored in plain text. They must be hashed using a one-way function.

#### Bad Practices
```
Plain text:  password123          ← Catastrophic
MD5:         482c811da5d5b4bc...  ← Broken, easily rainbow-tabled
SHA-1:       f2477a144dff4f...    ← Broken
SHA-256:     ef92b779...          ← Better but still fast (bad for passwords)
```

#### Good Practices — Slow Hashing Algorithms

| Algorithm | Notes |
|---|---|
| **bcrypt** | Industry standard, work factor adjustable (cost parameter) |
| **scrypt** | Memory-hard, harder to parallelize than bcrypt |
| **Argon2** | Winner of Password Hashing Competition, best current choice |
| **PBKDF2** | NIST recommended, used in many standards |

```python
# bcrypt example
import bcrypt

password = b"user_password"
salt = bcrypt.gensalt(rounds=12)  # cost factor = 12
hashed = bcrypt.hashpw(password, salt)
# Stored: $2b$12$...long_hash...

# Verification
bcrypt.checkpw(password, hashed)  # True
```

### Salting
A unique random value (salt) added to each password before hashing. Prevents rainbow table attacks and ensures two users with the same password have different hashes.

```
Password: "password123"
Salt A:   "xK9mP2"
Hashed:   bcrypt("password123" + "xK9mP2")  → unique hash A

Same password, different user:
Salt B:   "qR7nL5"
Hashed:   bcrypt("password123" + "qR7nL5")  → completely different hash B
```

### Peppering
An additional secret value (pepper) added to all passwords before hashing. Unlike salt, pepper is stored in the application config, not the database.

```
hash = bcrypt(password + salt + pepper)
```

Even if the database is compromised, attacker also needs the pepper from config.

### Password Policies
- **Minimum length** — At least 12 characters (NIST recommends 8 minimum but 12+ preferred)
- **Character complexity** — Mix of upper, lower, numbers, symbols (but NIST 2017 says don't force complexity over length)
- **Breach checking** — Check against known breached password lists (HaveIBeenPwned)
- **No password hints** — Hints reduce security
- **Expiry** — NIST now recommends against forced regular rotation unless breach suspected

### Password Reset Flow (Secure)
```
1. User requests reset
2. Generate cryptographically random token (not sequential IDs)
3. Store hash of token in DB with expiry (15-60 minutes)
4. Email link: https://app.com/reset?token=<plaintext_token>
5. User clicks link → token validated against stored hash
6. Token invalidated after use (one-time use)
7. User sets new password
8. Invalidate all existing sessions
```

---

## 6. Session Management

### What is a Session?
After successful authentication, the server creates a session — a server-side record that tracks the authenticated user's state across multiple requests (since HTTP is stateless).

### Session-Based Authentication Flow

```
1. User submits credentials
2. Server validates → creates Session ID (random, unique)
3. Session data stored server-side (memory, Redis, DB)
4. Session ID sent to client in a cookie
5. Client sends cookie on every request
6. Server looks up Session ID → finds user data
7. Request processed as authenticated user
```

### Session Storage Options

| Storage | Pros | Cons |
|---|---|---|
| **In-memory** | Fast | Lost on server restart, doesn't scale horizontally |
| **Database** | Persistent, scalable | Slower, DB becomes bottleneck |
| **Redis/Memcached** | Fast + persistent | Additional infrastructure |
| **Client-side (cookie)** | No server storage | Must be encrypted + signed |

### Session Cookie Security Attributes

```http
Set-Cookie: sessionId=abc123; 
  HttpOnly;       ← JS cannot access — prevents XSS theft
  Secure;         ← Only sent over HTTPS
  SameSite=Strict;← Prevents CSRF
  Path=/;
  Max-Age=3600;   ← Expires in 1 hour
  Domain=app.com
```

### Session Security Best Practices
- **Regenerate Session ID** after login (prevents session fixation)
- **Short expiry** for sensitive applications
- **Sliding expiry** — reset timer on activity
- **Absolute expiry** — force re-login after X hours regardless of activity
- **Invalidate on logout** — remove server-side session, clear cookie
- **Bind to IP/User-Agent** — detect session hijacking (optional, can break legitimate use)

### Session vs Token-Based Auth

```
Session-Based:                   Token-Based (JWT):
─────────────────────────        ──────────────────────────────
State stored on SERVER           State stored on CLIENT (token)
Session ID in cookie             Token in cookie or header
Server must look up session      Token is self-contained
Easier to invalidate             Hard to invalidate before expiry
Scales poorly (sticky sessions)  Scales easily (stateless)
Good for monoliths               Good for APIs, microservices
```

---

## 7. Tokens

A token is a compact, self-contained or referenced piece of data that represents authentication/authorization state.

### Types of Tokens

#### 1. Opaque Token
A random string that has no intrinsic meaning — the server looks it up in a store to find associated data.

```
Token: "a7f3d9e2b1c8k4m5n6p0q2r3"
Server looks up → { userId: 42, role: "admin", expires: ... }
```

#### 2. Self-Contained Token (JWT)
Token that carries all needed information within itself. No server lookup needed. See [section 17](#17-jwt-deep-dive) for full detail.

#### 3. Access Token
Short-lived token granting access to protected resources. Used in OAuth 2.0.
- Usually expires in 15 minutes to 1 hour
- Sent in every API request

#### 4. Refresh Token
Long-lived token used to get new access tokens without re-authentication.
- Expires in days/weeks/months
- Stored securely, never sent to resource servers
- Can be rotated on use (refresh token rotation)

#### 5. ID Token
Token that contains user identity information (claims about who the user is). Comes from OIDC (OpenID Connect).
- Contains: sub, email, name, picture, etc.
- Not meant to be used for API access

#### 6. Authorization Code
Short-lived, one-time-use code exchanged for tokens. Used in OAuth 2.0 Authorization Code flow.
- Expires in seconds to minutes
- Used only once, then discarded

### Token Lifecycle

```
Issue → Use → Refresh → Revoke

[Login]
  ↓
[Access Token (15min)] + [Refresh Token (30 days)]
  ↓
[API Calls with Access Token]
  ↓
[Access Token Expires]
  ↓
[Use Refresh Token → New Access Token]
  ↓
[Refresh Token Rotated]
  ↓
[Logout → Revoke Refresh Token]
```

### Token Storage (Client-Side)

| Storage | XSS Risk | CSRF Risk | Notes |
|---|---|---|---|
| **HttpOnly Cookie** | ✅ Safe | ⚠ Mitigate with SameSite | Best for web apps |
| **Memory (JS var)** | ✅ Safe | ✅ Safe | Lost on page refresh |
| **localStorage** | ❌ Vulnerable | ✅ Safe | Avoid for sensitive tokens |
| **sessionStorage** | ❌ Vulnerable | ✅ Safe | Cleared when tab closes |

**Best practice:** Store access tokens in memory, refresh tokens in HttpOnly cookies.

---

## 8. OAuth 2.0

OAuth 2.0 is an **authorization framework** — NOT an authentication protocol. It allows a third-party application to access resources on behalf of a user, without the user sharing their credentials.

### The Problem OAuth Solves

```
Without OAuth:
  User gives Instagram their Google password to import contacts
  → Instagram now has your Google password ← DANGEROUS

With OAuth:
  User gives Instagram permission (via Google consent screen)
  → Instagram gets limited access token
  → Google password never shared
```

### Key Roles in OAuth 2.0

| Role | Description |
|---|---|
| **Resource Owner** | The user who owns the data/resource |
| **Client** | The application requesting access |
| **Authorization Server** | Issues tokens (e.g., Google, Auth0, Keycloak) |
| **Resource Server** | The API/service with the protected data |

### OAuth 2.0 Grant Types (Flows)

#### 1. Authorization Code Flow (Most Secure — for Web Apps)

```
User         Client App      Auth Server      Resource Server
  │               │               │                  │
  │──Login Btn──→ │               │                  │
  │               │──Redirect──→  │                  │
  │               │  client_id    │                  │
  │               │  redirect_uri │                  │
  │               │  scope        │                  │
  │◄──────────────────────────────│                  │
  │  Login & Consent Screen       │                  │
  │───────────────────────────────│                  │
  │  User consents                │                  │
  │               │◄──code───────│                  │
  │               │               │                  │
  │               │──code+secret→│                  │
  │               │◄──tokens─────│                  │
  │               │               │                  │
  │               │──access_token────────────────→  │
  │               │◄──protected data────────────────│
```

#### 2. Authorization Code + PKCE (For SPAs & Mobile Apps)

PKCE (Proof Key for Code Exchange) — prevents authorization code interception attacks.

```
1. Client generates random code_verifier
2. Client hashes it: code_challenge = SHA256(code_verifier)
3. Client sends code_challenge in auth request
4. Auth server stores code_challenge
5. Client receives auth code
6. Client sends auth code + code_verifier to token endpoint
7. Auth server verifies: SHA256(code_verifier) == stored code_challenge
8. Tokens issued
```

#### 3. Client Credentials Flow (Machine-to-Machine)

No user involved. Server-to-server communication.

```
Client (backend service)     Auth Server
  │                              │
  │── client_id + client_secret→ │
  │◄── access_token ─────────────│
  │                              │
  │── access_token ──────→ Resource Server
```

#### 4. Device Authorization Flow (IoT / TV apps)

For devices that can't display a browser.

```
1. Device shows: "Go to example.com/activate and enter code: BDFG-HJKM"
2. User goes to that URL on their phone/computer and logs in
3. Device polls auth server
4. Once user approves, device gets tokens
```

#### 5. Implicit Flow (Deprecated)
Previously used for SPAs. Token returned directly in URL fragment. **Do not use** — replaced by Auth Code + PKCE.

### OAuth 2.0 Scopes
Scopes define the level of access being requested:

```
scope=read:profile          ← Read user profile
scope=write:posts           ← Create posts
scope=read:profile write:posts delete:comments  ← Multiple scopes
scope=openid profile email  ← OpenID Connect scopes
```

### OAuth Token Endpoints

```
/authorize      → Start auth flow, user login & consent
/token          → Exchange code for tokens
/introspect     → Validate a token (RFC 7662)
/revoke         → Revoke a token (RFC 7009)
/userinfo       → Get user info (OIDC)
/.well-known/openid-configuration  → Discovery document
```

---

## 9. OpenID Connect (OIDC)

OIDC is an **authentication** layer built on top of OAuth 2.0. It adds identity to OAuth's authorization framework.

```
OAuth 2.0     =  Authorization framework ("what can you do?")
OIDC          =  OAuth 2.0 + Identity ("who are you?")
```

### What OIDC Adds to OAuth 2.0

- **ID Token** (JWT containing user identity claims)
- **UserInfo endpoint** to fetch user profile
- **Standard claims** (sub, email, name, picture, phone_number, etc.)
- **Discovery document** (`/.well-known/openid-configuration`)
- **JWKS endpoint** (public keys to verify ID token signature)

### OIDC Flow

```
1. Client includes scope=openid in OAuth request
2. User authenticates with Identity Provider
3. Auth server returns: access_token + id_token (+ refresh_token)
4. Client validates id_token (JWT)
5. id_token contains user identity claims
6. Client can also call /userinfo with access_token for more claims
```

### ID Token Structure (JWT)

```json
{
  "iss": "https://accounts.google.com",
  "sub": "1234567890",
  "aud": "your-client-id",
  "exp": 1700000000,
  "iat": 1699996400,
  "email": "user@example.com",
  "email_verified": true,
  "name": "John Doe",
  "picture": "https://...",
  "nonce": "abc123"
}
```

### OIDC vs OAuth 2.0 Token Usage

| Token | OAuth 2.0 | OIDC |
|---|---|---|
| **Access Token** | Access APIs | Access APIs |
| **Refresh Token** | Get new access token | Get new access token |
| **ID Token** | ❌ Not part of OAuth | ✅ Carry user identity |

### OIDC Standard Scopes

| Scope | Claims returned |
|---|---|
| `openid` | sub (required for OIDC) |
| `profile` | name, given_name, family_name, picture, locale |
| `email` | email, email_verified |
| `phone` | phone_number, phone_number_verified |
| `address` | address |

---

## 10. SAML

SAML (Security Assertion Markup Language) is an XML-based open standard for exchanging authentication and authorization data between parties — specifically between an Identity Provider (IdP) and a Service Provider (SP).

### SAML vs OAuth/OIDC

| Aspect | SAML | OAuth 2.0 / OIDC |
|---|---|---|
| Format | XML | JSON |
| Age | 2002 | 2012 |
| Use case | Enterprise SSO | Web/Mobile apps |
| Complexity | High | Lower |
| Mobile friendly | ❌ Poor | ✅ Great |

### SAML Roles

- **Identity Provider (IdP)** — Authenticates users and issues SAML assertions (e.g., Okta, ADFS)
- **Service Provider (SP)** — Relies on IdP for authentication (e.g., Salesforce, your app)
- **Principal** — The user being authenticated

### SAML Flow (SP-Initiated)

```
User → SP: Access resource
SP → User: Redirect to IdP (with SAMLRequest)
User → IdP: Login page
User authenticates with IdP credentials
IdP → User: Redirect to SP (with SAMLResponse containing Assertion)
SP → SP: Validate SAMLResponse signature and assertions
SP → User: Access granted, session created
```

### SAML Assertion
The core of SAML — an XML document stating facts about the user:

```xml
<saml:Assertion>
  <saml:Issuer>https://idp.example.com</saml:Issuer>
  <saml:Subject>
    <saml:NameID>john.doe@company.com</saml:NameID>
  </saml:Subject>
  <saml:Conditions
    NotBefore="2024-01-01T10:00:00Z"
    NotOnOrAfter="2024-01-01T10:05:00Z">
  </saml:Conditions>
  <saml:AttributeStatement>
    <saml:Attribute Name="Role">
      <saml:AttributeValue>Admin</saml:AttributeValue>
    </saml:Attribute>
  </saml:AttributeStatement>
</saml:Assertion>
```

### SAML Bindings
How SAML messages are transported:
- **HTTP Redirect Binding** — SAML message in URL query string (deflated + Base64 encoded)
- **HTTP POST Binding** — SAML message in HTML form POST body (Base64 encoded)
- **HTTP Artifact Binding** — Reference (artifact) sent, actual message retrieved via back-channel

---

## 11. Authorization

Authorization is the process of determining what an authenticated identity is allowed to do. It answers: **"What can you do?"**

### Authorization vs Authentication (Revisited)

```
Authentication: "You are John Doe, authenticated employee"
                              ↓
Authorization:  "John Doe can: READ reports, WRITE comments"
                "John Doe CANNOT: DELETE records, VIEW payroll"
```

### Authorization Decision Components

```
Request: Can <subject> perform <action> on <resource> given <context>?

Subject:   user_id=42, role=editor, dept=marketing
Action:    DELETE
Resource:  /articles/89 (owned by user_id=15)
Context:   request from IP 10.0.0.1, time=2pm weekday

Decision:  DENY (editor cannot delete other users' articles)
```

### Where Authorization Happens

```
[Request] → [API Gateway] → [Auth Middleware] → [Application Logic] → [Database]
              ↑                   ↑                    ↑
         Coarse-grained      Route-level auth    Fine-grained
         (IP blocks,          (JWT validation,    (row-level security,
          rate limits)         role checks)        ownership checks)
```

### Authorization Patterns

#### Centralized Authorization
All authorization decisions made by a central service (e.g., OPA — Open Policy Agent).

```
Application → Auth Service: "Can user:42 delete:article:89?"
Auth Service → Application: "DENY — user doesn't own resource"
```

#### Decentralized Authorization
Each service makes its own authorization decisions using shared tokens/roles.

#### Inline / Hardcoded Authorization
Authorization logic embedded directly in application code.

```python
if user.role != "admin":
    raise PermissionError("Only admins can delete users")
```

---

## 12. Authorization Models

### Overview

```
ACL         → Who has access to what (simple list)
RBAC        → Access based on roles
ABAC        → Access based on attributes/context
PBAC        → Access based on policies (rules engine)
ReBAC       → Access based on relationships
DAC         → Owner controls access
MAC         → System-enforced mandatory access
```

---

## 13. Access Control Lists (ACL)

An ACL is a list of permissions attached to a resource. It specifies which users or system processes are granted access and what operations are allowed.

### File System ACL Example

```
File: /home/reports/Q4_2024.xlsx
──────────────────────────────────
Principal       Permission
──────────────
alice           READ, WRITE
bob             READ
group:finance   READ, WRITE
group:hr        DENY ALL
*               DENY ALL
```

### ACL in Networking (Firewall Rules)

```
Rule  Source IP      Dest IP        Port    Action
────────────────────────────────────────────────
1     10.0.0.0/24   192.168.1.5    443     ALLOW
2     0.0.0.0/0     192.168.1.5    22      DENY
3     10.0.1.50     ANY            ANY     ALLOW
```

### ACL Pros and Cons

```
Pros:                        Cons:
✅ Simple concept            ❌ Doesn't scale well
✅ Fine-grained control      ❌ Hard to audit with many users
✅ Per-resource control      ❌ No concept of roles or groups
                             ❌ Changing permissions = update every ACL
```

---

## 14. Role-Based Access Control (RBAC)

RBAC assigns permissions to roles, and users are assigned to roles. Users inherit the permissions of their roles.

### Core Concepts

```
Users ──→ assigned to ──→ Roles ──→ have ──→ Permissions
Alice  ────────────────→  Admin  ──────────→ [read, write, delete]
Bob    ────────────────→  Editor ──────────→ [read, write]
Carol  ────────────────→  Viewer ──────────→ [read]
```

### RBAC Components

| Component | Description |
|---|---|
| **User** | An entity (person or service) |
| **Role** | A named collection of permissions |
| **Permission** | The right to perform an operation on a resource |
| **Session** | Active role assignment for a user |

### Hierarchical RBAC

Roles can inherit permissions from other roles:

```
Super Admin
  └── Admin
        └── Manager
              └── Employee
                    └── Guest

Admin inherits all Employee and Guest permissions + has additional ones
```

### RBAC Example in Code

```python
# Permission check
def can_perform(user, action, resource):
    user_permissions = get_permissions_for_roles(user.roles)
    required_permission = f"{action}:{resource}"
    return required_permission in user_permissions

# Usage
user = get_user(user_id=42)  # has roles: ["editor", "commenter"]
if not can_perform(user, "delete", "articles"):
    raise PermissionDenied("Editors cannot delete articles")
```

### RBAC Pros and Cons

```
Pros:                                Cons:
✅ Easy to understand and manage     ❌ Role explosion (too many specific roles)
✅ Easy to audit                     ❌ No context awareness (time, location)
✅ Centralized permission management ❌ Static — can't express "own resource only"
✅ Scales well for large orgs        ❌ Not fine-grained enough for all use cases
```

---

## 15. Attribute-Based Access Control (ABAC)

ABAC makes authorization decisions based on attributes of the subject, resource, action, and environment. It's more expressive and flexible than RBAC.

### ABAC Policy Structure

```
Policy: IF <conditions about attributes> THEN <ALLOW/DENY>

Example:
IF  user.department == "finance"
AND user.clearance_level >= 3
AND resource.classification == "confidential"
AND resource.department == "finance"
AND action == "read"
AND environment.time BETWEEN "09:00" AND "18:00"
AND environment.location == "corporate_network"
THEN ALLOW
```

### Four Attribute Categories

#### Subject Attributes
```
user.id, user.role, user.department, user.clearance_level,
user.age, user.subscription_tier, user.location
```

#### Resource Attributes
```
resource.owner, resource.classification, resource.department,
resource.type, resource.sensitivity, resource.created_date
```

#### Action Attributes
```
action.type (read/write/delete), action.http_method,
action.operation
```

#### Environment Attributes
```
env.time, env.day_of_week, env.ip_address, env.location,
env.network_type, env.device_type
```

### ABAC Policy Examples

```yaml
# Policy 1: Doctors can read patient records in their department
- effect: ALLOW
  subject:
    role: doctor
    department: "{{resource.department}}"
  action: read
  resource:
    type: patient_record

# Policy 2: No access outside business hours
- effect: DENY
  action: [write, delete]
  environment:
    time: "NOT BETWEEN 08:00 AND 20:00"

# Policy 3: Users can only edit their own posts
- effect: ALLOW
  action: edit
  resource:
    type: post
    owner: "{{subject.id}}"
```

### ABAC Pros and Cons

```
Pros:                                    Cons:
✅ Highly flexible and expressive        ❌ Complex to design and maintain
✅ Context-aware decisions               ❌ Performance overhead (complex evaluation)
✅ Fine-grained control                  ❌ Hard to audit and debug
✅ No role explosion problem             ❌ Requires well-designed attribute schema
✅ Dynamic (adapts to context)
```

---

## 16. Policy-Based Access Control (PBAC)

PBAC uses a policy engine to evaluate authorization decisions. Policies are written in a dedicated language and evaluated at runtime. It's essentially ABAC with a formal policy language.

### XACML (eXtensible Access Control Markup Language)
The classic PBAC standard using XML policies:

```xml
<Policy PolicyId="ReadFinancialReports">
  <Target>
    <Resources><Resource>financial-reports</Resource></Resources>
    <Actions><Action>read</Action></Actions>
  </Target>
  <Rule RuleId="FinanceEmployeesOnly" Effect="Permit">
    <Condition>
      <Apply FunctionId="string-equal">
        <AttributeDesignator Category="subject" AttributeId="department"/>
        <AttributeValue>finance</AttributeValue>
      </Apply>
    </Condition>
  </Rule>
</Policy>
```

### OPA — Open Policy Agent

Modern PBAC engine using Rego policy language. Cloud-native, widely used.

```rego
# policy.rego
package authz

default allow = false

# Allow if user is admin
allow {
    input.user.role == "admin"
}

# Allow read if user owns the resource
allow {
    input.action == "read"
    input.resource.owner == input.user.id
}

# Allow if user's department matches resource's department
allow {
    input.action == "read"
    input.user.department == input.resource.department
    input.resource.classification != "top_secret"
}
```

Query OPA from your application:
```json
POST /v1/data/authz/allow
{
  "input": {
    "user": { "id": 42, "role": "editor", "department": "marketing" },
    "action": "read",
    "resource": { "id": 99, "owner": 42, "classification": "internal" }
  }
}
Response: { "result": true }
```

### Cedar (AWS Policy Language)
Modern, strongly-typed policy language by AWS:

```
permit (
  principal == User::"alice",
  action in [Action::"read", Action::"write"],
  resource in Folder::"public"
);

forbid (
  principal,
  action == Action::"delete",
  resource
) unless {
  principal == resource.owner
};
```

---

## 17. JWT Deep Dive

JWT (JSON Web Token) is a compact, URL-safe means of representing claims securely between two parties.

### JWT Structure

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9   ← Header (Base64URL)
.
eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIn0  ← Payload (Base64URL)
.
SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c          ← Signature
```

#### Header
```json
{
  "alg": "RS256",
  "typ": "JWT",
  "kid": "key-id-1"
}
```

#### Payload (Claims)
```json
{
  "iss": "https://auth.myapp.com",
  "sub": "user_42",
  "aud": ["https://api.myapp.com"],
  "exp": 1700003600,
  "iat": 1700000000,
  "nbf": 1700000000,
  "jti": "unique-token-id-abc123",
  "name": "John Doe",
  "email": "john@example.com",
  "role": "admin",
  "permissions": ["read:users", "write:reports"]
}
```

### Registered Claims (Standard)

| Claim | Name | Description |
|---|---|---|
| `iss` | Issuer | Who created the token |
| `sub` | Subject | Who the token is about |
| `aud` | Audience | Who the token is for |
| `exp` | Expiration | When the token expires |
| `iat` | Issued At | When token was created |
| `nbf` | Not Before | Token invalid before this time |
| `jti` | JWT ID | Unique identifier for the token |

### Signature Algorithms

| Algorithm | Type | Notes |
|---|---|---|
| **HS256** | Symmetric (HMAC) | Same key signs and verifies — share secret needed |
| **HS384** | Symmetric (HMAC) | Same as HS256 with SHA-384 |
| **HS512** | Symmetric (HMAC) | Same as HS256 with SHA-512 |
| **RS256** | Asymmetric (RSA) | Private key signs, public key verifies — best for distributed |
| **RS384** | Asymmetric (RSA) | — |
| **RS512** | Asymmetric (RSA) | — |
| **ES256** | Asymmetric (ECDSA) | Shorter keys, same security as RS256 — modern choice |
| **PS256** | Asymmetric (RSA-PSS) | More secure variant of RS256 |
| `none` | No signature | **NEVER USE** — allows signature bypass attacks |

### JWT Validation Checklist

When receiving a JWT, you MUST verify:

```
1. ✅ Signature is valid (using correct key)
2. ✅ Algorithm matches expected (prevent alg:none attack)
3. ✅ exp is in the future (not expired)
4. ✅ nbf is in the past (token is now valid)
5. ✅ iss matches expected issuer
6. ✅ aud contains your service
7. ✅ jti not in revocation list (if implementing revocation)
```

### JWT Security Pitfalls

#### 1. Algorithm Confusion Attack (alg:none)
```
Attacker changes header from {"alg":"RS256"} to {"alg":"none"}
and removes signature — if server doesn't validate algorithm, accepts it.
Fix: Always hardcode expected algorithm, never trust alg from header.
```

#### 2. HS256 with RS256 Public Key Attack
```
If server uses RS256, public key is public.
Attacker uses that public key as the secret for HS256.
Fix: Always validate algorithm type matches what you expect.
```

#### 3. Sensitive Data in Payload
```
JWT payload is Base64URL encoded — NOT encrypted.
Anyone can decode and read it.
Fix: Never store sensitive data (SSN, passwords) in JWT payload.
     Use JWE (JSON Web Encryption) if payload needs to be encrypted.
```

#### 4. Token Revocation Problem
JWTs are stateless — you can't invalidate them before expiry without a blocklist.
```
Solutions:
- Short expiry (5-15 minutes) + refresh tokens
- Token blocklist in Redis (defeats stateless benefit but necessary for logout)
- Token versioning in database (check user's current token version on each request)
```

---

## 18. API Security

### API Authentication Methods Comparison

```
API Key       → Simple, static, no user context
Basic Auth    → Credentials in header, HTTPS required
Bearer Token  → JWT or opaque, most common
OAuth 2.0     → Delegated access, industry standard
mTLS          → Certificate-based, strongest
```

### API Key Best Practices

```
✅ Generate cryptographically random (256-bit minimum)
✅ Hash stored keys (like passwords) — only store hash
✅ Prefix keys for identification: sk_live_abc123, pk_test_xyz
✅ Scope keys (read-only, write, admin)
✅ Support key rotation without downtime
✅ Log all key usage
✅ Rate limit per key
✅ Allow IP restriction per key
```

### OAuth 2.0 Token in API Requests

```http
GET /api/v1/users/me HTTP/1.1
Host: api.example.com
Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9...
```

### API Gateway Authorization

```
Client → API Gateway → (validates token) → Microservice

API Gateway responsibilities:
  - Validate JWT signature and claims
  - Rate limiting
  - IP allowlisting
  - Inject user context into downstream headers (X-User-Id, X-User-Role)
  - Log all requests with identity context
```

### Scopes in API Authorization

```
GET  /api/articles     → requires: articles:read
POST /api/articles     → requires: articles:write
DELETE /api/articles/1 → requires: articles:delete OR admin:all
GET  /api/users        → requires: users:read AND role:admin
```

### OIDC/JWT in Microservices

```
[Client] → [API Gateway]
              │ validates JWT
              │ extracts user context
              ↓
         [Service A] ← passes JWT or user context headers
              ↓
         [Service B] ← validates same JWT (shared public key)
              ↓
         [Service C] ← uses JWT claims for fine-grained authz
```

---

## 19. SSO (Single Sign-On)

SSO allows users to authenticate once and gain access to multiple applications without logging in again.

### How SSO Works

```
User logs in to company portal once
     ↓
Accesses Salesforce  → No login required ✅
Accesses Slack       → No login required ✅
Accesses GitHub Org  → No login required ✅
Accesses JIRA        → No login required ✅
```

### SSO Architecture

```
[User]
  │ 1. Access App A
  ↓
[App A] ← Not logged in
  │ 2. Redirect to SSO Provider
  ↓
[SSO Provider / IdP]
  │ 3. User logs in (once)
  │ 4. SSO session created
  │ 5. Token/Assertion issued
  ↓
[App A] ← Receives token/assertion
  │ 6. User logged in to App A
  │
  │ 7. User accesses App B
  ↓
[App B] ← Not logged in
  │ 8. Redirect to SSO Provider
  ↓
[SSO Provider / IdP] ← Already has SSO session
  │ 9. No login needed — issues new token
  ↓
[App B] ← User logged in instantly
```

### SSO Protocols

| Protocol | Format | Common Use |
|---|---|---|
| **SAML 2.0** | XML | Enterprise, legacy systems |
| **OIDC** | JSON/JWT | Modern web/mobile apps |
| **CAS** | XML | University SSO |
| **WS-Federation** | XML | Microsoft/ADFS environments |

### SSO Security Considerations

```
✅ SSO session should have its own expiry (separate from app sessions)
✅ Support Single Logout (SLO) — logout from one logs out from all
✅ Protect the IdP — it's now a single point of failure and high-value target
✅ MFA at the SSO level applies to all connected apps
⚠  If IdP is compromised, all connected apps are compromised
```

---

## 20. MFA (Multi-Factor Authentication)

MFA requires users to provide two or more verification factors from different categories.

### OTP (One-Time Password)

#### TOTP (Time-Based OTP) — RFC 6238
```
Secret (shared) + Current Time → 6-digit code valid for 30 seconds

TOTP = HOTP(secret, floor(time/30))
     = HMAC-SHA1(secret, time_step)
     → 6-digit truncation

Apps: Google Authenticator, Authy, Microsoft Authenticator
```

#### HOTP (HMAC-Based OTP) — RFC 4226
```
Secret + Counter → 6-digit code valid until used

HOTP = HMAC-SHA1(secret, counter)
Counter increments on each use
Used in hardware tokens
```

#### SMS OTP
```
Weaknesses:
- SIM swapping attacks
- SS7 network vulnerabilities
- SMS interception
- Not recommended for high-security applications
NIST deprecated SMS OTP as a sole factor
```

### Hardware Tokens

#### FIDO2 / WebAuthn
Modern standard for hardware authenticators. Phishing-resistant.

```
Registration:
1. Server sends challenge
2. Authenticator creates key pair (private key stays on device)
3. Public key + attestation sent to server
4. Server stores public key

Authentication:
1. Server sends challenge
2. Authenticator signs challenge with private key
3. Server verifies signature with stored public key
```

- **FIDO2** = WebAuthn + CTAP (Client-To-Authenticator Protocol)
- **YubiKey, Touch ID, Face ID** are FIDO2 authenticators
- **Phishing-resistant** — bound to specific origin

### Push Notification MFA
App receives push → user approves/denies → server notified

```
Login attempt detected
     ↓
Push sent to Duo / Okta Verify app
     ↓
User sees: "Login from Chrome, New York. Approve?"
     ↓
User taps Approve → access granted
```

### MFA Bypass Attacks

```
Attack                Description
─────────────────────────────────────────────────────
MFA Fatigue           Spam user with push requests until they approve
SS7 Hijacking         Intercept SMS codes via telecom vulnerabilities
SIM Swapping          Social engineer carrier to transfer phone number
Real-time Phishing    Proxy site captures OTP and relays it instantly
Account Recovery      Bypass MFA via insecure account recovery
```

---

## 21. Passwordless Authentication

Authentication without passwords — uses other factors as primary.

### Magic Links
```
1. User enters email
2. Server generates signed, time-limited token
3. Email sent with link: https://app.com/auth?token=<signed_token>
4. User clicks link → authenticated
5. Token invalidated (one-time use)
```

### Passkeys (FIDO2 / WebAuthn)
Device-bound cryptographic credentials. The future of authentication.

```
Creation:
  Device generates key pair
  Private key → stays in secure enclave (never leaves device)
  Public key  → registered with server
  Protected by: biometric, PIN, or device unlock

Usage:
  Server: "Prove you have this private key"
  Device: Signs challenge (after biometric/PIN confirmation)
  Server: Verifies with stored public key
```

**Advantages:**
- No password to steal, phish, or reuse
- Phishing-resistant (bound to origin)
- Works with biometrics (Touch ID, Face ID, Windows Hello)
- Syncs across devices via iCloud Keychain / Google Password Manager

### Email OTP / Phone OTP
```
User enters email/phone
Server sends 6-digit code
User enters code → authenticated
```

### Biometric-Only Auth (Mobile)
```
App uses device biometric (fingerprint/face)
Biometric → unlocks private key in secure element
Signed challenge sent to server
Server verifies
```

---

## 22. Zero Trust Architecture

"Never trust, always verify" — the principle that no user, device, or network is implicitly trusted, even inside a corporate network.

### Old Model vs Zero Trust

```
Old Perimeter Model:              Zero Trust:
──────────────────────            ──────────────────────────
Corporate network = trusted       Every request verified
Outside network = untrusted       Every time, every resource
Get inside VPN → trust everything Least privilege always
                                  Continuous verification
```

### Zero Trust Principles

```
1. Verify explicitly
   → Authenticate and authorize every request
   → Use all available signals (identity, location, device, time)

2. Least privilege access
   → Grant minimum permissions needed
   → Just-in-time and just-enough access
   → Time-limited access where possible

3. Assume breach
   → Minimize blast radius
   → Segment networks and data
   → Encrypt all traffic, even internal
   → Monitor and detect anomalies
```

### Zero Trust Components

```
Identity Provider (IdP)       → Authenticate users
Device Management (MDM/EDR)   → Verify device health and compliance
Network (Microsegmentation)   → Control lateral movement
Application (ABAC/PBAC)       → Fine-grained access per resource
Data Classification           → Protect sensitive data differently
Monitoring/SIEM               → Continuous behavioral analysis
```

### Continuous Authentication
ZTA doesn't just authenticate at login — it continuously evaluates risk:

```
Login ──→ Every request evaluated for:
           - Is this normal user behavior?
           - Is the device still compliant?
           - Is the location consistent?
           - Any anomalies in access patterns?
           → Re-authenticate if risk score crosses threshold
```

---

## 23. Security Threats & Attacks

### Authentication Attacks

#### Brute Force
```
Attack: Try every possible password combination
Mitigation:
  - Account lockout after N failures
  - CAPTCHA after N failures
  - Rate limiting per IP and per account
  - Strong password policy
  - MFA
```

#### Credential Stuffing
```
Attack: Use leaked username:password pairs from other breaches
        (reused passwords are common)
Mitigation:
  - Breach password checking (HaveIBeenPwned API)
  - MFA
  - Anomaly detection (new location, new device)
  - Rate limiting
```

#### Phishing
```
Attack: Trick user into entering credentials on fake site
Mitigation:
  - FIDO2/WebAuthn (phishing-resistant, origin-bound)
  - Security awareness training
  - Email filtering
  - Anti-phishing browser extensions
```

#### Session Hijacking
```
Attack: Steal session cookie and replay it
Mitigation:
  - HttpOnly cookie (JS can't access)
  - Secure cookie flag (HTTPS only)
  - SameSite cookie attribute
  - Bind session to IP/User-Agent (optional)
  - Short session expiry
```

#### CSRF (Cross-Site Request Forgery)
```
Attack: Trick authenticated user's browser into making unwanted requests
Mitigation:
  - SameSite=Strict cookie attribute
  - CSRF tokens in forms
  - Check Origin/Referer headers
  - Require re-authentication for sensitive actions
```

#### XSS (Cross-Site Scripting) → Token/Cookie Theft
```
Attack: Inject malicious JS to steal tokens from localStorage
Mitigation:
  - Store tokens in HttpOnly cookies (JS cannot access)
  - Content Security Policy (CSP) headers
  - Input validation and output encoding
  - Never use innerHTML with user data
```

#### JWT Attacks
```
Attack: alg:none, alg confusion, weak secret brute force
Mitigation:
  - Validate algorithm explicitly
  - Use RS256 or ES256 (asymmetric)
  - Use strong secrets for HS256 (256+ bits)
  - Always validate all claims (exp, iss, aud)
```

#### Man-in-the-Middle (MitM)
```
Attack: Intercept communication between client and server
Mitigation:
  - HTTPS/TLS everywhere
  - HSTS (HTTP Strict Transport Security)
  - Certificate pinning (mobile apps)
  - mTLS for service-to-service
```

#### Replay Attack
```
Attack: Capture and re-use a valid token/request
Mitigation:
  - Short token expiry
  - Nonces (one-time values in requests)
  - Timestamp validation
  - jti claim tracking
```

#### OAuth Attacks
```
Authorization Code Interception:
  Fix: PKCE for all public clients

Redirect URI Manipulation:
  Fix: Strict redirect URI validation, no wildcards

Open Redirect:
  Fix: Validate redirect URIs against allowlist

CSRF on OAuth:
  Fix: state parameter (must be validated)
```

---

## 24. Cryptography in Auth

### Symmetric Encryption
Same key for encryption and decryption.

```
AES-256-GCM: Used for encrypting session data, cookies
HMAC-SHA256: Used for JWT signatures (HS256), cookie signing

Problem: How to share the key securely?
Solution: Use asymmetric cryptography for key exchange
```

### Asymmetric Cryptography
Key pair: Public key (share freely) + Private key (keep secret).

```
RSA-2048 / RSA-4096:
  Sign with private key → anyone verifies with public key
  Encrypt with public key → only private key holder can decrypt

ECDSA (P-256): Same concept, shorter keys, faster
  Used in: JWT RS256, TLS certificates, WebAuthn/FIDO2

Use in Auth:
  - JWT: Private key signs token, public key (JWKS endpoint) verifies
  - TLS: Server presents certificate signed by CA
  - mTLS: Both client and server present certificates
  - WebAuthn: Device holds private key, server holds public key
```

### JWKS (JSON Web Key Set)
Public endpoint that exposes public keys for JWT verification:

```json
{
  "keys": [
    {
      "kty": "RSA",
      "kid": "key-id-1",
      "use": "sig",
      "alg": "RS256",
      "n": "pjdss8ZaDfEH6K6U7GeW2nxDqR4IP049fk1fK0lndimbMMVBdPv...",
      "e": "AQAB"
    }
  ]
}
```

Any service can download this and verify JWTs without contacting the auth server.

### TLS (Transport Layer Security)
Encrypts all communication between client and server. Essential for all auth systems.

```
TLS 1.3 Handshake:
1. Client Hello (supported cipher suites)
2. Server Hello + Certificate
3. Client verifies certificate against CA
4. Key exchange (ECDHE)
5. Encrypted communication begins

Requirements for auth systems:
✅ TLS 1.2 minimum (TLS 1.3 preferred)
✅ Strong cipher suites only
✅ HSTS header
✅ Certificate from trusted CA
✅ Certificate expiry monitoring
```

### Hashing in Auth

```
Passwords        → bcrypt / Argon2 / scrypt (slow + salted)
Token IDs        → SHA-256 (fast, store hash of opaque tokens)
TOTP             → HMAC-SHA1 (time-based OTP generation)
JWT Signature    → HMAC-SHA256 or RSA-SHA256
```

---

## 25. Identity Providers (IdP)

An Identity Provider is a system that creates, maintains, and manages identity information and provides authentication services.

### Types of Identity Providers

#### Enterprise IdPs
- **Microsoft Entra ID (Azure AD)** — Microsoft ecosystem, SAML, OIDC, OAuth
- **Okta** — Cloud IAM, SAML, OIDC, SCIM provisioning
- **PingIdentity** — Enterprise SSO, MFA
- **ADFS (Active Directory Federation Services)** — On-premise, SAML, WS-Federation
- **OneLogin** — Cloud IAM

#### Social IdPs
- Google (OIDC)
- Apple (OIDC)
- Facebook (custom OAuth)
- GitHub (custom OAuth)
- Twitter/X

#### Open Source IdPs
- **Keycloak** — Full-featured, SAML + OIDC, self-hosted
- **Authentik** — Modern, self-hosted
- **Gluu** — Enterprise open source
- **Ory Hydra/Kratos** — Headless, API-first

#### Auth-as-a-Service
- **Auth0** (Okta)
- **Firebase Authentication**
- **AWS Cognito**
- **Supabase Auth**
- **Clerk**

### SCIM (System for Cross-domain Identity Management)
Protocol for automating user provisioning/deprovisioning across systems:

```
HR system creates new employee:
  ↓
SCIM push to IdP (Okta):
  POST /scim/v2/Users
  { "userName": "jane.doe", "active": true, "groups": ["engineering"] }
  ↓
IdP syncs to all connected apps:
  → GitHub Org: Add jane.doe
  → Salesforce: Create account
  → Slack: Invite to workspace
  → JIRA: Create account
```

When employee leaves:
```
HR deactivates employee
  ↓
SCIM PATCH: { "active": false }
  ↓
All apps deprovisioned immediately
```

---

## 26. Federation

Identity federation allows authentication across different domains and organizations.

### What is Federation?

```
Company A uses Okta
Company B uses Azure AD

Without federation: Each employee needs accounts in both systems
With federation: Company B trusts Company A's identity assertions
                 Company A employees can access Company B's resources
```

### Federation vs SSO

```
SSO:         One IdP, multiple apps within the SAME organization
Federation:  Trust BETWEEN different organizations/IdPs
             SSO is often a component of federation
```

### Trust Models

```
Direct Trust:
  SP directly trusts a specific IdP
  Simple, but doesn't scale

Federation Hub:
  All parties trust a central hub
  Hub brokers trust between parties
  e.g., eduGAIN (academic federation), InCommon

Web of Trust:
  Each party evaluates others based on metadata and certificates
```

### WS-Federation
Microsoft protocol for federated identity, used by ADFS:

```
User → App (SP) → ADFS (IdP) → Token Issued → App grants access
```

### Token Translation
Different parts of a federated system may use different token formats:

```
Client sends SAML assertion →
  Gateway translates to JWT →
    Backend microservice uses JWT
```

---

## 27. How Everything Connects

This section shows how all the concepts above work together in real-world scenarios.

### Connection Map

```
┌─────────────────────────────────────────────────────────────────────┐
│                         IDENTITY LAYER                              │
│  IdP (Okta/Keycloak/Azure AD) ←── SCIM ──→ User Directory (LDAP)  │
│           │                                                         │
│     SAML / OIDC / OAuth 2.0                                        │
└───────────────────────────────────────────────────────────────────┘
                     │           │
          ┌──────────┘           └───────────────┐
          ↓                                       ↓
┌──────────────────────┐             ┌──────────────────────────┐
│     SSO Layer        │             │     API Auth Layer        │
│  (Web App Login)     │             │   (Bearer Token / mTLS)   │
│  Session Cookies     │             │   API Gateway             │
│  ID Tokens (OIDC)    │             │   JWT Validation          │
└──────────────────────┘             └──────────────────────────┘
          │                                       │
          ↓                                       ↓
┌──────────────────────────────────────────────────────────────────┐
│                     AUTHORIZATION LAYER                           │
│                                                                   │
│   RBAC (roles in JWT) → coarse-grained                           │
│       ↓                                                           │
│   ABAC (attributes + context) → medium-grained                   │
│       ↓                                                           │
│   OPA / Cedar (policy engine) → fine-grained, dynamic            │
│       ↓                                                           │
│   ACL (per-resource permissions) → finest grained (row-level)    │
└──────────────────────────────────────────────────────────────────┘
```

### Complete Login Flow (Modern Web App)

```
1. [User] clicks "Login"
2. [App] redirects to IdP (OIDC Authorization Code + PKCE flow)
3. [IdP] shows login form
4. [User] enters credentials
5. [IdP] checks if MFA required (adaptive/risk-based)
6. [User] completes MFA (TOTP / WebAuthn)
7. [IdP] creates SSO session, issues authorization code
8. [App] exchanges code for access_token + id_token + refresh_token
9. [App] validates id_token (JWT): signature, iss, aud, exp, nonce
10. [App] extracts user identity from id_token (sub, email, name)
11. [App] creates application session, stores tokens securely
12. [App] determines user's roles and permissions (from JWT claims or DB lookup)
13. [User] sees authenticated UI

---

Subsequent API Requests:
14. [App Frontend] sends access_token in Authorization: Bearer header
15. [API] validates JWT: signature (JWKS), exp, iss, aud, scope
16. [API] extracts user identity and roles from JWT claims
17. [API] checks authorization:
    - RBAC: does user have required role?
    - ABAC: do attributes satisfy policy?
    - Resource check: does user own this resource?
18. [API] returns data if authorized

---

Token Refresh:
19. access_token expires (15-60 min)
20. App sends refresh_token to IdP /token endpoint
21. IdP validates refresh_token (not revoked, not expired)
22. IdP issues new access_token (+ rotated refresh_token)
23. App updates stored tokens

---

Logout:
24. App calls IdP /revoke with refresh_token
25. App clears local session and tokens
26. App calls IdP /logout (Single Logout)
27. IdP invalidates SSO session
28. All other apps' sessions become invalid (SLO)
```

### OAuth 2.0 + OIDC + JWT Connection

```
OAuth 2.0        → Framework for token-based delegated authorization
OIDC             → Built on OAuth 2.0, adds identity (ID Token)
JWT              → Token format used for access tokens and ID tokens
JWKS             → Public key endpoint to verify JWT signatures
Scopes           → OAuth concept, define access level in tokens
Claims           → JWT concept, data inside the token
```

### Authentication → Authorization Pipeline

```
HTTP Request arrives at API
          │
          ▼
┌─────────────────────┐
│  Extract Token      │  Get JWT from Authorization header
└─────────────────────┘
          │
          ▼
┌─────────────────────┐
│  Verify Signature   │  Fetch JWKS, verify RS256 signature
└─────────────────────┘
          │
          ▼
┌─────────────────────┐
│  Validate Claims    │  Check exp, iss, aud, nbf
└─────────────────────┘
          │
          ▼
┌─────────────────────┐
│  Extract Identity   │  sub, email, roles, permissions
└─────────────────────┘
          │
          ▼
┌─────────────────────┐
│  Authorization      │  RBAC: check role
│  Decision           │  ABAC: check attributes + context
│                     │  Resource: check ownership
└─────────────────────┘
          │
          ▼
    ALLOW or DENY
```

### When to Use What

```
Use Case                          Recommended Approach
────────────────────────────────────────────────────────────────────
Web app user login                OIDC (Authorization Code + PKCE)
Mobile app login                  OIDC (Authorization Code + PKCE)
Server-to-server API              OAuth 2.0 Client Credentials
Enterprise SSO                    SAML 2.0 or OIDC
Social login                      OIDC (Google, Apple, GitHub)
API authentication (simple)       API Key or Bearer Token (JWT)
High security API                 mTLS + JWT
Simple role control               RBAC
Complex conditional access        ABAC
Policy managed by separate team   PBAC (OPA/Cedar)
Per-resource permissions          ACL
Organization-wide SSO             SSO (SAML or OIDC) + Federation
Eliminate passwords               Passkeys (FIDO2/WebAuthn)
Add security layer to any auth    MFA (TOTP or FIDO2)
Zero trust internal services      mTLS + short-lived JWT
```

---

## Quick Reference Cheat Sheet

```
Authentication Hierarchy (weakest → strongest):
  Password → Password+SMS → Password+TOTP → Password+FIDO2 → Passkey

Authorization Hierarchy (coarsest → finest):
  RBAC → PBAC → ABAC → ACL

Token Hierarchy (least secure → most secure):
  API Key → Opaque Token → JWT (HS256) → JWT (RS256) → mTLS Certificate

OAuth 2.0 Grant Types:
  Web App          → Authorization Code
  SPA / Mobile     → Authorization Code + PKCE
  Server-to-Server → Client Credentials
  IoT/TV           → Device Authorization
  (Legacy SPA)     → Implicit (DEPRECATED)

Standard Ports:
  HTTP  → 80   (never use for auth)
  HTTPS → 443  (always)
  LDAP  → 389 / LDAPS → 636
  RADIUS → 1812/1813

Key Standards Bodies:
  IETF  → OAuth 2.0 (RFC 6749), JWT (RFC 7519), PKCE (RFC 7636)
  OASIS → SAML 2.0
  FIDO Alliance → FIDO2, WebAuthn, Passkeys
  NIST  → Password guidelines (SP 800-63)
  W3C   → WebAuthn specification
```

---

*End of Authentication & Authorization Comprehensive Notes*
