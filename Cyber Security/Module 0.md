# I3336 — Introduction to Cybersecurity

> [!summary] Final Idea
> This course is about **thinking like a security analyst**, not just using tools. It explains how systems fail under intentional attack, how to reason about risk and trust, and how to design systems that stay secure over time.

---

## 1. Course Overview

This is an **elective course** in cybersecurity.

### Basic details
| Item | Details |
|---|---|
| Course | I3336 — Introduction to Cybersecurity |
| Instructor | Ahmad Fadlallah |
| Duration | 36 hours |
| Schedule | One weekly lecture on Thursday at 4:00 PM |
|  | One biweekly lecture on Wednesday at 8:00 AM |
| Activities | Case studies / labs |

---

## 2. Why This Course Exists

> [!important] Why the course matters
> Cyber incidents affect all modern systems, attackers exploit design assumptions, and security failures are system failures.

### Main reasons
- Cyber incidents affect all modern systems.
- Attackers exploit design assumptions.
- Security failures are system failures.
- Security is now a computer science responsibility.
- Connectivity increases exposure.
- Foundational knowledge is required.

### Simple meaning
Security is not just a separate “cyber” topic. It is part of how computer systems are designed, built, and used.

---

## 3. Why Cybersecurity Matters to CS Students

Computer scientists design systems that other people will attack.

That means:
- design decisions affect trust,
- coding decisions affect exposure,
- architecture affects risk,
- security issues may appear long after deployment,
- secure thinking helps build robust and resilient systems.

### Example
A small design mistake in an authentication flow can later become a major data breach.

---

## 4. What This Course Is

This course is:
- concept-driven, not tool-driven
- focused on reasoning and understanding
- useful for all computer science careers
- built to develop long-term security intuition

### In one line
It teaches **how to think about security**, not just which commands to run.

---

## 5. What This Course Is Not

This course is **not**:
- a hacking course
- a penetration testing course
- a certification training course
- focused on tools, commands, or recipes
- about shortcuts or “security tricks”

### Simple meaning
The goal is understanding, not offensive practice or tool memorization.

---

## 6. What You Will Gain

By the end of the course, you should gain:
- a structured way to think about cybersecurity problems
- the ability to analyze real-world security incidents
- awareness of common design pitfalls
- preparation for advanced cybersecurity courses

---

## 7. Learning Outcomes

By the end of the course, you will be able to:

1. Explain core cybersecurity concepts and terminology.
2. Identify assets, adversaries, trust assumptions, and attack surfaces.
3. Describe attack techniques and malware behaviors.
4. Analyze security mechanisms in networks, operating systems, and applications.
5. Distinguish authentication, authorization, and access control.
6. Explain cryptographic mechanisms and their limits.
7. Analyze incidents using structured reasoning.
8. Recognize the role of human behavior, insider threats, ethics, and legal constraints.

---

## 8. Simplified Learning Outcomes

A shorter version of the same goals:
- explain key cybersecurity concepts
- identify assets, threats, vulnerabilities, and risks
- reason about strengths and limits of security mechanisms
- analyze incidents using structured thinking
- communicate security concerns clearly

---

## 9. Course Topics Overview

This course is organized around the following modules:

| Topic | Focus |
|---|---|
| Foundations of cybersecurity | Core principles and security thinking |
| Threat modeling and cyber threat landscape | Assets, adversaries, threats, vulnerabilities, risk |
| Malware and attack techniques | Viruses, worms, Trojans, ransomware, exploitation |
| Network and communication security | Firewalls, IDS/IPS, SIEM, secure communication |
| Identity, authentication, and access control | Passwords, MFA, permissions, identity as perimeter |
| Operating system and system security | Trust models, least privilege, patching, misconfiguration |
| Application and web security principles | Input validation, OWASP ideas, secure design |
| Secure Software Development Lifecycle (SSDLC) | Security by design, secure coding, early threat handling |
| Cryptography foundations | Encryption, hashing, signatures, PKI, TLS |
| Human factors and insider threats | Social engineering, phishing, human behavior |
| Risk management, governance, ethics | Policies, priorities, legal and ethical responsibilities |
| Emerging topics in cybersecurity | AI, automation, and future trends |

---

## 10. Module Meaning in Simple Terms

### Foundations of Cybersecurity
What security means in computing systems:
- security as a system property
- confidentiality, integrity, availability
- trade-offs and limitations
- security is never absolute

### Threat Modeling & Cyber Threat Landscape
Who attacks systems and why:
- assets and adversaries
- threats, vulnerabilities, risk
- attack surfaces and assumptions
- threat modeling

### Malware & Attack Techniques
Understanding malware by behavior:
- viruses, worms, Trojans, ransomware
- payloads vs delivery mechanisms
- attacker logic and chaining
- conceptual exploitation

### Network & Communication Security
Why connectivity increases risk:
- trust boundaries
- secure vs insecure communication
- firewalls
- IDS/IPS
- SIEM
- limits of network defenses

### Identity, Authentication & Access Control
How systems verify and limit access:
- authentication vs authorization
- password weaknesses
- MFA
- access control models
- identity compromise impact

### Operating System & System Security
How systems protect themselves:
- trust models
- least privilege
- hardening and configuration
- patching and updates
- misconfiguration risks

### Application & Web Security
Why apps are frequent targets:
- input validation
- trust boundaries
- OWASP Top 10 ideas
- secure design
- common app failures

### SSDLC
How to build security into development:
- security by design
- security by patching
- early threat identification
- secure coding
- preventing vulnerabilities before release

### Cryptography Foundations
What cryptography protects:
- encryption
- hashing
- digital signatures
- PKI
- TLS
- common misuse

### Human Factors & Insider Threats
Why people matter in security:
- social engineering
- phishing
- insider threats
- human assumptions as attack surfaces

### Risk Management, Governance & Ethics
Security as a decision-making process:
- prioritizing effort
- policies and governance
- legal and ethical responsibility
- societal impact

### Emerging Topics
Future-facing security issues:
- AI and machine learning for defense
- AI-assisted attacks and automation
- new challenges from intelligent systems

---

## 11. How the Course Is Taught

The course uses:
- conceptual lectures
- case studies
- guided discussions
- light practical and observational activities

### What this means
It emphasizes understanding over tools, and reasoning over shortcuts.

---

## 12. Should You Take This Course?

### This course is suitable if you want to:
- understand how systems fail under attack
- learn secure system and software design thinking
- develop analytical cybersecurity skills
- prepare for advanced cybersecurity courses

### This course may not be suitable if you only want:
- penetration testing skills
- tool-based training
- certification-oriented shortcuts

---

## 13. Security Thinking This Course Tries to Build

The course teaches you to ask:
- What are we protecting?
- Who might attack?
- What assumptions does the system make?
- Where can the attacker reach?
- What can fail?
- What is the best way to reduce risk?

### Example
Instead of asking only “Is this system encrypted?”, ask:
- Who can access it?
- What happens if credentials are stolen?
- What happens if the server is misconfigured?
- What if the user makes a mistake?

---

## 14. Final Message

> [!summary] Final Message
> Cybersecurity is about thinking and design, not only tools. This course builds foundations that remain useful over time and gives you long-term value as a computer scientist.

---

## 15. Important Words Only

| Word | Specific meaning | Example |
|---|---|---|
| Cybersecurity | Protecting systems from intentional attack | Defending a web app |
| Security as a system property | Security comes from the whole system, not one feature | A secure app can still fail if the OS is weak |
| Threat | Something that can cause harm | Phishing |
| Vulnerability | A weakness that can be exploited | Broken access control |
| Risk | Likelihood and impact of harm | Exposed student records |
| Asset | Something valuable that must be protected | Grades, passwords, data |
| Trust assumption | Something the system believes without enough proof | “Internal users are safe” |
| Attack surface | Where an attacker can interact with a system | API, login page |
| Authentication | Proving identity | Password, MFA |
| Authorization | Deciding what a user may do | Student cannot edit grades |
| Access control | Rules that limit access | Role-based permissions |
| Malware | Malicious software | Ransomware |
| Encryption | Protecting data by making it unreadable to others | TLS |
| Hashing | One-way transformation of data | Password storage |
| Signature | Proof that data came from a trusted source | Signed software update |
| PKI | System for managing public keys and trust | Certificates |
| TLS | Secure communication protocol | HTTPS |
| SSDLC | Secure Software Development Life Cycle | Security built into development |
| Social engineering | Manipulating humans to get access | Fake login email |
| Insider threat | Threat from someone inside the organization | Employee abuse |
| Governance | Rules and oversight for security | Security policy |
| Ethics | Responsible and fair security behavior | Avoid misuse of data |
| AI security | Security issues related to AI use | AI-assisted attacks |

---

## 16. One-Sentence Course Summary

This course teaches how to reason about cybersecurity from first principles so you can design, analyze, and defend systems in a world where attacks are normal and assumptions are constantly tested.