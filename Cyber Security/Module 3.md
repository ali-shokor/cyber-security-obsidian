# Cybersecurity Defense

> [!summary] Module Focus
> This module explains how network security mechanisms move from **threats** to **defense**. It focuses on protecting communication, limiting exposure, detecting malicious activity, and keeping services available under attack. The main idea is that defense does not eliminate all threats; it reduces risk through the right mix of preventive, protective, detective, and resilience mechanisms. 

---

## 1. From Threats to Defense

Security analysis starts by understanding:
- who attacks,
- why they attack,
- how they gain access,
- and why they persist. :contentReference[oaicite:1]{index=1}

Defense changes the perspective from attacker behavior to **system protection**. Network security mechanisms respond directly to observed threat patterns, but they focus on **risk reduction**, not complete threat elimination. :contentReference[oaicite:2]{index=2}

### Main idea
A defense mechanism should be understood conceptually before deployment, because a tool is only useful when its role and limits are clear. :contentReference[oaicite:3]{index=3}

---

## 2. Purpose of Network Security Mechanisms

Network security mechanisms exist to:

| Purpose | Meaning |
|---|---|
| Protect systems | Defend at the network and communication layers |
| Control communication | Decide who can talk to whom |
| Reduce exposure | Limit internal and external threats |
| Detect activity | Find suspicious or abnormal behavior |
| Preserve availability | Keep services working during attacks |
| Complement other layers | Work with host and application security |

These mechanisms are not meant to replace all other security controls. They support the overall defense strategy. :contentReference[oaicite:4]{index=4}

---

## 3. Core Objectives of Network Defense

> [!important] Network Defense Objectives
> Network defense is usually built around six goals: access control, isolation, protection, visibility, detection, and resilience. :contentReference[oaicite:5]{index=5}

| Objective      | Meaning                       | Simple example                       |
| -------------- | ----------------------------- | ------------------------------------ |
| Access Control | Restrict who can communicate  | Block unauthorized devices           |
| Isolation      | Limit attacker movement       | Separate departments into zones      |
| Protection     | Secure data in transit        | Encrypt traffic                      |
| Visibility     | Observe network behavior      | Monitor flows and logs               |
| Detection      | Identify malicious activity   | IDS alerts on suspicious traffic     |
| Resilience     | Maintain service availability | Keep a website online during a flood |

---

## 4. Why Categorize Network Defenses?

Network defenses do not all do the same job.

Some mechanisms:
- block traffic,
- some observe traffic,
- some absorb attack pressure,
- and some keep services alive under heavy load. :contentReference[oaicite:6]{index=6}

Categorizing defenses helps:
- understand their role,
- understand their limitations,
- compare them correctly in exams,
- avoid the idea that one tool solves everything. :contentReference[oaicite:7]{index=7}

---

## 5. Main Categories of Network Defense

| Category | Main role |
|---|---|
| Preventive | Block or restrict communication before access |
| Protective | Protect data and communication |
| Detective | Observe and analyze behavior |
| Resilience / Availability | Keep services usable during attack |

These categories often work together. A strong system usually needs all of them. 

---

# 6. Preventive Mechanisms

> [!important] Preventive Mechanisms
> Preventive controls act before or at the point of access. They reduce the exposed attack surface and enforce communication policy. :contentReference[oaicite:9]{index=9}

### Main role
- block or restrict communication
- enforce explicit policies
- reduce exposure
- prevent unauthorized access :contentReference[oaicite:10]{index=10}

### Limitation
They cannot detect every malicious action inside allowed traffic. :contentReference[oaicite:11]{index=11}

---

## 7. Firewalls

> [!important] Firewall
> A firewall is the first line of defense. It controls traffic based on predefined rules and filters traffic between trusted and untrusted zones. :contentReference[oaicite:12]{index=12}

### What it does
- decides which connections are allowed or denied
- enforces network boundaries
- protects against unauthorized access :contentReference[oaicite:13]{index=13}

### Limitation
- cannot detect attacks hidden inside allowed traffic
- cannot inspect encrypted payloads deeply in every case :contentReference[oaicite:14]{index=14}

### Types of firewalls

| Type | What it checks | Strength | Limitation |
|---|---|---|---|
| Packet-filtering firewall | Packet headers such as IP, port, and protocol | Fast and simple | Blind to payload content |
| Stateful firewall | Active connections and session state | Better context than packet filters | Limited for complex threats |
| Next-generation firewall | Application awareness and deep packet inspection | Can detect malware and block applications | More complex to manage |

### Simple example
A firewall may allow HTTPS traffic but still fail to notice malicious content hidden inside that traffic unless it has deeper inspection capability. :contentReference[oaicite:15]{index=15}

---

## 8. Packet-Filtering Firewalls

Packet-filtering firewalls inspect packet headers only, such as:
- IP address,
- port,
- protocol. :contentReference[oaicite:16]{index=16}

They are fast and useful, but they cannot see the payload. That means they may allow bad content if it arrives inside a permitted packet. :contentReference[oaicite:17]{index=17}

---

## 9. Stateful Firewalls

Stateful firewalls track active connections.

They allow traffic that belongs to known sessions, so they are smarter than simple packet filters. However, they still have limits when facing more complex threats. :contentReference[oaicite:18]{index=18}

### Simple example
If a connection is already established, the firewall may allow return traffic automatically because it recognizes the session state. :contentReference[oaicite:19]{index=19}

---

## 10. Next-Generation Firewalls

Next-generation firewalls add:
- application awareness,
- deep packet inspection,
- malware detection,
- application blocking,
- and often intrusion prevention features. :contentReference[oaicite:20]{index=20}

### Simple example
A next-generation firewall may block a risky application even if the traffic uses a normal port. :contentReference[oaicite:21]{index=21}

---

## 11. Network Access Control (NAC)

> [!important] NAC
> Network Access Control decides which devices may join the network and usually requires authentication before access is granted. :contentReference[oaicite:22]{index=22}

### Why it matters
- distinguishes trusted and untrusted endpoints
- reduces risk from rogue devices
- helps prevent unmanaged devices from connecting :contentReference[oaicite:23]{index=23}

### Simple example
A laptop cannot join the internal network unless it authenticates and meets the access policy. :contentReference[oaicite:24]{index=24}

---

## 12. Network Segmentation

> [!important] Network Segmentation
> Network segmentation divides a network into isolated zones to limit lateral movement and reduce the blast radius of attacks. :contentReference[oaicite:25]{index=25}

### Why it matters
- isolates systems
- limits damage after compromise
- is a structural and architectural defense
- depends heavily on correct design :contentReference[oaicite:26]{index=26}

### Simple example
If a user device is compromised, segmentation can stop the attacker from moving easily to servers or admin systems. :contentReference[oaicite:27]{index=27}

---

# 13. Protective Mechanisms

> [!important] Protective Mechanisms
> Protective controls focus on confidentiality and integrity. They protect data and communications, but they do not block traffic by themselves. :contentReference[oaicite:28]{index=28}

They are often transparent to users and are essential, but not sufficient alone. :contentReference[oaicite:29]{index=29}

---

## 14. Encryption for Network Communications

Encryption protects data in transit from eavesdropping and helps ensure confidentiality and integrity. It is critical against interception and man-in-the-middle attacks. :contentReference[oaicite:30]{index=30}

### Simple example
When you log in over HTTPS, encryption helps stop an attacker on the network from reading your password or session data. :contentReference[oaicite:31]{index=31}

---

## 15. Virtual Private Networks (VPNs)

> [!important] VPN
> A VPN creates a secure tunnel over an untrusted network, authenticates endpoints, and encrypts traffic. :contentReference[oaicite:32]{index=32}

### Main uses
- secure remote work
- connect branch offices
- protect public Wi-Fi sessions :contentReference[oaicite:33]{index=33}

### Main limitation
A VPN can extend trust to compromised endpoints, and it usually does not inspect internal traffic. :contentReference[oaicite:34]{index=34}

### Common VPN protocols
| Protocol | Use |
|---|---|
| IPsec | Widely used and secure |
| SSL/TLS VPN | Easier to deploy for remote access |

---

## 16. VPN Types

### Site-to-Site VPN
Connects two networks, such as a branch office and headquarters, usually transparently. It often uses IPsec tunnels between gateways. A weakness on one side can affect the trust between connected networks. :contentReference[oaicite:35]{index=35}

### Remote Access VPN
Connects individual users or devices to a private network. It depends on endpoint trust and credential protection. :contentReference[oaicite:36]{index=36}

### Cloud Remote Access VPN
Provides VPN access through cloud-hosted gateways. It scales well and often integrates with SSO and MFA, but it also introduces dependency on cloud trust. :contentReference[oaicite:37]{index=37}

### SSL VPN
Uses TLS/SSL instead of IPsec, is easier to deploy, and often gives application-level access rather than full network access. :contentReference[oaicite:38]{index=38}

### Multi-hop VPN
Routes traffic through multiple VPN servers to add layered encryption and anonymity, but it increases latency and overhead. :contentReference[oaicite:39]{index=39}

---

# 17. Detective Mechanisms

> [!important] Detective Mechanisms
> Detective controls observe and analyze network behavior to identify suspicious or malicious activity. They usually act after access has already happened. :contentReference[oaicite:40]{index=40}

### Main role
- observe traffic
- analyze behavior
- identify threats
- support response and investigation :contentReference[oaicite:41]{index=41}

### Important limitation
Visibility alone does not equal detection. A system can collect lots of data and still fail to understand it. :contentReference[oaicite:42]{index=42}

---

## 18. Network Monitoring

Network monitoring collects:
- traffic,
- flow data,
- metadata. :contentReference[oaicite:43]{index=43}

### Why it matters
- gives visibility
- establishes normal baselines
- supports investigation and forensics :contentReference[oaicite:44]{index=44}

### Example
Monitoring may show unusual traffic volume or unexpected connections, which can later help explain an incident. :contentReference[oaicite:45]{index=45}

---

## 19. IDS

> [!important] IDS
> An Intrusion Detection System analyzes traffic for known or anomalous patterns and generates alerts for suspicious activity. It does not automatically stop the attack. :contentReference[oaicite:46]{index=46}

### What it can detect
- exploitation
- malware activity
- suspicious patterns :contentReference[oaicite:47]{index=47}

### Example
An IDS may alert when it sees a pattern that matches a known exploit signature. :contentReference[oaicite:48]{index=48}

---

## 20. IPS

> [!important] IPS
> An Intrusion Prevention System actively blocks malicious traffic after detection. It combines detection with enforcement. :contentReference[oaicite:49]{index=49}

### Strength
It reduces reaction time because it can stop traffic automatically. :contentReference[oaicite:50]{index=50}

### Limitation
False positives may disrupt services. :contentReference[oaicite:51]{index=51}

### Simple example
If an IPS thinks a request is malicious, it may drop it before it reaches the server. :contentReference[oaicite:52]{index=52}

---

## 21. SIEM

> [!important] SIEM
> A SIEM aggregates, normalizes, correlates, and analyzes security-relevant events across systems. :contentReference[oaicite:53]{index=53}

### What SIEM does
- collects logs from many sources
- normalizes them into a common format
- correlates events across systems
- alerts on suspicious patterns :contentReference[oaicite:54]{index=54}

### Strengths
- centralized visibility
- correlation of distributed events
- supports forensic analysis :contentReference[oaicite:55]{index=55}

### Limitations
- depends on log quality and coverage
- cannot detect what is not logged
- may produce false positives or false negatives
- has limited visibility into encrypted traffic
- still needs human analysis :contentReference[oaicite:56]{index=56}

### SIEM vs IDS vs Firewall

| Tool | Main purpose |
|---|---|
| Firewall | Controls traffic based on rules |
| IDS / IPS | Detects or blocks known threats |
| SIEM | Correlates events across systems |

SIEM complements the other tools; it does not replace them. :contentReference[oaicite:57]{index=57}

---

# 22. Resilience and Availability Mechanisms

> [!important] Resilience
> Resilience mechanisms assume attacks will happen and try to keep services available by reducing impact rather than preventing every attack. :contentReference[oaicite:58]{index=58}

### Why they matter
- critical for public-facing services
- complement preventive and detective controls
- help maintain service under attack :contentReference[oaicite:59]{index=59}

---

## 23. DoS and DDoS Mitigation

DoS and DDoS mitigation protects services against traffic floods and excessive malicious traffic. It often relies on:
- scale,
- filtering,
- distribution. :contentReference[oaicite:60]{index=60}

### Limitation
Large-scale attacks cannot always be fully prevented. :contentReference[oaicite:61]{index=61}

### Simple example
A service may use traffic filtering or cloud scaling to stay online during a flood of requests. :contentReference[oaicite:62]{index=62}

---

## 24. Rate Limiting and Traffic Shaping

Rate limiting restricts abusive or excessive requests to protect system resources. Traffic shaping controls how traffic flows. :contentReference[oaicite:63]{index=63}

### Why it matters
- protects resources
- helps against low-rate attacks
- simple but powerful
- may affect legitimate users if too strict :contentReference[oaicite:64]{index=64}

### Simple example
A login page may allow only a few attempts per minute to reduce brute-force abuse. :contentReference[oaicite:65]{index=65}

---

# 25. Main exam idea

> [!summary] Final Idea
> Network defense is about choosing the right control for the right purpose: **prevent** access, **protect** data, **detect** behavior, and **preserve** availability. No single tool is enough on its own. 

---

# 26. Important Words Only

| Word | Specific meaning | Example |
|---|---|---|
| Network defense | Security controls that protect communication and availability | Firewall, IDS, VPN |
| Preventive mechanism | Stops or restricts access | Firewall, NAC |
| Protective mechanism | Protects confidentiality/integrity | Encryption, VPN |
| Detective mechanism | Finds suspicious activity | IDS, SIEM |
| Resilience mechanism | Keeps service available during attacks | Rate limiting, DDoS mitigation |
| Firewall | Filters traffic by rules | Block unauthorized ports |
| Packet filtering | Checks packet headers | IP, port, protocol |
| Stateful firewall | Tracks sessions | Allows return traffic in a session |
| NGFW | Firewall with deep inspection and app awareness | Block risky apps |
| NAC | Controls which devices can join the network | Reject unknown devices |
| Segmentation | Splits network into zones | Separate user and server zones |
| Encryption | Scrambles data in transit | HTTPS |
| VPN | Secure tunnel over untrusted network | Remote work access |
| IDS | Detects suspicious traffic | Alert on exploit pattern |
| IPS | Detects and blocks malicious traffic | Drop attack packets |
| SIEM | Correlates logs and events across systems | Central security dashboard |
| Monitoring | Collecting traffic and metadata | Track unusual flows |
| Availability | Keeping a service usable | Website stays online |
| DoS | Attack that makes a service unavailable | Traffic flood |
| DDoS | DoS from multiple systems | Botnet flood |
| Rate limiting | Limits request frequency | Stop login abuse |
| Traffic shaping | Controls traffic flow | Smooth heavy traffic |
| Trust boundary | Point where trust level changes | User input to backend |
| Attack surface | Places where a system can be reached | Web form, API, admin panel |
| Lateral movement | Moving deeper after compromise | Attacker reaches servers |
| Blast radius | How far damage spreads | Segmentation reduces it |
| Visibility | Ability to observe network behavior | Logs, flows, alerts |
| Detection | Identifying malicious activity | IDS alert |
| Resilience | Ability to keep working during attack | DDoS-resistant service |

---

## 27. Very short closing summary

This module says that network defense is built from different layers with different jobs. Firewalls and NAC prevent access, encryption and VPNs protect communication, IDS and SIEM detect suspicious behavior, and rate limiting plus DDoS mitigation help keep services available. Good defense combines all of them instead of depending on one tool. 