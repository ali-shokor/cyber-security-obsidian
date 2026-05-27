# Foundations of Cybersecurity

> [!summary] Final Idea
> Cybersecurity studies how digital systems fail under intentional attack, not just accidental errors. This module builds the core thinking behind the whole course: understand systems, assumptions, assets, threats, vulnerabilities, exposure, risk, and security objectives before choosing tools or defenses.

---

## 1. Introduction

Cybersecurity is a **design and analysis problem**, not a checklist.

It asks:
- what can go wrong,
- what assumptions the system makes,
- how attackers violate those assumptions,
- and what must be protected.  

The goal is to build security intuition that stays useful even when tools and technologies change.

---

## 2. Why Start with Foundations?

> [!important] Why foundations matter
> Most security failures begin with early design decisions. If you understand why systems fail, you can reason about security much better than if you only memorize attacks.

### Main reasons
| Reason | Meaning |
|---|---|
| Early design matters | Many failures are built in before coding starts |
| Principles last longer than tools | Tools change fast, but core ideas stay stable |
| Avoid false confidence | A system can look secure while still being weak |
| Build intuition | Good security thinking transfers to new systems |

### Simple example
If a system assumes users are trusted because it was built for a small internal group, that assumption may break later when the system becomes public.

---

## 3. Computing Systems: Then vs Now

### Old systems
- isolated
- physically controlled
- trusted users
- limited exposure

Example: a university mainframe accessed only from terminals inside a building.

### Modern systems
- internet-connected
- globally exposed
- always reachable
- dependent on cloud, mobile, and external services

Example: a university LMS available 24/7 to users worldwide.

### Key difference
Modern systems are attacked continuously, even when no attacker is specifically targeting them.

---

## 4. Why Cybersecurity Became Necessary

| Change | Security impact |
|---|---|
| Integration | Systems became interdependent |
| Automation | Attacks can scale massively |
| Lower attack cost | More attackers can participate |
| Cloud and mobile | More entry points and trust problems |
| External services | Security now depends on code you do not control |

### Simple example
A web app may be secure in its own code, but a vulnerable third-party library can still compromise the whole system.

---

## 5. Accidents vs Attacks

> [!important] Distinction
> Bugs are unintentional. Attacks are intentional.

| Concept | Meaning | Example |
|---|---|---|
| Bug | An accidental defect | A coding mistake |
| Attack | Deliberate action by an adversary | Exploiting a weakness |
| Security issue | A weakness that can be abused | Broken access control |

### Why this matters
Fixing bugs alone is not enough, because attackers adapt and actively search for weaknesses.

---

## 6. Real-Life Motivation

Security failures have real-world consequences:
- ransomware can block registration systems
- email accounts can be hijacked for phishing
- exam questions can leak before finals
- grades can be altered after submission
- trust and reputation can be damaged

### Simple example
If a grading system is compromised, the damage is not only technical; it affects fairness, trust, and institutional credibility.

---

## 7. Case Study: A System That Evolved Over Time

A Student Information System may begin as an internal tool for staff only.

Later it may be:
- connected to the LMS,
- enabled for remote access,
- expanded with automation,
- exposed to more users and more interfaces.

### Problem
A vulnerability in the LMS can then lead to unauthorized access to SIS records and grade modification.

### Why it is hard to detect
The activity may appear legitimate, so the system does not crash and logs may look normal.

---

## 8. Reflection on Early Design

Early designers often assumed:
- trusted users,
- cooperative behavior,
- physical isolation,
- limited access.

Those assumptions may have made sense originally, but they can become dangerous when the system evolves.

### Core lesson
Attackers exploit outdated assumptions.

---

## 9. Why “We’ll Secure It Later” Fails

> [!warning] Main risk
> Some security decisions are hard or impossible to fix after architecture is already set.

### Difficult to change later
| Design choice | Why it matters |
|---|---|
| Trust boundaries | Defines who trusts whom |
| Identity model | Defines how users are recognized |
| Data flows | Defines where sensitive data moves |
| System structure | Monolith vs separated components |

### Security controls that depend on early design
- access control
- isolation and containment
- auditing and accountability
- defense in depth

### Key idea
Patches and monitoring can reduce risk, but they rarely fix a weak architecture completely.

---

## 10. What Security Is Not

Security is not:
- a feature,
- a single tool,
- encryption alone,
- compliance,
- optional.

### Why
Security emerges from how the whole system works together:
- software
- hardware
- data
- network
- users

A secure component in an insecure system can still be insecure.

---

## 11. Security as a System Property

Security depends on:
- architecture,
- configuration,
- usage,
- assumptions.

### Example
A very secure database is not enough if the application around it has broken access control.

---

## 12. Security and Other System Properties

Security often conflicts with:
- performance
- availability
- usability

### Key point
Design is about trade-offs, not perfect optimization.

### Example
More authentication steps may improve security, but may also slow down users in emergencies.

---

## 13. Security Across the Lifecycle

Design decisions create assumptions.  
Code embeds those assumptions.  
Attackers exploit them.  
Then vulnerabilities appear.

### Main lesson
Vulnerabilities are often introduced before coding even starts.

---

## 14. Weakest-Link Principle

> [!important] Weakest-link principle
> System security is determined by its weakest dependency, not by its strongest component.

### Why it matters
- strong encryption does not help if authorization is broken
- secure servers do not help if backups are exposed
- good tools fail when combined badly

### Simple example
A system may use HTTPS, but if access control is broken, data can still be exposed.

---

## 15. System Failure Examples

Examples of poor integration:
- HTTPS with broken authorization
- encrypted database with open access
- secure server with exposed backup
- security tools configured inconsistently

### Key idea
Individual parts may be secure on their own, but the way they are combined creates gaps.

---

## 16. Complexity

The more tools, rules, and components a system has, the more likely:
- misconfiguration,
- rule conflict,
- unpatched components,
- and hidden weaknesses become.

### Example
A system with firewalls, IDS/IPS, WAFs, SIEM, endpoint agents, DLP, and zero-trust gateways may still fail if the configuration is inconsistent.

---

## 17. What Do We Protect?

Security starts by asking: **what are the assets?**

---

## 18. Assets

> [!important] Asset
> An asset is anything valuable whose loss or compromise causes harm.

### Important idea
Asset value depends on:
- purpose
- environment
- stakeholders
- time

### Example
Exam questions are extremely sensitive before the exam, but much less critical after it ends.

### Asset ranking example
Most critical to least critical in a university:
1. Exam questions
2. Student email accounts
3. Course schedules
4. Archived lecture slides
5. Public website content

---

## 19. Threats

> [!important] Threat
> A threat is a potential cause of harm to an asset.

Threats:
- exist even when no attack is happening,
- depend on context,
- cannot be fully eliminated,
- must be managed or reduced.

### Example
Phishing is a threat to university email accounts because it can steal credentials.

---

## 20. Murphy’s Law in Cybersecurity

Murphy’s law says: anything that can go wrong, will go wrong.

### Why it matters here
Cybersecurity assumes:
- failures happen,
- misuse happens,
- rare events still matter,
- the worst-case failure often happens at the worst time.

### Correct interpretation
Do not become paranoid.  
Design systems to fail gracefully and limit damage.

---

## 21. Vulnerabilities

> [!important] Vulnerability
> A vulnerability is an exploitable weakness that makes harm possible when a threat exists.

Vulnerabilities can come from:
- design
- implementation
- configuration

### Important point
A vulnerability may exist for years before anyone notices it.

### Example
Missing authentication or default permissions can create major security problems.

---

## 22. Exposure

> [!important] Exposure
> Exposure is whether a vulnerability is reachable by an attacker.

A vulnerability only matters if the attacker can actually reach it.

### Example
A flaw hidden behind internal-only access is less dangerous than the same flaw exposed on the public internet.

### Why exposure matters
Exposure can increase when:
- deployment changes,
- interfaces become public,
- trust boundaries shift.

---

## 23. Risk

> [!important] Risk
> Risk is the potential for harm when a threat exploits a vulnerability in an exposed asset.

### Key idea
A threat alone is not risk.  
A vulnerability alone is not risk.  
Exposure alone is not risk.  
Risk appears when all three come together.

### Why this matters
Security resources are limited, so risk helps decide what to fix first.

---

## 24. Attacks

> [!important] Attack
> An attack is an intentional attempt to cause harm to valuable assets.

Attacks are not accidents.  
They are deliberate and adversarial.

### Example
A student changing request parameters to alter another student’s grades is an attack, not a bug.

---

## 25. Bugs vs Vulnerabilities

| Term | Meaning |
|---|---|
| Bug | A defect in software, configuration, or design |
| Vulnerability | A bug that can be exploited to cause security harm |

### Important distinction
Many bugs are only reliability problems.  
A bug becomes a security issue when attackers can abuse it.

---

## 26. Case Study: University Grade System

A student logs in with a valid account, changes request parameters, accesses another student’s record, and modifies grades.

### What happened
- The system checked login status.
- It did not verify ownership of the record.
- The action looked normal in logs.
- No errors were generated.

### Analysis
| Item | Meaning |
|---|---|
| Asset | Grades, student records, trust, academic integrity |
| Flaw | Authentication checked, ownership not checked |
| Weakness | Users can access other students’ data |
| Exposure | Web interface is reachable normally |
| Attack | Deliberate parameter manipulation |
| Why hidden | Activity looked legitimate |

### Core lesson
Security failures can be silent.

---

## 27. Security Objectives

> [!important] Security objectives
> Security objectives define what a system must preserve under misuse or attack.

Security is not absolute.  
It is about preserving the most important properties.

### Main objectives
- confidentiality
- integrity
- availability
- authentication
- authenticity
- accountability

---

## 28. Cybersecurity Definition

Cybersecurity is about preventing, protecting, and restoring systems so they preserve:
- availability
- integrity
- confidentiality
- authentication
- non-repudiation

---

## 29. Confidentiality

> [!important] Confidentiality
> Confidentiality means information is not disclosed to unauthorized entities.

### Example
- exam questions seen before the exam
- student grades visible to other students
- internal emails exposed through bad access control

### Key point
Confidentiality can be lost without any system crash or data modification.

---

## 30. Data Confidentiality vs Privacy

| Term | Meaning |
|---|---|
| Data confidentiality | Technical protection against unauthorized access |
| Privacy | Protection of personal rights and appropriate use of personal data |

### Important difference
A system can preserve confidentiality and still violate privacy.

### Example
A hospital may technically restrict access to records, but a staff member can still violate privacy by looking up a celebrity patient out of curiosity.

---

## 31. Integrity

> [!important] Integrity
> Integrity means data and system state are not altered improperly.

### Integrity applies to
- stored data
- transmitted data
- system behavior

### Examples
- grades changed without authorization
- configuration files altered
- logs modified to hide actions
- software updates replaced with altered versions

### Key point
Integrity violations can be silent.

---

## 32. Data Integrity vs System Integrity

| Type | Meaning | Example |
|---|---|---|
| Data integrity | Data is not modified without authorization | Grades remain correct |
| System integrity | The system behaves as intended | Rules are enforced properly |

A system may keep data unchanged but still behave incorrectly.

---

## 33. Availability

> [!important] Availability
> Availability means legitimate users can access systems and services when needed.

### Examples
- registration system down during enrollment
- LMS unavailable during exams
- email outage
- cloud services unavailable due to overload

### Key point
Availability loss can happen even when no data is destroyed.

---

## 34. Authentication and Authenticity

| Term | Meaning |
|---|---|
| Authentication | Verifying identity |
| User authenticity | User is who they claim to be |
| Data authenticity | Data comes from a legitimate source |

### Example
A system may verify that an instructor is logged in, and also verify that submitted grades really came from that instructor.

---

## 35. Accountability

> [!important] Accountability
> Accountability means actions can be traced uniquely to the entity that performed them.

This supports:
- non-repudiation
- fault isolation
- intrusion detection
- legal or disciplinary action
- after-action recovery

### Example
Audit logs can show who modified a grade and when.

---

## 36. Linking Security Objectives Together

| Objective | Main role |
|---|---|
| Confidentiality | Protects information from unauthorized access |
| Integrity | Protects correctness and state |
| Availability | Keeps systems usable |
| Authentication | Establishes who can be trusted |
| Authenticity | Confirms the source is genuine |
| Accountability | Makes actions traceable |

### Important point
A system may satisfy one objective and fail another.

---

## 37. Trade-Off Examples

### Confidentiality vs Availability
A hospital may enforce very strong access checks, but delays in emergencies can hurt patient care.

### Availability vs Integrity
An exam platform may stay online but accept invalid submissions if validation is reduced.

### Integrity vs Confidentiality
Publishing detailed audit logs improves integrity and accountability, but may expose sensitive information.

### Authentication vs Availability
Too much authentication can make registration systems unavailable at peak times.

### Accountability vs Privacy
Extensive monitoring improves traceability but may reduce privacy.

### Confidentiality vs Usability
End-to-end encryption can be strong, but if keys are lost and no recovery exists, users may lose access to their own data.

---

## 38. From Objectives to Threats

Security objectives define what must be preserved.

That leads to the next question:
**what can threaten those objectives?**

This is why the next step in cybersecurity reasoning is threat analysis and threat modeling.

---

## 39. Important Words Only

| Word | Specific meaning | Example |
|---|---|---|
| Cybersecurity | Protection of systems against intentional attack | Defending against phishing |
| Design decision | Early choice that shapes security later | Trust boundary placement |
| Assumption | Something the system believes is true | “Users are trusted” |
| Asset | Something valuable to protect | Grades, email, records |
| Threat | Potential cause of harm | Phishing against email |
| Vulnerability | Exploitable weakness | Broken ownership check |
| Exposure | Whether a weakness can be reached | Public API |
| Risk | Harm from threat + vulnerability + exposure | Public flaw on a web app |
| Attack | Deliberate harmful action | Parameter tampering |
| Bug | Defect in code or design | Incorrect logic |
| Confidentiality | Prevent unauthorized disclosure | Hidden exam questions |
| Integrity | Prevent unauthorized modification | Correct grades |
| Availability | Keep services usable | Online registration |
| Authentication | Verify identity | Password login |
| Authenticity | Confirm genuine source | Real instructor submission |
| Accountability | Trace action to actor | Audit logs |
| Non-repudiation | Cannot deny an action convincingly | Signed logs |
| Privacy | Protection of personal rights | Limited employee tracking |
| Trust boundary | Where trust assumptions change | Browser to backend |
| Weakest link | Security depends on the most vulnerable point | A weak login breaks the system |
| Murphy’s law | Expect failure and misuse | Plan for worst-case events |

---

## 40. Final Takeaway

>[!summary] Final Idea
> Security begins with understanding what matters, what can go wrong, and why systems fail. The whole module builds one mental model: assets define value, threats define possible harm, vulnerabilities define weakness, exposure defines reachability, risk defines priority, and security objectives define what the system must preserve.