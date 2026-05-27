**Module 2 — Cyber Threat Landscape**  
Ready to paste into Obsidian.

> [!summary] Module Focus
> This module explains how cybersecurity starts with **assets**, then looks at **adversaries**, **trust**, **attack surfaces**, **vulnerabilities**, **exploits**, **threats**, and **attacks**. It shows that many real incidents happen because systems trust the wrong things, expose too much, or fail to model risk early. It also introduces threat modeling as the structured way to connect assets, attackers, weak points, and likely impact.

---

# 1) Core Idea

Cybersecurity is not just “blocking hackers.”  
It is about understanding:

- what matters,
- who might attack,
- what they want,
- how they can reach it,
- what weaknesses they can use,
- and what damage they can cause.

---

# 2) Assets

> [!important] Asset
> An asset is anything that has value and needs protection. Assets give meaning to security objectives, because security mechanisms exist to protect them.

## Common asset categories

| Asset type         | What it means                                   | Example                          |
| ------------------ | ----------------------------------------------- | -------------------------------- |
| Data               | Personal, financial, or proprietary information | Student records, bank data       |
| Identity           | Credentials and authentication material         | Passwords, tokens                |
| Service            | Availability and continuity of operation        | A portal staying online          |
| Integrity          | Correctness of records and transactions         | Correct grades, correct payments |
| Control            | Administrative or privileged access             | Admin account                    |
| Trust / reputation | Confidence in the system or organization        | User trust in a platform         |

These categories matter because different systems care about different things, and the same asset can matter differently depending on context. For example, in one system availability may matter more, while in another integrity may matter more.

### Simple example

A university portal protects grade data and transcripts, while a payment system may care more about transaction integrity and financial records.

---

# 3) Why assets matter

Assets determine:

- what attackers want,
- how much effort they may invest,
- where protection should be strongest,
- and which systems are truly critical.

If assets are identified incorrectly, security controls may be placed in the wrong place.

---

# 4) Adversaries / Threat Actors

> [!important] Adversary
> An adversary is an entity that intentionally causes harm. Cyber attacks are deliberate, not accidental.

Adversaries have:

- goals,
- incentives,
- and constraints.

## Main adversary categories

|Category|Meaning|Example|
|---|---|---|
|External attacker|No legitimate access|Internet attacker scanning systems|
|Malicious authenticated user|Has valid access but abuses it|User misusing a portal|
|Insider|Has privileged or internal access|Disgruntled employee|
|Third-party / supply-chain adversary|Comes through trusted vendors or services|Compromised software update|
|Automated / opportunistic attacker|Uses scripts and tools at scale|Script kiddie scanning the web|

Adversaries also differ by motivation and skill:

- script kiddies,
- hacktivists,
- cybercriminal groups,
- disgruntled employees,
- state-sponsored or strategic actors.

### Simple examples

- A script kiddie may scan for exposed systems using public tools.
- A hacktivist may target symbolic systems for visibility or protest.
- An insider may abuse legitimate access without needing malware.
- A state-sponsored actor may focus on stealth, long-term access, and intelligence gathering.

---

# 5) Trust

> [!important] Trust
> Trust defines which actions are allowed without verification. Systems rely on trust to function efficiently, but excessive trust increases exposure.

## Explicit vs implicit trust

|Type|Meaning|Risk|
|---|---|---|
|Explicit trust|Clearly defined and enforced|Easier to review|
|Implicit trust|Hidden assumption in design|Harder to audit and often abused|

Implicit trust is dangerous because attackers actively look for it, and developers may not even realize it is there.

### Simple example

A university portal may authenticate users correctly, but still fail if it assumes every logged-in user only requests their own records. That is implicit trust in user behavior.

---

# 6) Authentication vs Authorization

Authentication answers: **Who are you?**  
Authorization answers: **What are you allowed to do?**

Authentication does **not** imply authorization. Confusing the two leads to access-control flaws.

### Example

A user may log in successfully, but still should not be allowed to access another student’s grade report.

---

# 7) Trust Boundaries

> [!important] Trust Boundary
> A trust boundary separates components with different trust levels. Data crossing that boundary must be validated.

Trust boundaries are often:

- between external and internal systems,
- between users and services,
- between privilege levels,
- between network segments.

### Example

User input always crosses a trust boundary, so it should never be trusted by default.

---

# 8) Attack Surface

> [!important] Attack Surface
> An attack surface is the set of points where a system can be interacted with. Every interface is a potential attack surface.

## Common attack surfaces

| Type                   | Example                      |
| ---------------------- | ---------------------------- |
| User-facing interfaces | Web pages, forms             |
| Network services       | Open ports, exposed services |
| APIs                   | Backend endpoints            |
| File handling          | Upload/download features     |
| Authentication systems | Login, sessions              |
| Management interfaces  | Admin panels                 |

Attack surfaces matter because attackers cannot exploit what they cannot reach. Larger systems and new features usually create more exposure.

### Input-based attack surface

User input is inherently untrusted, and bad validation creates exploitation paths.

### Example

A public web form that accepts unsanitized input becomes a major attack surface.

---

# 9) Vulnerabilities

> [!important] Vulnerability
> A vulnerability is a weakness that can be exploited. It can exist in code, configuration, or design.

## Types of vulnerabilities

|Type|Meaning|Example|
|---|---|---|
|Technical vulnerability|Comes from code or implementation errors|Log4Shell-style flaw|
|Logical vulnerability|Comes from flawed logic or assumptions|IDOR / broken ownership check|

Technical vulnerabilities are often easier to scan for, while logical vulnerabilities usually require human analysis because they are system-specific.

### Example

A system may correctly authenticate a user but fail to verify whether a requested resource belongs to that user. That is a logical vulnerability.

---

# 10) Exploits

> [!important] Exploit
> An exploit is the method used to leverage a vulnerability. It turns weakness into control.

Not every vulnerability has a usable exploit, but when one exists, it becomes a practical attack path.

### Example

A SQL injection flaw becomes dangerous when an attacker sends crafted input that changes the database query behavior.

---

# 11) Threats

> [!important] Threat
> A threat is a potential cause of unwanted harm. It requires an adversary, a goal, a target asset, and a feasible path.

## Threat formula

**Threat = adversary + goal + path to asset**

### Example

A ransomware group targeting a file transfer system for data theft and extortion is a threat scenario because it includes:

- an adversary,
- a goal,
- a vulnerability,
- an asset,
- and a path.

---

# 12) Attack vs Threat

> [!important] Attack
> An attack is the deliberate execution of a threat. It is a sequence of actions that exploits vulnerabilities through attack surfaces.

A threat is the possibility of harm.  
An attack is the real action that tries to make that harm happen.

### Example

Phishing is a threat type; sending the fake email and stealing credentials is the attack.

---

# 13) Attack Chain

Attacks usually happen in stages, not randomly. Common stages include:

- reconnaissance,
- preparation,
- initial access,
- escalation,
- persistence,
- execution,
- escape.

Breaking one stage can stop the whole progression.

### Simple example

An attacker may first scan a target, then gain access using stolen credentials, then move deeper, then steal data, then hide traces.

---

# 14) Common attack types

## Phishing

Phishing tries to steal sensitive information such as usernames, passwords, or credit card data by pretending to be a legitimate source.

### Examples

- “Your account has been compromised”
- “You have won a prize”
- “Urgent action required”
- “Fake invoice or payment request”
- “Fake job offer”
- “Update your account information”
- “Fake charity donation request”
- “Fake tech support”

## Malware

Malware is malicious software that performs unauthorized actions and supports attacker objectives. It is a tool, not the attack itself.

## Social engineering

Social engineering is psychological manipulation used to make people reveal confidential information or perform harmful actions.

## Denial of Service

A DoS attack makes a system unavailable by overwhelming resources or exploiting limits. DDoS uses multiple compromised systems.

## Physical theft

Physical theft can target devices directly, temporarily or permanently.

---

# 15) Malware types

|Malware type|What it does|Simple example|
|---|---|---|
|Virus|Attaches to legitimate files and spreads through execution|A file-infected payload|
|Worm|Self-propagates across networks without user action|Network-spreading malware|
|Trojan|Disguises itself as legitimate software|Fake installer|
|Ransomware|Encrypts data and demands payment|File-encryption extortion|
|Backdoor|Gives repeated remote access|Hidden access route|
|Spyware|Collects sensitive information secretly|Credential/location capture|

Malware may support data theft, surveillance, extortion, service disruption, credential harvesting, or botnet participation.

### Important distinction

Not every cyberattack uses malware. Some rely only on social engineering or logical exploitation.

---

# 16) Persistence

> [!important] Persistence
> Persistence allows continued access after compromise. It transforms a single intrusion into a long-term campaign.

Persistence can use:

- backdoors,
- stolen credentials,
- session hijacking,
- account creation,
- service installation,
- scheduled tasks.

### Why it matters

Long dwell time increases damage, and longer detection delay usually means bigger impact.

### Example

A backdoor may bypass normal authentication and allow repeated access silently.

---

# 17) Least Privilege

> [!important] Least Privilege
> Users, processes, and components should get only the permissions they strictly need.

Least privilege:

- limits scope,
- limits duration,
- reduces lateral movement,
- reduces privilege escalation,
- reduces overall attack surface.

### Good example

In an e-commerce system:

- customers manage only their own orders,
- support staff can view orders and issue refunds,
- administrators manage system settings,
- backend services use narrow database permissions.

### Bad example

If all authenticated users share one broad role and the backend trusts frontend checks only, one compromise can expose the whole system.

---

# 18) Transitive Trust

> [!important] Transitive Trust
> Transitive trust happens when trust is extended indirectly through another trusted entity. Attackers exploit trust chains rather than just single systems.

### Example

A trusted software vendor sends an update, and customers automatically deploy it inside their internal network. If the vendor is compromised, the trust chain becomes a path into many organizations.

### Why it is dangerous

A single compromised component can affect many systems, expand the attack surface silently, and bypass controls legitimately.

---

# 19) Trust management in design

Good systems:

- treat third-party systems as untrusted by default,
- validate even trusted components,
- segment trust boundaries,
- minimize inherited permissions,
- make trust relationships explicit and reviewable.

Over-trust increases exposure. Under-trust can reduce usability. Security requires deliberate balancing.

---

# 20) Threat modeling

> [!important] Threat Modeling
> Threat modeling is structured security reasoning. It connects assets, adversaries, attack surfaces, vulnerabilities, paths, persistence, and impact.

## Why threat modeling matters

- systems are complex,
- adversaries adapt,
- not all weaknesses matter equally,
- defensive resources are limited,
- structured analysis reduces blind spots,
- prevention is better than reaction.

## Threat modeling steps

|Step|What you do|
|---|---|
|System decomposition|Break the system into components|
|Trust boundaries|Find where trust changes|
|Threat enumeration|List adversaries, goals, vulnerabilities, paths|
|Prioritization|Rank likely and high-impact threats|
|Review|Use the analysis in design and code review|

Threat modeling makes assumptions explicit and supports secure design decisions.

### Practical questions

- What are the critical assets?
- Who might target them?
- Where are the trust boundaries?
- How could exploitation occur?
- What enables persistence?
- What would the impact be?

---

# 21) STRIDE

> [!important] STRIDE
> STRIDE is a threat categorization model used in threat modeling.

|STRIDE category|Meaning|
|---|---|
|Spoofing|Impersonating an entity|
|Tampering|Unauthorized data modification|
|Repudiation|Denying actions without proof|
|Information Disclosure|Unauthorized data access|
|Denial of Service|Disrupting availability|
|Elevation of Privilege|Gaining higher permissions|

---

# 22) Data Flow Diagram (DFD) elements

|DFD element|Meaning|
|---|---|
|External entity|User or external system|
|Process|Application or service that performs computation|
|Data store|Database or file storage|
|Data flow|Movement of data between elements|
|Trust boundary|Change in trust level between components|

DFDs help threat modeling by showing how data moves and where trust changes.

---

# 23) Threat modeling tools

## Microsoft Threat Modeling Tool

A desktop tool based on DFDs that maps elements to STRIDE threats, generates threat lists per component, and supports documentation.

## OWASP Threat Dragon

An open-source, web-based tool that supports STRIDE-based threat enumeration and exports models for documentation.

### Limitation of tools

Tools help structure analysis, but they do not replace expert judgment. They depend on accurate modeling and may generate too many generic threats if the model is weak.

---

# 24) Final mental model

> [!summary] Entire Module in One Line
> **Assets define what matters, adversaries define who acts, threats define possible harm, attacks define execution, exploits define the mechanism, and persistence defines how long damage can continue.**

---

# 25) Important Words Only

|Word|Specific meaning|Example|
|---|---|---|
|Asset|Something valuable that needs protection|Grades, credentials, money|
|Adversary|Someone who intentionally causes harm|Insider, hacker, state actor|
|Trust|What the system accepts without checking|Logged-in user assumed trusted|
|Explicit trust|Trust clearly defined and enforced|Authentication check|
|Implicit trust|Hidden trust assumption|Assuming users only access their own data|
|Trust boundary|Place where trust changes|User input entering backend|
|Attack surface|Points where the system can be reached|Web form, API, admin panel|
|Vulnerability|Weakness that can be exploited|SQL injection flaw|
|Technical vulnerability|Code/configuration weakness|Unpatched software flaw|
|Logical vulnerability|Design/logic weakness|Broken ownership check|
|Exploit|Technique used to abuse a weakness|Crafted input triggering SQLi|
|Threat|Possible cause of harm|Ransomware targeting files|
|Attack|Deliberate execution of a threat|Sending phishing emails|
|Attack chain|Steps used to reach the goal|Recon → access → escalate → persist|
|Phishing|Fake message to steal data|Fake login page email|
|Malware|Malicious software|Trojan, worm, ransomware|
|Ransomware|Malware that encrypts data for payment|Locked files and ransom note|
|Backdoor|Hidden access path|Silent remote access|
|Spyware|Software that secretly collects data|Capturing credentials|
|Persistence|Staying inside after compromise|Backdoor, stolen token|
|Least privilege|Minimum permissions needed|Support staff cannot change prices|
|Transitive trust|Trust inherited through another trusted system|Trusted vendor update compromise|
|Threat modeling|Structured analysis of attack risk|Mapping assets and trust boundaries|
|STRIDE|Threat categories model|Spoofing, Tampering, etc.|
|DFD|Diagram of data movement and components|User → process → database|
|DoS|Making a system unavailable|Overloading a service|
|DDoS|DoS from many systems|Botnet traffic flood|

---

# 26) Very short closing summary

This module says that cybersecurity begins by identifying assets and understanding who may attack them. Then it looks at trust, trust boundaries, attack surfaces, vulnerabilities, exploits, threats, and attacks. The final goal is to use threat modeling so security decisions are structured, realistic, and based on how attackers actually operate.