# Week 4 — Cyber Kill Chain Analysis: LockBit Ransomware

## 1. Introduction

This week focuses on analyzing a real-world cyberattack using the Cyber Kill Chain model and mapping each stage to corresponding MITRE ATT&CK techniques.

The case study for this analysis is LockBit ransomware.

The Cyber Kill Chain provides a high-level model of how a cyberattack progresses through different stages. MITRE ATT&CK provides a more detailed description of the tactics and techniques used by attackers.

The seven stages of the Cyber Kill Chain are:

1. Reconnaissance
2. Weaponization
3. Delivery
4. Exploitation
5. Installation
6. Command and Control
7. Actions on Objectives

---

## 2. LockBit Ransomware

LockBit is a ransomware family that has been used in real-world cyberattacks.

LockBit operates using a Ransomware-as-a-Service (RaaS) model, where different affiliates may use different techniques to gain access to victim environments.

The attack can include gaining initial access, executing malicious code, establishing persistence, moving through the network, disabling security controls, and encrypting data.

This analysis uses documented LockBit behavior to demonstrate how a ransomware attack can be mapped to the Cyber Kill Chain and MITRE ATT&CK.

---

## 3. Cyber Kill Chain and MITRE ATT&CK

The Cyber Kill Chain is used to describe the overall progression of a cyberattack.

MITRE ATT&CK is used to identify specific attacker techniques associated with different stages of the attack.

In this project:

- Cyber Kill Chain shows the **stage of the attack**.
- MITRE ATT&CK shows the **technique used by the attacker**.

Using both frameworks allows the attack to be analyzed at two levels: the overall attack lifecycle and the specific technical actions performed by the attacker.

---

## 4. Attack Flow

The LockBit attack can be represented using the following Cyber Kill Chain sequence:

- Reconnaissance
- Weaponization
- Delivery
- Exploitation
- Installation
- Command and Control
- Actions on Objectives

---

## 5. Stage 1 — Reconnaissance

Reconnaissance is the first stage of the Cyber Kill Chain.

During this stage, the attacker collects information about the target environment. The goal is to identify potential systems, services, vulnerabilities, and possible entry points.

For a LockBit attack, network and service discovery can help attackers understand the target environment and identify systems that may be useful for further operations.

### MITRE ATT&CK Mapping

**T1046 — Network Service Discovery**

This technique is used to identify network services and systems available in the target environment.

The information collected during this stage can help the attacker decide how to proceed with the attack.


### Defensive Controls

Organizations can reduce the risk of reconnaissance by:

- Monitoring unusual network scanning activity
- Restricting unnecessary network services
- Using firewalls
- Segmenting internal networks
- Monitoring publicly exposed systems
- Reviewing the organization's external attack surface

### Summary

The Reconnaissance stage helps the attacker understand the target environment before continuing to the next stages of the attack.

**Cyber Kill Chain:** Reconnaissance

**MITRE ATT&CK:** T1046 — Network Service Discovery

---

## 6. Stage 2 — Weaponization

Weaponization is the second stage of the Cyber Kill Chain.

During this stage, the attacker prepares the malicious payload that will be used against the target.

In the case of LockBit, the ransomware payload can use techniques that make the malware more difficult to analyze and detect.

### MITRE ATT&CK Mapping

**T1027.002 — Software Packing**

Software packing can be used to modify the structure of a malicious program and make analysis more difficult.

**T1140 — Deobfuscate/Decode Files or Information**

LockBit can decrypt or decode parts of its payload during execution.

These techniques can help the attacker hide the actual functionality of the ransomware until it is executed on the victim's system.

### Defensive Controls

Organizations can detect or analyze suspicious payloads using:

- Endpoint Detection and Response (EDR)
- Antivirus and anti-malware software
- Malware sandboxing
- Static malware analysis
- Dynamic malware analysis
- Application control

### Summary

During the Weaponization stage, the attacker prepares the malicious ransomware payload and can use obfuscation or packing techniques to make detection and analysis more difficult.

**Cyber Kill Chain:** Weaponization

**MITRE ATT&CK:** T1027.002 — Software Packing; T1140 — Deobfuscate/Decode Files or Information

---

## 7. Stage 3 — Delivery

Delivery is the third stage of the Cyber Kill Chain.

During this stage, the attacker attempts to deliver the malicious content or gain initial access to the target environment.

According to documented LockBit activity, several techniques can be used to obtain initial access.

### MITRE ATT&CK Mapping

**T1566 — Phishing**

Attackers can use phishing to deliver malicious content or obtain user credentials.

**T1133 — External Remote Services**

Attackers can use externally accessible remote services to gain access to the target environment.

**T1190 — Exploit Public-Facing Application**

Attackers can exploit vulnerable applications that are exposed to the Internet.

**T1078 — Valid Accounts**

Attackers can use compromised legitimate accounts to gain access to systems.

The exact delivery method can vary depending on the LockBit affiliate and the target environment.

### Defensive Controls

Organizations can reduce the risk of initial access by using:

- Multi-factor authentication (MFA)
- Email security
- Phishing protection
- Secure remote access
- Vulnerability management
- Strong password policies
- Monitoring of external remote services

### Summary

During the Delivery stage, the attacker attempts to gain initial access to the victim's environment using methods such as phishing, external remote services, exploitation of public-facing applications, or compromised accounts.

**Cyber Kill Chain:** Delivery

**MITRE ATT&CK:** T1566 — Phishing; T1133 — External Remote Services; T1190 — Exploit Public-Facing Application; T1078 — Valid Accounts

---

## 8. Stage 4 — Exploitation

Exploitation is the fourth stage of the Cyber Kill Chain.

During this stage, the attacker exploits the available access or vulnerabilities and executes commands or malicious payloads on the victim's systems.

For LockBit, attackers can use command execution and service execution techniques to run malicious activity on compromised systems.

### MITRE ATT&CK Mapping

**T1059.003 — Windows Command Shell**

Attackers can use the Windows Command Shell to execute commands on a compromised system.

**T1569.002 — System Services: Service Execution**

LockBit has been documented using service execution techniques such as PsExec to execute commands or payloads on compromised systems.

These techniques allow the attacker to execute malicious operations after gaining access to the target environment.

### Defensive Controls

Organizations can reduce the risk of exploitation by:

- Monitoring command-line activity
- Monitoring suspicious process execution
- Monitoring the creation of new services
- Restricting administrative privileges
- Using endpoint detection and response (EDR)
- Monitoring tools such as PsExec
- Applying security patches and updates

### Summary

During the Exploitation stage, the attacker executes commands or malicious payloads on compromised systems. LockBit can use Windows command execution and service execution to perform these activities.

**Cyber Kill Chain:** Exploitation

**MITRE ATT&CK:** T1059.003 — Windows Command Shell; T1569.002 — System Services: Service Execution

---

## 9. Stage 5 — Installation

Installation is the fifth stage of the Cyber Kill Chain.

During this stage, the attacker attempts to establish persistence, maintain access, and prepare the compromised system for further activity.

In a LockBit attack, attackers can use Windows services, registry modifications, and other persistence mechanisms. They may also attempt to weaken security controls.

### MITRE ATT&CK Mapping

**T1543.003 — Windows Service**

Attackers can create or modify Windows services to execute malicious code or maintain persistence.

**T1547.004 — Winlogon Helper DLL**

This technique can be used to achieve persistence through the Windows logon process.

**T1562.001 — Impair Defenses**

Attackers may attempt to disable or weaken security controls on the compromised system.

**T1112 — Modify Registry**

LockBit can modify Windows Registry settings to change system or security configurations.

### Defensive Controls

Organizations can detect and prevent installation and persistence by:

- Monitoring the creation of new Windows services
- Monitoring Registry modifications
- Protecting security software from unauthorized changes
- Using Endpoint Detection and Response (EDR)
- Applying the principle of least privilege
- Monitoring suspicious persistence mechanisms
- Restricting administrative access

### Summary

During the Installation stage, the attacker attempts to maintain access and prepare the compromised system for further operations. LockBit can use Windows services, Registry modifications, and techniques that weaken security controls.

**Cyber Kill Chain:** Installation

**MITRE ATT&CK:** T1543.003 — Windows Service; T1547.004 — Winlogon Helper DLL; T1562.001 — Impair Defenses; T1112 — Modify Registry

---

## 10. Stage 6 — Command and Control

Command and Control (C2) is the sixth stage of the Cyber Kill Chain.

During this stage, the compromised system communicates with attacker-controlled infrastructure.

The communication channel can be used to exchange information or commands between the compromised system and the attacker's infrastructure.

### MITRE ATT&CK Mapping

**T1071.001 — Application Layer Protocol: Web Protocols**

LockBit can use HTTP-based communication to communicate with attacker-controlled infrastructure.

**T1573.001 — Encrypted Channel: Symmetric Cryptography**

Encryption can be used to protect communication between the compromised system and the attacker's infrastructure.

Using web protocols and encrypted communication can make malicious traffic more difficult to detect.

### Defensive Controls

Organizations can detect suspicious Command and Control activity by using:

- Network traffic monitoring
- DNS monitoring
- Firewall rules
- Network Detection and Response (NDR)
- Endpoint Detection and Response (EDR)
- Monitoring unusual outbound connections
- Blocking known malicious infrastructure

### Summary

During the Command and Control stage, compromised systems communicate with attacker-controlled infrastructure. LockBit can use web protocols and encrypted channels for this communication.

**Cyber Kill Chain:** Command and Control

**MITRE ATT&CK:** T1071.001 — Web Protocols; T1573.001 — Encrypted Channel

---

## 11. Stage 7 — Actions on Objectives

Actions on Objectives is the final stage of the Cyber Kill Chain.

During this stage, the attacker performs actions that achieve the main objective of the attack.

For LockBit, the main objective is to disrupt the victim's environment and encrypt valuable data. Attackers can also move through the network and disable recovery mechanisms before encryption.

### MITRE ATT&CK Mapping

**T1135 — Network Share Discovery**

Attackers can identify available network shares in the compromised environment.

**T1021.002 — SMB/Windows Admin Shares**

Attackers can use SMB and Windows administrative shares for lateral movement between systems.

**T1490 — Inhibit System Recovery**

LockBit can delete or disable recovery mechanisms such as Volume Shadow Copies. This makes it more difficult for the victim to recover encrypted data.

**T1486 — Data Encrypted for Impact**

LockBit encrypts files on compromised systems to prevent the victim from accessing the data.

Data encryption is one of the main objectives of a ransomware attack.

### Defensive Controls

Organizations can reduce the impact of ransomware by using:

- Offline backups
- Immutable backups
- Network segmentation
- Regular backup testing
- File integrity monitoring
- Endpoint protection
- Recovery procedures
- Least privilege
- Monitoring of SMB and administrative shares

### Summary

During the Actions on Objectives stage, LockBit performs the final malicious actions, including network discovery, lateral movement, disabling recovery mechanisms, and data encryption.

**Cyber Kill Chain:** Actions on Objectives

**MITRE ATT&CK:** T1135 — Network Share Discovery; T1021.002 — SMB/Windows Admin Shares; T1490 — Inhibit System Recovery; T1486 — Data Encrypted for Impact

---

## 12. Complete LockBit Attack Chain

The LockBit attack can be summarized as a sequence of seven Cyber Kill Chain stages.

### Attack Sequence

**1. Reconnaissance**

The attacker identifies target systems, network services, and possible entry points.

↓

**2. Weaponization**

The attacker prepares the ransomware payload and can use packing or obfuscation techniques.

↓

**3. Delivery**

The attacker gains initial access through methods such as phishing, external remote services, exploitation of public-facing applications, or valid accounts.

↓

**4. Exploitation**

The attacker executes commands or malicious payloads on compromised systems.

↓

**5. Installation**

The attacker establishes persistence and may disable or modify security controls.

↓

**6. Command and Control**

Compromised systems communicate with attacker-controlled infrastructure using web protocols or encrypted channels.

↓

**7. Actions on Objectives**

The attacker moves through the network, inhibits recovery mechanisms, and encrypts data.

### Overall Attack Flow

Reconnaissance
        ↓
Identify target systems and services
        ↓
Weaponization
        ↓
Prepare ransomware payload
        ↓
Delivery
        ↓
Gain initial access
        ↓
Exploitation
        ↓
Execute malicious commands
        ↓
Installation
        ↓
Establish persistence and impair defenses
        ↓
Command and Control
        ↓
Communicate with attacker infrastructure
        ↓
Actions on Objectives
        ↓
Lateral movement
        ↓
Inhibit system recovery
        ↓
Encrypt data

---

## 13. Cyber Kill Chain vs MITRE ATT&CK

The Cyber Kill Chain and MITRE ATT&CK provide different levels of analysis of a cyberattack.

### Cyber Kill Chain

The Cyber Kill Chain describes the overall sequence of an attack.

It helps answer the question:

> At what stage of the attack is the adversary?

The seven stages provide a high-level view of how the attack progresses from reconnaissance to the final objective.

### MITRE ATT&CK

MITRE ATT&CK provides a more detailed description of attacker behavior.

It helps answer the question:

> How does the adversary perform a specific action?

For example, the final stage of the Cyber Kill Chain can include several MITRE ATT&CK techniques:

- **T1490 — Inhibit System Recovery**
- **T1486 — Data Encrypted for Impact**
- **T1021.002 — SMB/Windows Admin Shares**
- **T1135 — Network Share Discovery**

Therefore, the Cyber Kill Chain provides the overall attack structure, while MITRE ATT&CK provides detailed technical information about the techniques used by the attacker.

### Combined Analysis

The combination of both frameworks makes it possible to understand:

- The overall progression of the attack
- The techniques used by the attacker
- Possible detection points
- Appropriate defensive controls

This approach provides a structured way to analyze the LockBit ransomware attack.

---

## 14. Defensive Strategy

The Cyber Kill Chain can also be used to identify defensive opportunities at different stages of an attack.

Security controls should be applied throughout the attack lifecycle rather than only after ransomware starts encrypting files.

| Cyber Kill Chain Stage | Example Defensive Control |
|---|---|
| Reconnaissance | Network monitoring and attack surface management |
| Weaponization | Malware analysis and Endpoint Detection and Response (EDR) |
| Delivery | Email security, phishing protection, and Multi-Factor Authentication (MFA) |
| Exploitation | Vulnerability management, patching, and endpoint monitoring |
| Installation | Monitoring services, Registry changes, and persistence mechanisms |
| Command and Control | Network traffic monitoring, DNS monitoring, and firewall controls |
| Actions on Objectives | Offline backups, immutable backups, network segmentation, and recovery procedures |

### Early Detection

The earlier an organization detects malicious activity, the greater the chance of preventing the attacker from reaching the final stage.

For example:

- Suspicious scanning can be detected during Reconnaissance.
- Malicious files can be detected during Delivery.
- Suspicious command execution can be detected during Exploitation.
- Persistence mechanisms can be detected during Installation.
- Unusual outbound connections can be detected during Command and Control.
- File encryption and recovery modification can be detected during Actions on Objectives.

### Summary

Effective defense requires multiple security controls across the entire attack lifecycle.

Organizations should combine network monitoring, endpoint protection, access control, vulnerability management, network segmentation, and reliable backups to reduce the impact of ransomware attacks.

---

## 15. Conclusion

The LockBit ransomware case demonstrates how the Cyber Kill Chain can be used to analyze the different stages of a real-world cyberattack.

The attack can be described through seven stages:

**Reconnaissance → Weaponization → Delivery → Exploitation → Installation → Command and Control → Actions on Objectives**

Each stage can be associated with specific MITRE ATT&CK techniques.

The analysis shows that LockBit attackers can use techniques for:

- Network and service discovery
- Initial access
- Command execution
- Persistence
- Defense evasion
- Command and Control
- Lateral movement
- Inhibiting system recovery
- Data encryption

The most important techniques during the final stage include:

- **T1490 — Inhibit System Recovery**
- **T1486 — Data Encrypted for Impact**
- **T1021.002 — SMB/Windows Admin Shares**
- **T1135 — Network Share Discovery**

Using the Cyber Kill Chain together with MITRE ATT&CK provides both a high-level view of the attack and a detailed view of the techniques used by the adversary.

This analysis demonstrates how understanding attacker behavior can help organizations detect ransomware activity earlier and apply appropriate defensive controls throughout the attack lifecycle.

---

## 16. References

1. Lockheed Martin — Cyber Kill Chain  
   https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html

2. Lockheed Martin — Intelligence-Driven Computer Network Defense  
   https://www.lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf

3. MITRE ATT&CK — LockBit 3.0  
   https://attack.mitre.org/software/S1202/

4. CISA — #StopRansomware: LockBit 3.0  
   https://www.cisa.gov/news-events/cybersecurity-advisories/aa23-165a

5. MITRE ATT&CK — Network Service Discovery (T1046)  
   https://attack.mitre.org/techniques/T1046/

6. MITRE ATT&CK — Software Packing (T1027.002)  
   https://attack.mitre.org/techniques/T1027/002/

7. MITRE ATT&CK — Deobfuscate/Decode Files or Information (T1140)  
   https://attack.mitre.org/techniques/T1140/

8. MITRE ATT&CK — Data Encrypted for Impact (T1486)  
   https://attack.mitre.org/techniques/T1486/

9. MITRE ATT&CK — Inhibit System Recovery (T1490)  
   https://attack.mitre.org/techniques/T1490/
