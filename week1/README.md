# Week 1 — Cyber Threat Intelligence Fundamentals

## Project Topic

**Ransomware Threat Intelligence and IOC Analysis**

### Case Study: LockBit 3.0

---

## 1. Introduction to Cyber Threat Intelligence

Cyber Threat Intelligence (CTI) is the process of collecting, processing, analyzing, and using information about cyber threats.

CTI helps security teams understand:

- who may be attacking an organization;
- what techniques attackers use;
- what indicators can reveal malicious activity;
- how an attack can be detected and investigated.

For this project, CTI is applied to ransomware threats, with LockBit 3.0 used as a case study.

---

## 2. What is Ransomware?

Ransomware is a type of malicious software that prevents victims from accessing their data or systems.

Modern ransomware operations may involve:

1. Initial access to the victim environment.
2. Execution of malicious software.
3. Privilege escalation.
4. Discovery of systems and network resources.
5. Lateral movement.
6. Data exfiltration.
7. Data encryption.
8. Extortion.

Ransomware operators may use a double-extortion model. In this model, attackers can steal sensitive data before encrypting systems and then threaten to publish the stolen information.

---

## 3. LockBit 3.0

LockBit 3.0 is a ransomware variant associated with a Ransomware-as-a-Service (RaaS) model.

According to MITRE ATT&CK, LockBit 3.0 has been used since at least June 2022 and can target Windows and VMware ESXi environments.

The malware has been associated with multiple techniques, including:

- PowerShell;
- Group Policy modification;
- disabling security tools;
- data encryption;
- deleting volume shadow copies;
- network share discovery;
- SMB-based lateral movement;
- process discovery.

Source:

MITRE ATT&CK — LockBit 3.0
https://attack.mitre.org/software/S1202/

---

## 4. Key CTI Terms

### 4.1 Indicator of Compromise (IOC)

An Indicator of Compromise is a piece of technical information that may indicate malicious activity.

Examples include:

- IP addresses;
- domain names;
- file hashes;
- URLs;
- email addresses;
- malicious files;
- suspicious registry entries.

IOCs can be used by security teams to search logs, endpoint systems, network traffic, and security platforms for evidence of compromise.

---

### 4.2 Tactics, Techniques and Procedures (TTPs)

TTPs describe how threat actors conduct their operations.

- **Tactics** describe the attacker's goal.
- **Techniques** describe how the attacker achieves that goal.
- **Procedures** describe the specific implementation used by the attacker.

For example:

**Tactic:** Impact

**Technique:** T1486 — Data Encrypted for Impact

**Procedure:** LockBit 3.0 encrypts targeted data.

---

### 4.3 Threat Actor

A threat actor is an individual, group, or organization that performs malicious cyber activity.

In ransomware operations, different actors may perform different parts of an attack.

---

### 4.4 Ransomware-as-a-Service (RaaS)

Ransomware-as-a-Service is an operational model where ransomware infrastructure or malware is provided to affiliates who conduct attacks.

This allows different participants to specialize in activities such as initial access, deployment, or extortion.

---

### 4.5 Command and Control (C2)

Command and Control refers to communication between malicious software and infrastructure controlled by an attacker.

C2 communication may be used to:

- send commands;
- receive information;
- control compromised systems;
- transfer data.

---

## 5. Types of Ransomware Threats

### File Encryption

Attackers encrypt files and demand payment for recovery.

### System Impact

Attackers may disrupt systems or services to increase the impact of the attack.

### Data Exfiltration

Attackers may steal sensitive information before encryption.

### Double Extortion

Attackers combine data theft with encryption and threaten to publish stolen information.

---

## 6. LockBit 3.0 and MITRE ATT&CK

MITRE ATT&CK provides a knowledge base for describing adversary tactics and techniques.

Examples associated with LockBit 3.0 include:

| Technique ID | Technique | Description |
|---|---|---|
| T1486 | Data Encrypted for Impact | Encrypts targeted data |
| T1059.001 | PowerShell | Uses PowerShell for execution and system changes |
| T1484.001 | Group Policy Modification | Can modify Group Policy |
| T1490 | Inhibit System Recovery | Can delete volume shadow copies |
| T1135 | Network Share Discovery | Can identify network shares |
| T1021.002 | SMB/Windows Admin Shares | Can use SMB for lateral movement |
| T1057 | Process Discovery | Can identify processes |
| T1112 | Modify Registry | Can modify Windows Registry |

These techniques demonstrate how CTI can connect observed technical behavior to a standardized attack framework.

---

## 7. Threat Intelligence Sources

The following sources will be used during this project:

| Source | Purpose |
|---|---|
| MITRE ATT&CK | Analyze attacker techniques and TTPs |
| VirusTotal | Analyze files, hashes, domains and other indicators |
| Shodan | Investigate publicly exposed network services |
| Maltego | Visualize relationships between entities |
| MISP | Store, process and correlate IOCs |
| CISA | Obtain ransomware guidance and threat information |

---

## 8. Project Objective

The objective of this project is to demonstrate a basic Cyber Threat Intelligence workflow for ransomware.

The project will follow three stages:

**Collection → Processing → Analysis**

During Week 1, the project focuses on understanding ransomware, CTI concepts, IOCs, TTPs, and MITRE ATT&CK.

During Week 2, publicly available threat intelligence will be collected using OSINT tools.

During Week 3, collected IOCs will be processed and analyzed using MISP.

---

## 9. Conclusion

Cyber Threat Intelligence provides structured information that helps security teams understand and detect cyber threats.

Ransomware is a useful case study because its operations involve multiple stages and can produce different types of technical indicators.

By using MITRE ATT&CK, OSINT tools, and MISP, this project will demonstrate how raw threat information can be collected and transformed into structured intelligence.

---

## References

1. MITRE ATT&CK — LockBit 3.0
   https://attack.mitre.org/software/S1202/

2. MITRE ATT&CK — Data Encrypted for Impact
   https://attack.mitre.org/techniques/T1486/

3. MITRE ATT&CK — Inhibit System Recovery
   https://attack.mitre.org/techniques/T1490/

4. CISA / MS-ISAC — Ransomware Guide
   https://www.cisa.gov/stopransomware/ransomware-guide
