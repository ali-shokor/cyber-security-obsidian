# I3336 — Introduction to Cybersecurity

## Module 5: Operating System and System Security

**Instructor:** Ahmad Fadlallah  
**Academic Year:** 2025–2026

> [!summary] Module Focus  
> Operating systems are the enforcement layer of security. This module explains how OS trust models, privilege separation, hardening, patching, and configuration management reduce the impact of attacks — and how misconfiguration often defeats even strong security design.

---

## Table of Contents

1. [Big Picture](https://chatgpt.com/c/69e4baa5-e1b4-83eb-8c2d-bc55a4921543#big-picture)
    
2. [Why OS Security Matters](https://chatgpt.com/c/69e4baa5-e1b4-83eb-8c2d-bc55a4921543#why-os-security-matters)
    
3. [Trust Models and the Trusted Computing Base](https://chatgpt.com/c/69e4baa5-e1b4-83eb-8c2d-bc55a4921543#trust-models-and-the-trusted-computing-base)
    
4. [User Space vs Kernel Space](https://chatgpt.com/c/69e4baa5-e1b4-83eb-8c2d-bc55a4921543#user-space-vs-kernel-space)
    
5. [Privilege Levels](https://chatgpt.com/c/69e4baa5-e1b4-83eb-8c2d-bc55a4921543#privilege-levels)
    
6. [Principle of Least Privilege](https://chatgpt.com/c/69e4baa5-e1b4-83eb-8c2d-bc55a4921543#principle-of-least-privilege)
    
7. [Privilege Escalation](https://chatgpt.com/c/69e4baa5-e1b4-83eb-8c2d-bc55a4921543#privilege-escalation)
    
8. [Process Isolation](https://chatgpt.com/c/69e4baa5-e1b4-83eb-8c2d-bc55a4921543#process-isolation)
    
9. [System Hardening](https://chatgpt.com/c/69e4baa5-e1b4-83eb-8c2d-bc55a4921543#system-hardening)
    
10. [Patch and Configuration Management](https://chatgpt.com/c/69e4baa5-e1b4-83eb-8c2d-bc55a4921543#patch-and-configuration-management)
    
11. [Misconfiguration as an Attack Vector](https://chatgpt.com/c/69e4baa5-e1b4-83eb-8c2d-bc55a4921543#misconfiguration-as-an-attack-vector)
    
12. [Final Takeaways](https://chatgpt.com/c/69e4baa5-e1b4-83eb-8c2d-bc55a4921543#final-takeaways)
    
13. [Quick Revision Table](https://chatgpt.com/c/69e4baa5-e1b4-83eb-8c2d-bc55a4921543#quick-revision-table)
    
14. [Self-Test Questions](https://chatgpt.com/c/69e4baa5-e1b4-83eb-8c2d-bc55a4921543#self-test-questions)
    

---

## Big Picture

> [!important] Core Idea  
> Most real-world compromises do not begin with sophisticated exploitation. They begin with weak configuration, excessive privilege, unnecessary services, or delayed patching.

### Typical attack path

| Stage                | What happens                    | Example                                               |
| -------------------- | ------------------------------- | ----------------------------------------------------- |
| Initial access       | Attacker gets a foothold        | Weak password, exposed service, vulnerable web app    |
| Limited execution    | Code runs with low privileges   | Guest account, normal user, service account           |
| Privilege escalation | Attacker gains higher rights    | Misconfigured sudo, vulnerable service, admin session |
| Full compromise      | Entire system can be controlled | Root on Linux or Administrator on Windows             |

### Key observation

A system can be secure in theory but insecure in practice if it is poorly configured.

---

## Why OS Security Matters

The operating system is the central authority that manages:

- hardware access
    
- memory
    
- processes
    
- files
    
- users
    
- network resources
    

All applications depend on the OS to enforce:

- security
    
- isolation
    
- access control
    

> [!example] Example  
> A browser may be safe by itself, but if the OS allows unrestricted access to sensitive files or privileged services, the browser is still exposed to serious risk.

### Why a weakness at OS level is serious

|OS weakness|Impact|
|---|---|
|Poor permissions|Sensitive files can be read or modified|
|Misconfigured services|Attackers can access internal functionality|
|Weak privilege model|Users or processes can gain excessive power|
|Missing patches|Known vulnerabilities remain exploitable|

---

## Trust Models and the Trusted Computing Base

### Trust model

A trust model defines:

- which components are trusted
    
- which components are untrusted
    
- how trust is enforced by the OS
    

### Trusted vs untrusted components

|Category|Components|Security meaning|
|---|---|---|
|Trusted|Kernel, core services, authentication system|Must be protected because compromise breaks the system|
|Untrusted|User applications, external input, downloaded files|Must be restricted and validated|

> [!example] Example  
> A regular user program should never directly modify system-critical files. If it can do that, the trust model has failed.

### Trusted Computing Base (TCB)

The TCB is the set of components that must remain secure for the system to be trusted.

|TCB Element|Why it matters|
|---|---|
|Kernel|Controls core system behavior|
|Authentication mechanisms|Protects identity and login control|
|Core system services|Supports system operation and access control|

> [!important] Security Principle  
> A smaller TCB is easier to protect. A larger TCB creates a larger attack surface.

### Why TCB protection matters

If a TCB component is compromised, the attacker may gain control of the whole machine.

---

## User Space vs Kernel Space

### Separation model

|Space|Role|Example|
|---|---|---|
|User space|Runs applications|Browser, editor, media player|
|Kernel space|Runs the OS core|Memory management, scheduling, device control|

This separation is enforced by hardware and the OS.

> [!example] Example  
> If a browser crashes in user space, the OS should still continue running normally. If the kernel is compromised, the attacker may control the whole system.

### Why this separation matters

- prevents user programs from accessing critical memory directly
    
- limits damage from buggy or malicious apps
    
- protects the OS core from ordinary application failures
    

---

## Privilege Levels

### Concept

Privilege level determines what a user or process is allowed to do.

### General hierarchy

|Level|Meaning|
|---|---|
|High privilege|Full or near-full control|
|Low privilege|Restricted actions|

Privileges are tied to:

- user accounts
    
- processes
    
- group memberships
    

### Linux privilege model

|Account type|Meaning|Typical ability|
|---|---|---|
|Root (UID 0)|Superuser|Full system control|
|Regular user|Standard account|Limited to permitted files and commands|

#### Linux commands to inspect identity

```bash
whoami
id
sudo -l
```

> [!example] Example  
> If `sudo -l` shows that a user can run many commands as root, that user has a higher risk of accidental or malicious privilege escalation.

### Windows privilege model

|Account type|Meaning|Typical ability|
|---|---|---|
|Administrator|Elevated user|Can install software and change system settings|
|Standard user|Limited user|Cannot make critical system changes|

Windows uses **User Account Control (UAC)** to reduce accidental elevation.

#### Windows commands to inspect identity

```powershell
whoami
whoami /groups
```

> [!example] Example  
> A user may belong to the Administrators group but still run in a non-elevated session until UAC approval is granted.

### Linux vs Windows privilege model

|Aspect|Linux|Windows|
|---|---|---|
|Main distinction|Root vs regular users|Administrator vs standard users|
|Control mechanism|Permissions, ownership, sudo|Groups, UAC, policy controls|
|Style|More explicit and direct|More flexible and layered|
|Security lesson|Security depends on correct configuration|Security depends on correct configuration|

---

## Principle of Least Privilege

### Definition

Give each user, process, or service only the permissions required to do its job.

### Why it matters

- reduces attack surface
    
- limits damage if a system is compromised
    
- prevents unnecessary access to sensitive resources
    

> [!example] Example  
> A printer service that only needs to read print jobs should not also have permission to delete system logs or modify user accounts.

### Practical interpretation

|Entity|Least privilege means|
|---|---|
|User|Only access the files and tools needed|
|Application|Only the APIs and resources required|
|Service|Only the ports, files, and privileges necessary|

---

## Privilege Escalation

### Definition

Privilege escalation means gaining higher permissions than intended.

### Types

|Type|Meaning|Example|
|---|---|---|
|Vertical escalation|Low privilege to high privilege|User to admin/root|
|Horizontal escalation|Access another account at similar level|User A to User B|

### Common escalation chain

1. attacker gains foothold
    
2. attacker executes limited code
    
3. attacker finds a weakness or misconfiguration
    
4. attacker escalates privileges
    
5. attacker reaches full compromise
    

> [!example] Example  
> If a user can run a sensitive command through a misconfigured `sudo` rule, a limited account can become root.

### Why privilege escalation is dangerous

A small flaw can become a full-system compromise when the exploited process already has high rights.

---

## Process Isolation

### Definition

Each process runs in its own memory space.

### Why it matters

- one application should not read or overwrite another application's memory
    
- one compromised process should not automatically infect the whole system
    
- isolation limits damage and slows attacker movement
    

> [!example] Example  
> If a text editor crashes, it should not be able to corrupt the memory of the web browser or the OS kernel.

---

## System Hardening

### Definition

System hardening is the process of reducing vulnerabilities by tightening configuration and removing unnecessary exposure.

### Goal

Reduce the attack surface as much as possible without breaking essential functionality.

### Attack surface

The attack surface includes all possible entry points into a system:

- open ports
    
- running services
    
- user accounts
    
- network interfaces
    
- exposed directories
    

|Larger attack surface|Smaller attack surface|
|---|---|
|More opportunities for attackers|Fewer opportunities for attackers|

### Main hardening actions

|Action|Purpose|Example|
|---|---|---|
|Disable unnecessary services|Reduce exposure|Turn off FTP if unused|
|Close unused ports|Remove entry points|Block unused listening ports|
|Enforce strong authentication|Prevent easy access|Unique strong passwords|
|Restrict privileges|Limit damage|Avoid admin access for daily work|
|Enable logging and monitoring|Detect attacks|Keep security logs enabled|

### Identifying open ports

#### Linux

```bash
ss -tuln
netstat -tuln
```

#### Windows

```powershell
netstat -ano
```

> [!example] Example  
> If port 21 is open for FTP but no FTP service is needed, that port should be closed.

### Secure configuration principles

|Principle|Meaning|
|---|---|
|Secure by design is not enough|A system can still be insecure if misconfigured|
|Default is not always safe|Defaults may be convenient, not secure|
|Explicit control is necessary|Security settings should be intentionally chosen|

### Defense in depth

Security should rely on multiple layers.

|Layer|Example|
|---|---|
|Network|Firewall|
|Identity|Authentication|
|Endpoint|Antivirus / endpoint protection|
|Monitoring|Logging and alerts|
|OS controls|Permissions and privilege separation|

> [!important] Idea  
> If one layer fails, another layer should still reduce the impact of the attack.

### Logging and monitoring

Hardening is not only prevention. It is also detection.

Systems should log:

- login attempts
    
- privilege changes
    
- configuration changes
    
- suspicious service activity
    

> [!example] Example  
> If an unknown account tries repeated logins, logs can help detect the activity before a compromise spreads.

---

## Patch and Configuration Management

### Why updates matter

Software is never perfectly secure. Bugs and vulnerabilities are discovered continuously.

### Patch management

Patch management is the process of:

- identifying updates
    
- acquiring them
    
- testing them
    
- applying them
    

### Why patching matters

|Situation|Risk|
|---|---|
|System is patched|Known flaws are harder to exploit|
|System is unpatched|Known flaws remain easy targets|

### Vulnerability lifecycle

|Stage|Description|
|---|---|
|Discovery|A flaw is found|
|Disclosure|The flaw becomes known publicly or to vendors|
|Patch release|A fix is released|
|Exploitation|Attackers build or adapt exploits|

> [!example] Example  
> In large-scale attacks, attackers often target systems that have not yet applied publicly available fixes.

### Patch management commands

#### Linux

```bash
apt list --upgradable
```

#### Windows

Use Windows Update settings to check pending updates.

### Patch management trade-offs

|Option|Benefit|Risk|
|---|---|---|
|Immediate patching|Lower security risk|Possible instability|
|Delayed patching|More testing time|Longer exposure window|
|Risk-based patching|Prioritizes critical flaws|Requires good judgment|

### Configuration management

Configuration management keeps systems consistent and secure across time.

#### Why it matters

- prevents drift
    
- keeps environments aligned
    
- makes auditing easier
    
- reduces accidental changes
    

### Configuration drift

Configuration drift happens when a system slowly deviates from its intended secure state.

> [!example] Example  
> One server in a group is updated and hardened, while another server remains unchanged. The second server becomes the weaker target.

### Automation tools

|Tool|Use|
|---|---|
|Ansible|Automates configuration and patch enforcement|
|Puppet|Enforces consistent system settings|
|Microsoft Endpoint Configuration Manager|Manages updates and policy in Windows environments|
|Lynis / OpenSCAP|Auditing and security benchmarking|

---

## Misconfiguration as an Attack Vector

### Definition

Misconfiguration means a system has been set up incorrectly or insecurely.

### Why it is dangerous

- often easier to exploit than software bugs
    
- does not require advanced techniques
    
- can expose sensitive services directly
    
- can bypass intended protections
    

### Common misconfigurations

|Misconfiguration|Example impact|
|---|---|
|Open or unnecessary ports|Attacker can connect to a service|
|Weak permissions|Files can be modified by unauthorized users|
|Default credentials|Immediate unauthorized access|
|Unprotected services|Sensitive data may be exposed|
|Disabled security controls|Reduced defense against attacks|
|Improper access control|Users gain access they should not have|
|Exposed sensitive directories|Confidential files become visible|

### Examples

#### 1) Weak file permissions

> [!example] Example  
> A folder with permissions similar to `chmod 777` allows everyone to read, write, and execute. This can let an attacker modify files, replace executables, or inject malicious content.

#### 2) Default credentials

> [!example] Example  
> A device left with `admin/admin` can be taken over immediately by anyone who knows the default login.

#### 3) Exposed service without authentication

> [!example] Example  
> A database accessible without a password can leak or allow modification of data without any exploit beyond simple connection access.

#### 4) Disabled security controls

> [!example] Example  
> Turning off the firewall for convenience can expose services that were never meant to be public.

### Why misconfiguration happens

|Cause|Description|
|---|---|
|Complexity|Modern systems are difficult to manage|
|Time pressure|Security settings are rushed|
|Poor documentation|Changes are not tracked clearly|
|Default assumptions|People assume secure defaults are enough|
|Lack of auditing|Problems remain hidden|
|Low awareness|Security implications are not understood|

> [!important] Key Insight  
> Many systems are secure by design but insecure in deployment.

---

## Final Takeaways

### Main lessons

|Topic|Main idea|
|---|---|
|Trust models|The OS must know what to trust and what to restrict|
|TCB|Protect the core components that security depends on|
|User/kernel separation|User applications must never control the kernel directly|
|Least privilege|Give only the permissions that are necessary|
|Hardening|Remove unnecessary exposure|
|Patch management|Fix known weaknesses quickly|
|Configuration management|Keep systems consistent over time|
|Misconfiguration|The most common and most dangerous weakness|

### Final conclusion

Security is not a single product or setting. It is a continuous process of enforcing trust boundaries, reducing exposure, applying updates, and keeping configurations correct.

> [!quote] Final thought  
> A well-secured system assumes breaches can happen and is designed to fail safely.

---

## Quick Revision Table

|Concept|One-line meaning|Example|
|---|---|---|
|Trust model|Defines what is trusted and restricted|User apps are untrusted|
|TCB|Core security-critical components|Kernel, authentication|
|User space|Where apps run|Browser|
|Kernel space|Where the OS core runs|Memory and process control|
|Least privilege|Only necessary permissions|Read-only access for a viewer app|
|Privilege escalation|Gaining higher rights|User becomes root|
|Hardening|Reducing exposure|Disabling unused services|
|Patch management|Applying fixes|Installing security updates|
|Configuration drift|Systems diverge from desired settings|One server is updated, another is not|
|Misconfiguration|Insecure setup|Default password left unchanged|

---

## Self-Test Questions

1. Why is the operating system central to security?
    
2. What is the difference between trusted and untrusted components?
    
3. Why is the Trusted Computing Base important?
    
4. What is the difference between user space and kernel space?
    
5. How does least privilege reduce risk?
    
6. What is privilege escalation?
    
7. Why is closing unused ports important?
    
8. Why are unpatched systems dangerous?
    
9. What is configuration drift?
    
10. Why is misconfiguration often more dangerous than a software bug?
    

---

## Exam-Friendly Definition Box

> [!tip] Memorize These
> 
> - **Security is enforced by the OS.**
>     
> - **Least privilege reduces damage.**
>     
> - **Hardening reduces attack surface.**
>     
> - **Patching removes known weaknesses.**
>     
> - **Misconfiguration is a major attack vector.**
>     

---

## Suggested Obsidian Tags

#cybersecurity #os-security #system-security #privilege #hardening #patching #misconfiguration #notes