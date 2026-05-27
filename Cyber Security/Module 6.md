# I3336 – Introduction to Cybersecurity

## Module 6: Web Security Fundamentals

**Ahmad Fadlallah | 2025–2026**

---

## Module Overview

Web security is about protecting web applications, users, and data from unauthorized access, misuse, and manipulation.  
This module explains how web apps work, where trust boundaries exist, how HTTP behaves, what common attacks look like, and how to defend against them.

> [!important]  
> The main idea of this module is simple: **the client can never be trusted**, and **security must be enforced on the server side**.

---

## Why Web Security Matters

|Reason|Explanation|
|---|---|
|Web apps are everywhere|Used in banking, e-commerce, healthcare, government, and more.|
|Sensitive data is exposed|Credentials, personal data, payment data, and private records can be targeted.|
|Attacks are frequent|Many attacks are automated and scan the internet continuously.|
|Small flaws can have big impact|A small mistake in input handling or access control can lead to major breaches.|
|Trust and reputation matter|Security failures can cause financial loss and damage user confidence.|

### Real-world consequences

- Data breaches
- Account takeover
- Financial fraud
- Unauthorized access to private information
- Damage to reputation and trust

---

## Evolution of Web Applications

Web applications have become more complex over time.

|Old Web Apps|Modern Web Apps|
|---|---|
|Mostly static pages|Single-page applications (SPAs)|
|Simple server-side logic|APIs and microservices|
|Less client-side logic|More frontend logic|
|Smaller attack surface|Larger attack surface|

### Why complexity matters

More components mean more entry points, more data flow, and more opportunities for attackers to exploit mistakes.

---

## Attacker Mindset

Attackers do not use applications the way normal users do.

|Attacker Behavior|Meaning|
|---|---|
|Intercept requests|They capture traffic before it reaches the server.|
|Modify data|They change parameters, headers, cookies, and body content.|
|Replay actions|They resend valid requests to see what happens.|
|Ignore the UI|They do not depend on buttons or page behavior.|

> [!note]  
> Anything that comes from the client can be changed by the attacker.

---

# 1. Web Architecture & Trust Boundaries

## Typical Web Application Architecture

A web application usually has:

- a browser or client,
- a web server,
- a database,
- and sometimes APIs or other services.

### Modern architecture

Modern apps often use:

- frontend frameworks,
- backend APIs,
- microservices,
- asynchronous communication.

This increases flexibility, but also increases complexity and attack surface.

---

## Data Flow in Web Applications

|Stage|What Happens|
|---|---|
|Input|User sends data through forms, URLs, headers, cookies, or APIs.|
|Processing|The application validates, transforms, and uses the data.|
|Storage|Data may be saved in databases, sessions, or logs.|
|Response|The server sends a result back to the browser.|

### Why this matters

Every transition point is a possible place where validation, filtering, or protection can fail.

---

## What is a Trust Boundary?

A trust boundary is the point where data moves from a less trusted area to a more trusted one.

### Example

- Browser input crosses into server logic
- External API data crosses into internal processing
- User-controlled data crosses into the database layer

> [!important]  
> When data crosses a trust boundary, it must be treated as untrusted until verified.

---

## Attack Surface

The attack surface includes every place an attacker can interact with the application.

|Entry Point|Risk|
|---|---|
|Forms|Input manipulation|
|URL parameters|Tampering with data|
|Headers|Hidden request manipulation|
|Cookies|Session abuse|
|File uploads|Malicious files or payloads|
|APIs|Direct request tampering|

---

## Client-Side vs Server-Side Responsibilities

|Client Side|Server Side|
|---|---|
|Presentation|Security enforcement|
|User interaction|Business rules|
|Usability checks|Validation|
|Visual feedback|Access control|

### Key rule

Client-side validation improves usability only. It does **not** provide security.

---

# 2. HTTP & Web Communication Fundamentals

## HTTP as a Communication Protocol

HTTP is the main protocol used for web communication.

|Feature|Description|
|---|---|
|Request-response model|Client sends request, server sends response|
|Stateless|Each request is independent|
|Widely used|Used for websites and APIs|
|Flexible|Supports more than just simple pages|

---

## Structure of an HTTP Request

|Part|Purpose|
|---|---|
|Request line|Contains method, path, and version|
|Headers|Carry metadata such as cookies or authorization|
|Body|Contains data sent to the server|
|Parameters|Can appear in the URL or request body|

### Security note

Attackers can modify all parts of a request.

---

## Structure of an HTTP Response

|Part|Purpose|
|---|---|
|Status line|Tells whether the request succeeded or failed|
|Headers|Provide metadata and browser instructions|
|Body|Contains the returned content|

Responses can reveal internal application behavior, so they must be designed carefully.

---

## HTTP Methods

|Method|Meaning|
|---|---|
|GET|Retrieve data|
|POST|Submit data and change state|
|PUT|Replace or update a resource|
|PATCH|Partially update a resource|
|DELETE|Remove a resource|

> [!note]  
> Misusing HTTP methods can create security problems, especially when sensitive actions are done through unsafe request types.

---

## HTTP Headers and Security

Headers often carry sensitive information.

|Header Use|Example|
|---|---|
|Authentication|Tokens or credentials|
|Session data|Cookies|
|Authorization|Access tokens|
|Custom metadata|Application-specific info|

### Why headers matter

If attackers modify headers, they may bypass weak controls or expose sensitive application behavior.

---

## Statelessness of HTTP

HTTP does not remember previous requests by itself.

|Property|Meaning|
|---|---|
|Stateless|Each request is processed independently|
|No built-in session memory|The server does not automatically track users|
|Scalable|Easier to distribute and scale|
|Security challenge|The app must manage state safely|

---

## Maintaining State in Web Applications

| State Mechanism      | Purpose                                  |
| -------------------- | ---------------------------------------- |
| Cookies              | Store session identifiers in the browser |
| Server-side sessions | Track authentication on the server       |
| Tokens               | Used in API authentication               |
| Local storage        | Sometimes used for client-side storage   |

> [!warning]  
> Poor state handling can lead to session hijacking, impersonation, and data exposure.

---

## Cookies and Security

Cookies are widely used to store session identifiers and related data.

|Attribute|Role|
|---|---|
|`Secure`|Sends cookie only over HTTPS|
|`HttpOnly`|Prevents JavaScript access|
|`Domain`|Defines where the cookie is valid|
|`Path`|Limits where the cookie is sent|

### Security concern

If cookies are poorly configured, attackers may steal or misuse sessions.

---

## HTTPS and Secure Communication

HTTPS uses TLS to encrypt data between client and server.

|Benefit|Explanation|
|---|---|
|Confidentiality|Prevents others from reading traffic|
|Integrity|Prevents tampering|
|Authentication|Helps verify the server|

> [!important]  
> HTTPS protects communication, but it does **not** fix broken application logic or weak security design.

---

## From HTTP to Attacks

Attackers often use interception tools to:

1. capture requests,
2. change values,
3. resend requests,
4. study server responses.

This process helps them discover weak validation, access control, or session handling.

---

# 3. Core Web Security Principles

## Why Security Principles Matter

Security problems usually happen when basic principles are ignored.

|Principle|Why It Matters|
|---|---|
|Never trust input|Prevents manipulation from the client|
|Validate and encode|Protects both backend and browser|
|Least privilege|Limits damage from compromise|
|Separation of responsibilities|Keeps client and server roles clear|
|Defense in depth|Prevents single-point failure|
|Secure defaults|Safer behavior by default|
|Zero trust|Trust nothing automatically|

---

## Never Trust User Input

All input from the client must be treated as untrusted.

### Examples of untrusted input

- form fields
- URL parameters
- cookies
- headers
- hidden fields

> [!note]  
> Hidden fields are not secure just because they are invisible in the UI.

---

## Input Validation and Output Encoding

|Technique|Purpose|Protects|
|---|---|---|
|Input validation|Checks if data is acceptable|Backend|
|Output encoding|Escapes data before display|Frontend/browser|

### Best practice

- Use strict allowlists
- Validate on the server
- Encode before rendering output

---

## Authentication vs Authorization

|Concept|Meaning|Example|
|---|---|---|
|Authentication|Confirms identity|Logging in with a password|
|Authorization|Confirms permissions|Accessing admin pages|

> [!important]  
> A user can be authenticated but still not authorized to access a resource.

---

## Principle of Least Privilege

Users, services, and components should only have the permissions they truly need.

### Benefits

- Reduces damage after compromise
- Limits misuse
- Shrinks attack surface

---

## Defense in Depth

Defense in depth means using multiple layers of protection.

|Layer|Example|
|---|---|
|Input validation|Reject malformed input|
|Authentication|Verify user identity|
|Authorization|Restrict access|
|Logging|Record suspicious activity|
|Monitoring|Detect attacks|
|Secure headers|Improve browser protection|

---

## Secure Session Management

A session should be:

- unpredictable,
- protected,
- time-limited,
- and invalidated correctly.

### Best practices

- Use strong random session IDs
- Expire sessions after inactivity
- Regenerate session IDs after login
- Protect sessions from client-side access

---

## Separation of Client and Server Responsibilities

|Client|Server|
|---|---|
|User interface|Security enforcement|
|Display logic|Validation and decision-making|
|Convenience checks|Business rule enforcement|

### Rule

Never put critical security decisions only in the frontend.

---

## Fail Securely

If something goes wrong, the system should fail safely.

|Secure Behavior|Meaning|
|---|---|
|Deny by default|Access is blocked unless allowed|
|Safe error handling|No sensitive details leaked|
|Secure defaults|Good security without extra setup|

---

## Zero Trust Mindset

Zero trust means no component is trusted automatically.

### Core idea

- Trust nothing by default
- Verify everything
- Recheck every request
- Do not rely on internal network location alone

---

# 4. Major Web Vulnerabilities

## Main Categories

|Category|Description|
|---|---|
|Injection attacks|Untrusted input is interpreted as code|
|XSS|Malicious script runs in the browser|
|Authentication attacks|Weak login or credential handling|
|Session attacks|Session theft or hijacking|
|Access control flaws|Unauthorized resource access|
|CSRF|Forged requests using a victim’s session|
|Client-side trust issues|Trusting browser-side logic too much|

---

## Injection Attacks

Injection happens when untrusted data is treated as executable code.

### Common targets

- databases
- operating systems
- interpreters
- templates
- APIs and JSON processing logic

### SQL injection idea

If user input is inserted directly into a query string, an attacker may change the meaning of the query.

> [!important]  
> The root problem is mixing **data** with **code**.

### Example

Instead of:

`SELECT * FROM users WHERE name = 'input';`

an unsafe design may allow input to alter the query structure.

---

## XSS (Cross-Site Scripting)

XSS occurs when malicious script is executed inside a user’s browser.

### How it happens

- application outputs untrusted input,
- browser interprets it as script,
- attacker code runs in the victim’s browser.

### Impact

- session theft
- credential theft
- page manipulation
- user impersonation

### Key cause

Poor output handling.

---

## Authentication Attacks

Weak authentication can allow attackers to:

- guess passwords,
- reuse credentials,
- exploit weak login systems,
- or bypass account protection.

### Impact

- account takeover
- identity theft
- unauthorized access

---

## Session Management Attacks

If sessions are weak, attackers may hijack them.

|Problem|Result|
|---|---|
|Predictable session IDs|Easier guessing|
|Exposed cookies|Session theft|
|Poor logout handling|Stolen sessions remain active|

---

## Access Control Vulnerabilities

Access control flaws happen when authorization checks are missing or incorrect.

### Example

A user changes an object ID in a request and accesses another user’s data.

This is often called **IDOR** (Insecure Direct Object Reference).

### Impact

- private data exposure
- unauthorized actions
- privilege abuse

---

## CSRF (Cross-Site Request Forgery)

CSRF tricks a logged-in user into sending an unwanted request.

### How it works

- the user is already authenticated,
- the browser automatically includes session credentials,
- the server processes the request as if it were legitimate.

### Impact

- changing account settings
- sending unauthorized actions
- financial or administrative misuse

---

## Client-Side Trust Vulnerabilities

These happen when the application trusts the browser too much.

### Common mistakes

- using frontend validation as security
- storing sensitive data in browser-accessible places
- relying on hidden fields
- implementing critical logic only in JavaScript

> [!warning]  
> Attackers can modify frontend code, requests, and browser storage.

---

# 5. Defensive Techniques & Best Practices

## General Defense Strategy

Security must be layered.

|Goal|Meaning|
|---|---|
|Enforce correct behavior|Do not rely on user honesty|
|Protect every layer|Frontend, backend, database, and transport|
|Reduce risk|Do not depend on one control only|

---

## Injection Defenses

|Defense|Why It Helps|
|---|---|
|Parameterized queries|Prevents input from changing SQL structure|
|Avoid string concatenation|Stops query manipulation|
|Validate input|Reject unexpected data|
|Use ORM safely|Reduces manual query building|
|Limit DB privileges|Reduces impact if something goes wrong|

---

## XSS Defenses

|Defense|Purpose|
|---|---|
|Output encoding|Prevents script execution|
|Context-aware encoding|Matches the output location|
|Avoid raw insertion|Do not place user input directly into HTML or script|
|Content Security Policy (CSP)|Limits what browser can load or run|
|Sanitization|Removes unsafe content where needed|

---

## Authentication and Session Defenses

|Defense|Purpose|
|---|---|
|Strong passwords|Harder to guess|
|Multi-factor authentication|Extra login protection|
|High-entropy session IDs|Harder to predict|
|Session regeneration|Reduces session fixation risk|
|Proper logout and timeout|Prevents old sessions from remaining active|

---

## Session Protection Best Practices

|Cookie/Session Practice|Benefit|
|---|---|
|`HttpOnly`|Protects cookies from JavaScript|
|`Secure`|Sends only over HTTPS|
|`SameSite`|Helps reduce CSRF|
|Avoid localStorage for sensitive tokens|Reduces exposure to script access|
|Monitor session activity|Detects suspicious behavior|

---

## Access Control Defenses

|Defense|Purpose|
|---|---|
|Check authorization on every request|Prevents unauthorized access|
|Never trust client IDs|Stops IDOR-style attacks|
|Verify ownership|Ensures the user owns the resource|
|Use role-based / attribute-based access|Organizes permissions clearly|
|Deny by default|Safer security baseline|

---

## CSRF Defenses

|Defense|Purpose|
|---|---|
|Anti-CSRF tokens|Verify request legitimacy|
|Check Origin / Referer|Helps detect cross-site requests|
|SameSite cookies|Limits automatic cross-site sending|
|Re-authenticate sensitive actions|Adds protection for critical operations|
|Avoid GET for state changes|Prevents unintended action through links|

---

## Client-Side Trust Defenses

|Defense|Purpose|
|---|---|
|Never trust client requests|Main security rule|
|Validate all server-side input|Enforces real security|
|Keep sensitive data off the client|Reduces exposure|
|Do not put business logic only in frontend|Prevents bypass|
|Enforce critical decisions on server|Ensures control|

---

## Security Headers and Browser Protections

|Header|Purpose|
|---|---|
|CSP|Controls what resources can load or execute|
|HSTS|Forces HTTPS connections|
|X-Frame-Options|Prevents embedding in frames to reduce clickjacking|

> [!note]  
> Security headers strengthen browser-side protection, but they do not replace secure coding.

---

## Secure Development and Testing Mindset

Security should be part of the development lifecycle.

### Good habits

- think like an attacker,
- test requests,
- modify and replay inputs,
- use tools such as Burp Suite or ZAP,
- test continuously.

---

# Quick Revision Table

|Topic|Core Idea|
|---|---|
|Web security|Protect apps, data, and users|
|Trust boundary|Where trust changes|
|HTTP|Request-response, stateless protocol|
|State management|Cookies, sessions, tokens|
|Principle of least privilege|Give minimum access|
|Defense in depth|Use layered protection|
|Injection|Data becomes code|
|XSS|Malicious script runs in browser|
|CSRF|User is tricked into unwanted action|
|Access control|Only allowed users get access|
|Client-side trust|Never rely on browser-side security|

---

# Final Key Takeaways

- Web security is about protecting trust.
- Most attacks exploit simple design or logic flaws.
- The client environment is fully controlled by the attacker.
- The server must validate, authorize, and enforce security rules.
- Security must be built into the design, not added later.

> [!summary]  
> The strongest web security mindset is: **assume nothing is trustworthy until the server verifies it**.