[# Module 4 — Identity, Authentication, and Access Control

### Module Focus

This module explains the critical shift from traditional perimeter-based network security to identity-centric security (Zero Trust). It covers the mechanics of proving who a user is (Authentication) and determining what they are allowed to do (Authorization). The module details the weaknesses of password-based systems, how to defend against identity-based attacks using Multi-Factor Authentication (MFA), and the foundational models used to enforce access control in modern systems.

### 1) Core Idea

Identity is the new security perimeter. Traditional security focused on protecting the internal network and assuming users inside were trusted. Today, cloud services, remote access, and personal devices mean the network boundary is no longer reliable. Modern security focuses on continuously verifying user identity and limiting access dynamically.

### 2) Identity vs. Account

- **Identity:** The real-world entity (person or system).
    
- **Account:** How that identity is represented in a specific system. A single identity can have multiple accounts across different platforms, each with different permissions, roles, and security settings.
    

### 3) Identification, Authentication & Authorization

- **Identification:** The act of claiming an identity (e.g., entering a username).
    
- **Authentication (AuthN):** The process of verifying that claim (e.g., entering a password). It answers: _Who are you?_.
    
- **Authorization (AuthZ):** Determining what allowed actions and permissions are granted after successful authentication. It answers: _What are you allowed to do?_.
    

### 4) The AAA Model

The Access Management Framework consists of three pillars:

1. **Authentication:** Verifies the identity of the user or system.
    
2. **Authorization:** Determines the allowed actions and permissions.
    
3. **Accounting:** Records user activity for monitoring and auditing.
    

### 5) Trust Boundaries & Sessions

- **Trust Boundary:** A point where trust assumptions change (e.g., between untrusted user input and a validated data flow). Systems should never automatically trust user input or external client-side data.
    
- **Session:** Created after successful authentication to maintain the user's authenticated state across requests (e.g., cookies, API tokens).
    

### 6) Passwords & Their Weaknesses

Passwords are easy to deploy and familiar, but they rely heavily on unreliable human behavior.

- **Fundamental Weaknesses:** Users choose weak, predictable passwords and often reuse them across multiple services. Passwords represent a single point of failure.
    
- **Password Storage:** Systems must _never_ store passwords in plaintext. They must use **Hashing** (converting passwords into a fixed, irreversible value) and **Salting** (adding random data before hashing to prevent pattern attacks).
    

### 7) Common Password Attacks

- **Brute-Force:** Testing all possible password combinations.
    
- **Dictionary Attacks:** Using lists of common passwords or known leaked credentials.
    
- **Credential Stuffing:** Using credentials leaked from previous breaches and testing them on other platforms using automated tools.
    
- **Phishing:** Tricking users into revealing their passwords via fake login pages or email impersonation.
    
- **Malware/Keyloggers:** Capturing passwords directly from infected endpoints.
    

### 8) Multi-Factor Authentication (MFA) & Passwordless

Because passwords are a single point of failure, security is improved by requiring multiple independent proofs of identity (MFA).

- **Authentication Factors:**
    
    - _Something You Know:_ Password, PIN.
        
    - _Something You Have:_ Hardware token, Authenticator App (OTP), Phone.
        
    - _Something You Are:_ Biometrics (Fingerprint, Face recognition).
        
- **Passwordless Authentication:** The goal is to eliminate passwords entirely using cryptographic authentication like FIDO2 and Passkeys.
    

### 9) Access Control Fundamentals & Principles

Access control regulates which **Subjects** (users/processes) can perform which **Actions** (read/write/delete) on which **Resources** (files/databases). It is governed by core principles:

- **Principle of Least Privilege:** Users should be given only the permissions they strictly need, reducing risk in case of mistakes or compromise.
    
- **Need-to-Know:** Access is granted only if it is necessary for a specific task (common in military/healthcare).
    
- **Separation of Duties:** Critical tasks are divided among multiple users to prevent a single user from having excessive control and to reduce fraud.
    

### 10) Access Control Models

|**Model**|**How it Works**|**Flexibility**|**Security**|**Typical Use**|
|---|---|---|---|---|
|**DAC** (Discretionary)|Access decisions are controlled by the resource owner.|High|Low–Medium|Personal systems, Windows/Linux files.|
|**MAC** (Mandatory)|Enforced strictly by the system based on security labels/clearance. Users cannot override.|Low|High|Military, government.|
|**RBAC** (Role-Based)|Permissions are assigned to roles, and users inherit permissions through roles.|Medium|Medium–High|Enterprises, corporate structures.|
|**ABAC** (Attribute-Based)|Decisions are based dynamically on user, resource, and environment attributes (time, location).|Very High|High|Cloud, modern complex systems.|

### 11) Identity Infrastructure & Standards

To manage identities securely at scale, modern environments use specialized infrastructure:

- **IdP (Identity Provider):** A system that manages user identities and authenticates users (e.g., Google, Microsoft).
    
- **SSO (Single Sign-On):** Allows users to log in once and access multiple services, reducing password fatigue but creating a single point of failure.
    
- **Identity Federation:** Allows multiple organizations to trust a shared identity (e.g., using university credentials for external software).
    
- **Standards:** OAuth 2.0 (Authorization), OpenID Connect (Authentication), SAML (Identity Federation).
    

### 12) Attacks on Identity & Access Control

- **Broken Access Control:** When access restrictions are not enforced, allowing users to perform actions beyond their permissions.
    
- **IDOR (Insecure Direct Object Reference):** When an application exposes internal identifiers (like a URL parameter `?id=123`), and an attacker changes it to access someone else's data without authorization checks.
    
- **Privilege Escalation:** Gaining higher access rights than intended. Can be _Vertical_ (user to admin) or _Horizontal_ (user to another user).
    
- **Session Hijacking:** Stealing session cookies or intercepting network traffic to take control of a valid user session without needing the password.
    

### 13) Final mental model

Entire Module in One Line: Identity is the new perimeter; we authenticate _who_ you are using robust methods like MFA, and we authorize _what_ you can do using strict, principle-driven access control models (like RBAC/ABAC) to limit potential damage.

### 14) Important Words Only

|**Word**|**Specific meaning**|**Example**|
|---|---|---|
|**Identity**|The digital representation of a real-world entity.|A human user, API, or IoT device.|
|**Authentication (AuthN)**|The process of verifying an identity claim.|Checking a password or biometric.|
|**Authorization (AuthZ)**|Determining allowed actions after authentication.|Checking if a user can view a file.|
|**Hashing**|One-way transformation of a password for secure storage.|Converting "password123" into fixed ciphertext.|
|**Salting**|Adding random data before hashing to prevent pattern attacks.|Ensuring two users with the same password have different hashes.|
|**Credential Stuffing**|Using leaked credentials from one breach to access other platforms.|Automated bot testing leaked email/passwords on banks.|
|**MFA**|Requiring multiple independent proofs of identity.|Password + SMS Code + Fingerprint.|
|**Least Privilege**|Giving users only the minimum permissions needed.|Support staff cannot change system settings.|
|**RBAC**|Role-Based Access Control; permissions assigned by job role.|Assigning "Accountant" role rather than per-user rules.|
|**ABAC**|Attribute-Based Access Control; permissions based on dynamic variables.|Allowing access only from the office IP during 9-to-5.|
|**Zero Trust**|Security model assuming no implicit trust; verify every request.|Identity checked even if user is on the corporate Wi-Fi.|
|**IdP**|Identity Provider; a system that manages identities.|Microsoft Entra, Google Workspace.|
|**SSO**|Single Sign-On; logging in once for multiple apps.|University login opens Email, Moodle, and Library.|
|**IDOR**|Insecure Direct Object Reference; exploiting predictable data identifiers.|Changing `user=1` to `user=2` in a URL to steal data.|

### 15) Very short closing summary

This module emphasizes that modern security cannot rely on network borders. Instead, identity is the foundation. It requires strong authentication (moving away from passwords to MFA/Passwordless) and strict authorization (using structured access control models and principles like least privilege). Because identity controls access to everything, attackers heavily target credentials and session logic, requiring defenders to employ Zero Trust architecture, identity federation, and continuous verification.](<# Module 4 — Identity, Authentication, and Access Control

> [!summary] Module Focus
> Identity is now the main security boundary. This module explains how systems identify users, verify them with authentication, decide what they can do with access control, and protect identities with MFA, SSO, federation, and modern identity infrastructure. It also shows how attackers target identity first because logging in is often easier than breaking in.

---

## 1. Why Identity Is a Primary Target

Why hack when you can log in?

Modern attackers often target user accounts instead of attacking systems directly. Stolen credentials can bypass many defenses and give attackers access to:
- sensitive data
- internal systems
- privileged operations

Many large breaches begin with compromised authentication. Weak identity protection can expose the whole system.  

### Simple example
If an attacker steals a university login, they may access email, grades, internal platforms, and other connected services.

---

## 2. Evolution of Security Thinking

Traditional security focused on the internal network perimeter:
- inside the network = trusted
- outside the network = untrusted

That model is weaker today because systems now use:
- cloud services
- remote access
- personal devices
- mobile connections

So security now focuses more on verifying identity continuously instead of trusting network location.

> [!important] Main Shift
> The old model trusted where a user was located. The modern model trusts who the user is, and verifies access continuously.

---

## 3. Core Concepts

### Identity
Identity is the digital representation of an entity in a system.

It can represent:
- a human user
- a software service
- a physical device

Identity is usually linked to identifiers like:
- username
- email address
- unique ID

### Identity vs Account

| Term | Meaning | Example |
|---|---|---|
| Identity | The real-world entity | A student or service |
| Account | The representation of that identity in a system | A university login |

A single identity can have many accounts across different platforms, and each account may have different roles, permissions, and security settings.

### Simple example
A student may have:
- a university account
- an email account
- a library account

All belong to the same person, but each account may have different permissions.

---

## 4. Identification, Authentication, Authorization

### Identification
Claiming an identity.

Example: entering a username.

### Authentication
Proving the claim is true.

Example: entering a password or MFA code.

### Authorization
Deciding what the authenticated user is allowed to do.

Example: a student can view grades but cannot modify them.

> [!important] Key Distinction
> Authentication answers **Who are you?**  
> Authorization answers **What are you allowed to do?**

### Simple example
A user may log in successfully, but still be blocked from accessing admin functions.

---

## 5. AAA Model

| AAA Component | Meaning |
|---|---|
| Authentication | Verifies identity |
| Authorization | Determines allowed actions |
| Accounting | Records activity for monitoring and auditing |

AAA is an access management framework used in secure systems.

---

## 6. Subjects, Resources, and Actions

Access control decisions are based on three elements:

| Element | Meaning | Example |
|---|---|---|
| Subject | The entity requesting access | User, process |
| Resource / Object | The target being accessed | File, database, API |
| Action | The operation being requested | Read, write, delete |

### Example
A student is the subject, a grade report is the resource, and reading it is the action.

---

## 7. Sessions

After successful authentication, the system creates a session.

A session:
- keeps the user authenticated across requests
- improves usability
- often uses cookies or tokens

### Common implementations
- session cookies in web apps
- API tokens

### Security note
Sessions are useful, but dangerous if stolen or mismanaged.

### Simple example
After logging in once, you stay signed in while moving through pages because the session remembers you.

---

## 8. Trust Boundaries

> [!important] Trust Boundary
> A trust boundary is where trust assumptions change. Every boundary crossing should be validated and verified.

Systems should not automatically trust:
- user input
- external systems
- client-side data

Many vulnerabilities happen because the system trusts something it should not.

### Simple example
Data coming from the browser should never be trusted automatically, because the user can change it.

---

## 9. Password-Based Authentication

Passwords are widely used because they are:
- familiar
- cheap to deploy
- easy for users to understand

But password systems have many weaknesses.

### Fundamental weaknesses
- weak or predictable passwords
- reuse across sites
- phishing
- credential stuffing
- brute force
- malware theft
- poor storage practices

---

## 10. Weak Passwords and Predictability

Attackers exploit weak passwords with dictionary-based attacks.

Common passwords are often simple patterns like:
- 123456
- password
- qwerty
- abc123

### Simple example
If a user uses “password123”, an attacker does not need advanced tools to guess it.

---

## 11. Dictionary Attacks

A dictionary attack uses:
- lists of common passwords
- leaked credentials
- pattern variations

This is much faster than brute force and very effective against real users.

### Simple example
An attacker tries “welcome1”, “welcome123”, and “welcome2025” instead of every possible character combination.

---

## 12. Credential Stuffing

Credential stuffing uses usernames and passwords leaked from one breach and tries them on other platforms.

### Why it works
Many people reuse passwords.

### Simple example
A password stolen from a shopping site may also work on email or social media if the user reused it.

---

## 13. Phishing Attacks

Phishing tricks users into giving away their passwords.

### Example
A fake login page looks like a real bank or university page, but it sends the password to the attacker.

---

## 14. Password Capture via Malware

Malware can steal passwords from infected devices.

### Common examples
- keyloggers
- browser credential stealers

This attack happens at the endpoint, not the server.

### Important idea
Even strong passwords can be stolen if the device is compromised.

---

## 15. Password Storage

> [!warning] Critical Mistake
> Systems must never store passwords in plaintext.

If a database is compromised and passwords are stored plainly, every password is exposed immediately.

### Secure storage
Passwords should be stored using hashing.

### Why hashing matters
Hashing turns a password into a fixed, irreversible value.

---

## 16. Hashing and Salting

### Hashing
A one-way transformation that stores a password as a hash instead of the original password.

### Salting
Adding random data before hashing so identical passwords do not produce identical stored values.

### Simple example
Two users with the same password should still have different stored hashes if salts are used.

---

## 17. Why Passwords Are Not Enough

Passwords alone are not strong enough because:
- users choose weak passwords
- users reuse passwords
- passwords can be guessed, stolen, or phished
- malware can capture them
- good systems can still be attacked through the user

So stronger authentication is needed.

---

## 18. Multi-Factor Authentication (MFA)

> [!important] MFA
> Multi-Factor Authentication requires two or more independent proofs of identity.

If one factor is compromised, the others still protect the account.

### Why MFA helps
It greatly reduces the risk of account compromise.

### Common factors
| Factor type | Example |
|---|---|
| Something you know | Password, PIN |
| Something you have | Phone, token, hardware key |
| Something you are | Fingerprint, face recognition |

### Examples of MFA
- password + SMS code
- password + authenticator app
- fingerprint + device unlock
- banking OTP confirmation
- corporate VPN token verification

---

## 19. OTPs, Hardware Tokens, and Authenticator Apps

### OTP
One-Time Passwords are temporary codes valid for a short time.

They can be:
- SMS-based
- app-generated

### Hardware tokens / authenticator apps
These are generally more secure than SMS because they do not depend on the mobile network.

### Simple example
A login code generated by an authenticator app changes every few seconds.

---

## 20. Biometrics

Biometrics use physical characteristics like:
- fingerprint
- face recognition

### Strengths
- convenient
- fast
- cannot be forgotten like a password

### Limitations
- cannot be changed easily if compromised
- may raise privacy concerns

### Simple example
If a fingerprint template is leaked, you cannot simply “reset” your fingerprint like a password.

---

## 21. Limitations of MFA

MFA improves security, but it does not remove all risk.

### Possible weaknesses
- SMS interception
- device compromise
- phishing
- poor implementation
- user inconvenience

### Important example
A fake login page can capture both the password and OTP if the attacker relays them quickly.

---

## 22. Phishing Against MFA

Attackers can bypass MFA using real-time phishing.

### How it works
1. User enters password on a fake site
2. User enters OTP too
3. Attacker forwards both instantly to the real site
4. The attack succeeds even though MFA is enabled

This is why MFA must be combined with good anti-phishing practices.

---

## 23. Passwordless Authentication

> [!summary] Passwordless Goal
> Passwordless authentication aims to remove reliance on passwords entirely and use stronger methods such as secure devices, biometrics, passkeys, and FIDO2.

### Benefits
- stronger security
- better user experience
- less password reuse
- less phishing risk

---

## 24. Access Control Fundamentals

> [!important] Access Control
> Access control regulates who can access what resources and what actions they are allowed to perform.

Access control happens after authentication succeeds.

### Why it matters
Without access control, any authenticated user could potentially access everything.

### Main goals
- prevent unauthorized access
- limit damage from compromised accounts
- enforce organizational policy
- support compliance

---

## 25. Authentication vs Access Control

| Concept | Question answered |
|---|---|
| Authentication | Who are you? |
| Access control | What can you do? |

### Example
A user may log in successfully, but access control decides whether they can open the admin panel.

---

## 26. Basic University Example

| Role | Allowed actions |
|---|---|
| Student | View own grades |
| Instructor | Modify grades |
| Admin | Manage users |

Access is based on:
- identity
- role

Incorrect configuration can expose or modify sensitive data.

---

## 27. Access Control Matrix

The access control matrix is a conceptual model that shows permissions.

| Structure | Meaning |
|---|---|
| Rows | Subjects |
| Columns | Resources |
| Cells | Allowed actions |

It helps visualize who can do what in a system.

---

## 28. Least Privilege

> [!important] Least Privilege
> Users should receive only the permissions they need, and nothing extra.

### Why it matters
It reduces damage from:
- mistakes
- compromised accounts
- misuse

### Simple example
A support worker should not have administrator access if support tasks do not require it.

---

## 29. Need-to-Know

Need-to-know means access is granted only when it is necessary for the task.

Even within the same role, access may differ depending on what is needed.

### Example
In healthcare, a doctor may not need access to every department’s full records.

---

## 30. Separation of Duties

Critical tasks are divided among multiple users.

### Why it matters
It prevents one person from having too much control and reduces fraud risk.

### Simple example
The person who requests a payment should not be the same person who approves it.

---

## 31. Policy vs Mechanism

| Term | Meaning | Example |
|---|---|---|
| Policy | What should be allowed | “Students cannot modify grades” |
| Mechanism | How the rule is enforced | Application code or access rules |

A secure system needs both correct policies and proper enforcement.

---

## 32. Centralized vs Decentralized Access Control

| Model | Meaning | Strength | Weakness |
|---|---|---|---|
| Centralized | One system manages access decisions | Easier consistency | Can be a single control point |
| Decentralized | Multiple systems manage access independently | Flexible | Harder to control and audit |

---

## 33. Access Control Models

Different systems need different permission models.

### Main models
- DAC
- MAC
- RBAC
- ABAC

---

## 34. DAC — Discretionary Access Control

In DAC, the resource owner controls access.

### Example
A user creates a file and decides who can read or modify it.

### Strengths
- flexible
- easy to use
- users control their data

### Limitations
- users may grant too much access
- difficult to enforce strict policy
- vulnerable to accidental sharing

### Real-world example
Windows file permissions and Linux ownership are common DAC-style systems.

---

## 35. MAC — Mandatory Access Control

In MAC, the system enforces access decisions using labels and classifications.

Users cannot override the rules.

### Example
A user with “Confidential” clearance cannot access “Top Secret” data.

### Strengths
- strong enforcement
- prevents unauthorized sharing

### Limitations
- rigid
- difficult in dynamic environments
- not user-friendly for general applications

---

## 36. RBAC — Role-Based Access Control

In RBAC, permissions are assigned to roles, and users inherit permissions from their roles.

### Example
An employee gets access because they are in the “HR” role or “Admin” role.

### Strengths
- easy to manage at scale
- fits organizations well
- reduces assignment complexity

### Limitations
- can create too many roles
- less flexible for context-based decisions

---

## 37. ABAC — Attribute-Based Access Control

In ABAC, access depends on attributes.

### Attributes can include:
- user attributes
- resource attributes
- environment attributes

### Example
Allow access if:
- the user is a doctor
- the resource is patient data
- the time is during working hours

### Strengths
- very flexible
- context-aware
- suitable for modern complex systems

### Limitations
- more complex to design
- harder to debug
- needs clear policy definition

---

## 38. Access Control Model Comparison

| Model | Control basis | Flexibility | Security strength | Typical use |
|---|---|---|---|---|
| DAC | Resource owner | High | Low–medium | Personal systems |
| MAC | System labels | Low | High | Military, government |
| RBAC | Roles | Medium | Medium–high | Enterprises |
| ABAC | Attributes and policies | Very high | High | Cloud, modern systems |

---

## 39. Identity as the New Security Perimeter

Modern security no longer relies mainly on the internal network boundary.

Instead, identity becomes the main trust anchor.

### Why this changed
Users now access systems from:
- home networks
- mobile devices
- cloud environments
- public internet

So security decisions are now based more on **who the user is** than **where they are**.

---

## 40. Traditional Security Model vs Modern Identity-Centric Security

### Traditional model
- inside network = trusted
- outside network = untrusted
- firewalls and segmentation protect the perimeter

### Limitation
Attackers can bypass the perimeter by:
- stealing credentials
- compromising endpoints

So “inside vs outside” is no longer enough.

---

## 41. Identity as the New Perimeter

> [!important] Modern Security Rule
> Every access request must be authenticated and authorized. Identity is the primary trust anchor, and access should be evaluated continuously, not only once at login.

### Key idea
Security decisions are based on:
- who the user is
- not just where they are located

---

## 42. Zero Trust

> [!summary] Zero Trust
> Zero Trust means “never trust, always verify.” No implicit trust is given based on network location or device ownership.

Every request must be validated.

---

## 43. Key Principles of Identity-Centric Security

- continuous verification of identity
- strong authentication like MFA
- least privilege access
- monitoring and logging
- dynamic decisions based on risk

### Simple example
If someone logs in from a new country, the system may require extra verification.

---

## 44. Risk-Based and Adaptive Authentication

Authentication can change based on context:
- user location
- device
- time of access
- behavior patterns

### Example
A login from a new country may trigger an additional challenge.

This improves both security and usability.

---

## 45. Continuous Authentication

Traditional model:
- authenticate once at login

Modern model:
- verify identity during the session too

### What it can detect
- unusual behavior
- suspicious activity

### Possible response
- re-authentication
- session termination

---

## 46. Identity Infrastructure

Modern systems need centralized identity management because manual identity handling does not scale.

Identity infrastructure helps with:
- secure authentication
- efficient access decisions
- central management

---

## 47. Identity Provider (IdP)

> [!important] Identity Provider
> An Identity Provider is a system that manages identities, authenticates users, and provides identity information to applications.

### Examples
- Google
- Microsoft
- university login systems

---

## 48. Single Sign-On (SSO)

SSO allows users to log in once and then access multiple services.

### Benefits
- fewer passwords to remember
- less password reuse
- better productivity
- centralized authentication

### Risk
If the main account is compromised, all connected services can be affected.

### Simple example
A student logs in once and can access email, Moodle, and library services.

---

## 49. Identity Federation

Identity federation lets different systems trust a shared identity.

### Example
You authenticate with one organization and access another service through trust between systems.

This is common in partnerships and enterprise environments.

---

## 50. Identity and Authorization Standards

Modern identity systems use standards so systems can work together securely.

| Standard | Main purpose |
|---|---|
| OAuth 2.0 | Authorization |
| OpenID Connect (OIDC) | Authentication |
| SAML | Identity federation |

These standards support:
- SSO
- secure communication
- trusted identity exchange

---

## 51. Attacks on Identity and Access Control

Identity systems are attractive targets because they control access to everything.

If identity is compromised, attackers get legitimate access.

### Common attack themes
- authentication weaknesses
- authorization flaws
- broken access control

These attacks often bypass traditional defenses.

---

## 52. Broken Access Control

> [!important] Broken Access Control
> Broken access control happens when access restrictions are not correctly enforced, allowing users to do things beyond their permissions.

### Examples
- accessing another user’s data
- modifying unauthorized resources

This is one of the most common and serious vulnerabilities.

---

## 53. IDOR — Insecure Direct Object Reference

IDOR happens when internal identifiers are exposed and the system does not check ownership correctly.

### Example
A URL like:
`/profile?id=123`

An attacker changes it to:
`/profile?id=124`

If the system does not verify ownership, it may expose another user’s data.

---

## 54. Privilege Escalation

Attackers gain higher access than intended.

### Types
| Type | Meaning |
|---|---|
| Vertical escalation | User becomes admin |
| Horizontal escalation | User accesses another user’s data |

### Causes
- misconfigured permissions
- logic flaws

---

## 55. Session Hijacking

An attacker takes over a valid user session.

### How it happens
- stolen session cookies
- network interception

The system thinks the attacker is the legitimate user.

### Simple example
If someone steals your session cookie, they may act as you without knowing your password.

---

## 56. Token Theft and Misuse

Modern systems use tokens to represent authenticated identity.

If a token is stolen, it can be reused.

### Common causes
- insecure storage
- exposure in URLs
- exposure in logs

---

## 57. Weak Authorization Checks

Sometimes the system checks authentication but not authorization properly.

### Bad assumption
“If the user is authenticated, access is allowed.”

This can expose sensitive data widely.

### Example
A logged-in user is able to access all records because the system forgets to check ownership or role.

---

## 58. Attack Chains

Real attacks often combine multiple weaknesses.

### Example chain
- phishing steals credentials
- login gives access
- IDOR exposes another user’s data

Attackers often use small weaknesses together to create a bigger compromise.

---

## 59. Defensive Perspective

Good defense requires:
- strong authentication
- proper authorization checks
- request validation
- least privilege
- monitoring for suspicious behavior

---

## 60. Final Takeaways

> [!summary] Final Idea
> Identity is the core of modern security. Authentication verifies identity, access control limits actions, and weak design in either one can lead to compromise. Secure systems need strong authentication, continuous verification, least privilege, proper enforcement, and identity-aware infrastructure.

---

## 61. Important Words Only

| Word | Specific meaning | Example |
|---|---|---|
| Identity | Digital representation of a user, service, or device | Student login |
| Account | System representation of an identity | University account |
| Identification | Claiming an identity | Entering username |
| Authentication | Proving the identity claim | Password, MFA |
| Authorization | Deciding what a user can do | Allow admin access or not |
| Accounting | Logging activity for auditing | Security logs |
| Session | Authenticated state maintained across requests | Logged-in browser session |
| Trust boundary | Point where trust changes | Browser to server |
| Password authentication | Login using a secret password | Website login |
| Dictionary attack | Trying common passwords | password123 |
| Credential stuffing | Reusing leaked credentials on other sites | Breach reuse |
| Phishing | Tricking users into revealing secrets | Fake login page |
| Malware capture | Stealing passwords from infected devices | Keylogger |
| Hashing | One-way storage of passwords | Stored password hash |
| Salting | Adding random data before hashing | Different hash for same password |
| MFA | Multiple independent identity proofs | Password + OTP |
| OTP | Temporary one-time code | App code |
| Token | Digital proof of authenticated identity | API token |
| Biometric | Physical characteristic used for login | Fingerprint |
| Access control | Regulating who can access what | Student reads own grades |
| Subject | The requester | User or process |
| Resource | The item being accessed | File or API |
| Action | Operation on the resource | Read, write, delete |
| Least privilege | Minimum permissions needed | Support staff cannot edit grades |
| Need-to-know | Access only when necessary | Restricted medical access |
| Separation of duties | Split critical tasks among multiple people | One approves, another executes |
| Policy | What should be allowed | Students cannot modify grades |
| Mechanism | How policy is enforced | App code or ACL |
| DAC | Owner controls access | File sharing |
| MAC | System-enforced classification | Military data labels |
| RBAC | Permissions based on role | Admin, teacher, student |
| ABAC | Permissions based on attributes | Doctor during working hours |
| Identity provider | System that authenticates users | Google, Microsoft |
| SSO | One login for many services | University portal access |
| Federation | Trusting identity across systems | Partner institutions |
| OAuth 2.0 | Authorization standard | Access to resources |
| OIDC | Authentication standard | Login identity proof |
| SAML | Federation standard | Enterprise SSO |
| Broken access control | Permissions not enforced correctly | Accessing other users’ data |
| IDOR | Using guessed object IDs without ownership checks | /profile?id=124 |
| Privilege escalation | Gaining higher access | User to admin |
| Session hijacking | Taking over a valid session | Stolen cookie |
| Token theft | Stealing and reusing a token | Reused bearer token |
| Zero Trust | Never trust, always verify | Every request checked |
| Continuous authentication | Verifying identity during the session | Re-check behavior |
| Adaptive authentication | Changing checks based on risk | Extra check from new country |

---

## 62. Very short closing summary

This module shows that identity is now the main security boundary. Strong systems verify users, control what they can do, apply least privilege, use MFA and modern identity infrastructure, and defend against attacks like phishing, IDOR, session hijacking, and broken access control.>)