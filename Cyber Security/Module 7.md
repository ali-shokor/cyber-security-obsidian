# Module 7 — Secure Software Development Life Cycle (SSDLC)


> [!summary] Module Focus  
>  Security must be built into software from the start, not added at the end. This module explains how Secure by Design, Shift-Left Security, threat modeling, secure coding, testing, deployment hardening, monitoring, and patch management work together to reduce risk across the whole software lifecycle.


---

## 1. Big Idea

Security is not a separate final step.

It is a continuous process that starts in:
- requirements
- architecture
- design
- coding
- testing
- deployment
- monitoring
- incident response

The SSDLC gives a structured way to include security in every phase.

---

## 2. Why Security as an Afterthought Fails

> [!warning] Main Problem
> If security is added only after development, the team usually fixes symptoms instead of the real cause.

### Why this fails
- vulnerabilities are often created during requirements or design
- late fixes cost more
- emergency patches create more mistakes
- reactive security slows delivery
- business damage becomes larger after release

### Simple example
A login system may work normally, but if authorization checks are weak, a user may access data they should not see.

### Main lesson
Security cannot be patched in at the end. It must be designed in from the beginning.

---

## 3. Where Vulnerabilities Actually Begin

| Stage | Common Weakness | Result |
|---|---|---|
| Requirements | Missing security requirements | Security is never implemented |
| Design | Weak trust assumptions | Unsafe flow of data |
| Coding | Unsafe implementation | Injection, access control issues, data exposure |
| Testing / Production | Late discovery | Higher cost and higher risk |

### Important idea
Many vulnerabilities are not only coding bugs.  
They often begin with:
- bad assumptions
- weak design
- missing security requirements

---

## 4. Attackers Exploit Trust Assumptions

Attackers often abuse what the system incorrectly trusts.

### Common trust mistakes
- trusting client-side data
- trusting hidden form fields
- trusting user input
- trusting internal services too much
- trusting default settings
- trusting that workflows cannot be skipped

### Example
If a server trusts the price sent by the browser, an attacker can modify that price before sending the request.

---

## 5. The Cost of Late Vulnerability Remediation

| When the problem is found | Cost | Risk |
|---|---|---|
| Requirements / Design | Low | Low |
| Implementation | Medium | Medium |
| Testing | High | High |
| Production | Very high | Very high |

### Why this matters
Late fixes may require:
- redesign
- rework
- emergency patching
- downtime
- incident response
- reputation recovery

---

## 6. Business Impact of Reactive Security

Reactive security affects the whole organization, not just developers.

### Business consequences
- financial loss
- operational disruption
- legal/compliance issues
- customer trust loss
- reputation damage
- delayed delivery

### Example
A weakness in a payment system can lead to fraud, incident response costs, and loss of trust.

---

## 7. Secure by Design and Shift-Left Security

> [!tip] Core Idea
> Secure by Design means security is part of the system from the beginning.  
> Shift-Left means security work happens earlier in the lifecycle.

### Secure by Design
Security is built into:
- architecture
- interfaces
- workflows
- access control
- data handling

### Shift-Left
Security is moved earlier into:
- planning
- design
- development
- build pipelines

### Example
Using parameterized queries from the start helps prevent SQL injection by design.

---

## 8. SSDLC as Continuous Security Engineering

SSDLC is the execution framework that makes security practical.

### What SSDLC provides
- structure
- repeatability
- consistency
- measurable security practices
- continuous improvement

### SSDLC flow
1. define security requirements
2. model threats
3. implement securely
4. test for abuse
5. deploy securely
6. monitor continuously
7. patch and improve

---

## 9. Security Is Not a Separate Development Phase

Security should not be isolated into one final step.

### Better approach
Security must be present in:
- planning
- design reviews
- coding standards
- CI/CD checks
- testing
- release controls
- operations

### Why
Modern development is fast and iterative.  
Security must move with delivery.

---

## 10. Agile, DevSecOps, and Modern Secure Delivery

### Why classical SSDLC alone is not enough
Modern teams release software quickly and frequently.  
Security must adapt to this pace.

### DevSecOps
Security is integrated into the delivery pipeline rather than handled separately.

### Shared responsibility problem
Security fails when everyone assumes someone else is responsible.

### Better model
- developers build securely
- operations deploy securely
- security teams guide, review, and validate
- automation supports the process

---

## 11. Secure Planning and Requirements Engineering

Security should be included in requirements.

### What should be defined
- security requirements
- abuse cases
- misuse cases
- security acceptance criteria

### Abuse case
A harmful way an attacker may use the system.

### Misuse case
A scenario showing how a feature may be used in a harmful or unintended way.

### Example
For file upload:
- file type restrictions
- file size limits
- virus scanning
- access control
- storage safety

---

## 12. Secure Architecture and Threat Modeling

> [!important] Threat Modeling
> Threat modeling is the process of thinking like an attacker to find risks before they become real attacks.

### Main questions
| Question                         | Purpose                          |
| -------------------------------- | -------------------------------- |
| What are we protecting?          | Identify the assets              |
| Who are the attackers?           | Understand attacker capabilities |
| Where can they enter?            | Identify entry points            |
| What can go wrong?               | Find possible threats            |
| Where do trust boundaries exist? | Find risky transitions           |

### Attack surface
All the ways an attacker can interact with the system.

### Trust boundary
A point where data or control moves from one level of trust to another.

### STRIDE
A threat model with six threat categories:
- Spoofing
- Tampering
- Repudiation
- Information disclosure
- Denial of service
- Elevation of privilege

### Example
If a user can change a URL parameter and gain admin access, that is a serious authorization problem.

---

## 13. Secure Implementation and Developer Security Practices

### Secure coding is more than bug-free code
A program can work correctly and still be insecure.

### Important practices
| Practice | Why it matters | Example |
|---|---|---|
| Input validation | Rejects unsafe input | Check length, type, format |
| Data handling | Prevents misuse of sensitive data | Encode, sanitize, protect output |
| Authentication | Confirms identity | Login system |
| Authorization | Confirms permissions | Only admins can delete users |
| Secrets handling | Protects passwords and keys | Use a secrets manager |
| Dependency security | Reduces supply chain risk | Scan third-party libraries |
| Code review | Finds logic mistakes | Review security-sensitive code |
| Automated checks | Catches issues early | SAST, policy checks, linting |

### Simple examples
- trusting user input directly can lead to injection
- storing API keys in source code can expose secrets
- missing permission checks can expose another user’s data

---

## 14. Input Validation and Data Handling

Input validation checks that input is expected and safe.

### Typical validation checks
- type
- length
- format
- range
- allowed values

### Why it matters
It reduces:
- injection risk
- malformed data
- unexpected behavior
- application crashes

### Example
A field expecting a number should not accept letters or script content.

---

## 15. Authentication and Authorization Enforcement

### Authentication
Verifies who the user is.

### Authorization
Verifies what the user is allowed to do.

### Why both matter
A system may correctly log in a user, but still fail if it does not check their permissions.

### Example
A normal user should not be able to access admin functions just by changing a page URL.

---

## 16. Secrets and Sensitive Data Handling

### Secrets
Sensitive values such as:
- passwords
- API keys
- tokens
- certificates
- private credentials

### Good practice
- do not hardcode secrets in source code
- use secure storage
- restrict access
- rotate secrets when needed
- avoid exposing secrets in logs

### Example
If an API key is pushed to a public repository, attackers may use it immediately.

---

## 17. Dependency Security and Supply Chain Risk

### Dependency
A third-party library or package used by the software.

### Supply chain risk
Risk introduced by external libraries, packages, or tools.

### Why it matters
A vulnerable dependency can make the whole system vulnerable.

### Good practice
- scan dependencies
- update packages
- remove unused libraries
- verify trusted sources
- monitor known vulnerabilities

---

## 18. Security Verification and Testing

### Security testing is not functional testing
| Functional Testing | Security Testing |
|---|---|
| Does it work? | Can it be abused? |
| Checks normal behavior | Checks hostile behavior |
| Verifies features | Verifies resistance to attack |

### Security testing techniques
| Technique | Purpose |
|---|---|
| SAST | Analyze source code without running it |
| DAST | Test the running application from outside |
| IAST | Combine runtime monitoring with testing |
| Dependency scanning | Detect vulnerable libraries |
| Secrets scanning | Detect exposed credentials |

### Manual testing still matters
Humans are better at finding:
- business logic abuse
- authorization flaws
- workflow bypasses
- edge cases
- design weaknesses

### Penetration testing
Simulates attacker behavior to find real-world weaknesses.

---

## 19. Security Testing in CI/CD

Security checks should be part of the pipeline.

### Why
This helps catch problems:
- early
- consistently
- automatically
- before release

### Good pipeline checks
- code scanning
- dependency scanning
- secrets scanning
- policy checks
- test automation
- build validation

---

## 20. Secure Release and Operations

Security does not end at release.

### After release
Software must still be:
- monitored
- patched
- hardened
- audited
- defended

### Secure deployment and hardening
| Area | Goal |
|---|---|
| Hardening | Remove unnecessary risk |
| Secure defaults | Start from safe settings |
| Least privilege | Give only the access needed |
| Defense in depth | Use multiple protection layers |

### Monitoring, logging, and detection
These help identify:
- suspicious activity
- exploitation attempts
- abnormal patterns
- policy violations

### Patch management
A continuous cycle of:
- discovering vulnerabilities
- prioritizing them
- fixing them
- verifying the fix

### Incident response
When something goes wrong:
- detect
- contain
- investigate
- recover
- learn

---

## 21. SSDLC as a Continuous Security Loop

> [!summary] Final Idea
> SSDLC is not a one-time task. It is a continuous loop of prevention, verification, release, monitoring, patching, and improvement.

### The loop
- observe
- detect
- improve
- secure
- verify
- repeat

### Result
Software becomes:
- more secure
- more resilient
- easier to maintain
- better aligned with real business needs

---

## 22. Exam-Friendly Short Summary

- Security must start early.
- Design matters as much as code.
- Threat modeling helps find risk before attackers do.
- Secure coding requires validation, authentication, authorization, secret protection, and dependency control.
- Security testing is different from functional testing.
- Release is not the end; monitoring and patching continue.

---

## 23. Glossary

| Term | Meaning |
|---|---|
| SSDLC | Secure Software Development Life Cycle |
| Secure by Design | Building security into the system from the start |
| Shift-Left | Moving security earlier in the lifecycle |
| Reactive security | Fixing security after problems appear |
| Proactive security | Preventing security problems before they happen |
| Threat modeling | Thinking like an attacker to identify threats |
| Attack surface | All possible entry points an attacker can use |
| Trust boundary | A point where trust level changes |
| STRIDE | A threat model with six categories |
| Spoofing | Pretending to be someone or something else |
| Tampering | Modifying data or behavior without permission |
| Repudiation | Denying an action happened |
| Information disclosure | Exposing data to unauthorized people |
| Denial of service | Making a service unavailable |
| Elevation of privilege | Gaining higher access than allowed |
| Abuse case | A harmful use of a system feature |
| Misuse case | A scenario describing harmful or unintended use |
| Security requirements | Requirements that define security needs |
| Acceptance criteria | Conditions that must be met to accept the work |
| Secure coding | Writing code with security in mind |
| Input validation | Checking that input is safe and expected |
| Sanitization | Cleaning input or output to reduce risk |
| Authentication | Verifying who a user is |
| Authorization | Verifying what a user can do |
| Secrets | Sensitive values like passwords, API keys, and tokens |
| Secrets manager | A tool for storing secrets securely |
| Dependency | A third-party library or package |
| Supply chain risk | Risk coming from third-party code or tools |
| Code review | Human inspection of code |
| Automated checks | Tool-based security checks |
| SAST | Static Application Security Testing |
| DAST | Dynamic Application Security Testing |
| IAST | Interactive Application Security Testing |
| Dependency scanning | Checking libraries for known vulnerabilities |
| Secrets scanning | Detecting exposed credentials |
| Penetration testing | Simulated attack testing |
| CI/CD | Continuous Integration / Continuous Delivery |
| Hardening | Reducing attack surface through secure configuration |
| Least privilege | Giving only the minimum permissions needed |
| Defense in depth | Using multiple layers of security |
| Monitoring | Watching systems for suspicious activity |
| Logging | Recording events for later review |
| Detection | Identifying suspicious or malicious activity |
| Patch management | Updating software to fix vulnerabilities |
| Incident response | The process of handling a security incident |
| Continuous security loop | Ongoing cycle of building, testing, deploying, and improving security |

---

## 24. Final Takeaway

Security is not a phase that comes after development.  
It is a continuous engineering practice that begins with requirements and continues through design, implementation, testing, release, monitoring, and response.