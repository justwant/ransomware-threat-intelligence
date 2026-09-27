# Week 1 — Cyber Threat Intelligence Fundamentals

## 1. Introduction

This week focuses on the fundamentals of Cyber Threat Intelligence (CTI)
and their application to a ransomware case study.

The main topic of our project is ransomware threat intelligence,
with LockBit used as the main case study.

The purpose of Week 1 is to understand the basic CTI concepts,
terminology, threat categories, and intelligence sources that will
be used during the following weeks.

---

## 2. Week 1 Objectives

According to the Week 1 tasks, the main objectives are:

- Understand the basic concepts of Cyber Threat Intelligence.
- Create a glossary of key CTI terms.
- Classify different types of cyber threats.
- Identify different sources of threat intelligence.
- Understand the role of MITRE ATT&CK in describing attacker behavior.
- Apply the learned CTI concepts to the ransomware case study.

---

## 3. Cyber Threat Intelligence Fundamentals

Cyber Threat Intelligence (CTI) is information about cyber threats
that is collected, processed, and analyzed to provide useful context
for cybersecurity activities and decisions.

CTI helps security teams understand:

- Threat actors
- Their objectives and motivations
- Malware
- Infrastructure
- Indicators of compromise (IOCs)
- Tactics, techniques and procedures (TTPs)
- Vulnerabilities
- Attack behavior

Threat intelligence can later be used for detection, incident response,
threat hunting, and improving security controls.

---

## 4. CTI Concepts

### Indicator of Compromise (IOC)

An IOC is a technical artifact that may indicate that a system or
network has been compromised.

Examples include:

- IP addresses
- Domains
- URLs
- File hashes
- Malicious files

### TTPs

TTPs stands for Tactics, Techniques and Procedures.

They describe how a threat actor behaves during an attack.

- Tactic — the main objective of the attacker.
- Technique — the method used to achieve the objective.
- Procedure — the specific implementation of a technique.

### Threat Actor

A threat actor is a person or group responsible for conducting
malicious cyber activities.

### Malware

Malware is malicious software designed to perform harmful or
unauthorized actions.

### Ransomware

Ransomware is a type of malware that prevents victims from accessing
their data or systems and is commonly associated with ransom demands.

---

## 5. CTI Glossary

The detailed glossary of key CTI terms is provided in:

[CTI Glossary](glossary.md)

The glossary contains definitions of the main concepts used in this
project, including CTI, IOC, TTPs, ransomware, OSINT, MITRE ATT&CK,
threat actors, malware, vulnerabilities, and threat hunting.

---

## 6. Threat Classification and Sources

Cyber threats can be classified into different categories depending
on their purpose, behavior, and impact.

The detailed classification and threat intelligence sources are
provided in:

[Threat Classification and Sources](threat_classification.md)

The classification includes examples such as:

- Ransomware
- Malware
- Phishing
- Credential theft
- Vulnerability exploitation
- DDoS

The section also identifies relevant intelligence sources such as
MITRE ATT&CK, ENISA, CISA, VirusTotal, Shodan, Maltego, security
research reports, and internal security logs.

---

## 7. MITRE ATT&CK

MITRE ATT&CK is a knowledge base that describes adversary tactics
and techniques based on real-world observations.

It provides a common structure for describing attacker behavior.

For this project, MITRE ATT&CK will be used to study ransomware
behavior and map relevant attacker techniques.

Examples relevant to the LockBit case study include:

- Data Encrypted for Impact
- Inhibit System Recovery

---

## 8. Intelligence Sources and Tools

The project uses several intelligence sources and tools.

| Source / Tool | Purpose |
|---|---|
| MITRE ATT&CK | Analyze attacker techniques and TTPs |
| VirusTotal | Analyze files, hashes, domains and other indicators |
| Shodan | Investigate publicly exposed network services |
| Maltego | Visualize relationships between entities |
| MISP | Store, process and correlate IOCs |
| CISA | Obtain ransomware guidance and threat information |
| ENISA | Study cyber threat trends and the threat landscape |

Some of these tools will be used during later weeks.
Week 1 focuses on understanding their role in the overall CTI workflow.

---

## 9. Project Objective

The objective of this project is to demonstrate a basic Cyber Threat
Intelligence workflow for ransomware.

The project will follow three main stages:

**Collection → Processing → Analysis**

During Week 1, the project focuses on understanding ransomware,
CTI concepts, IOCs, TTPs, MITRE ATT&CK, threat classifications,
and intelligence sources.

During Week 2, publicly available threat intelligence will be
collected using OSINT tools.

During Week 3, collected IOCs will be processed and analyzed
using MISP.

---

## 10. CTI Workflow

The overall CTI workflow used in this project can be represented as:

**Collect → Process → Analyze → Share → Apply**

### Collect

Threat information is collected from public sources such as
MITRE ATT&CK, VirusTotal, Shodan, security reports, ENISA,
CISA, and other OSINT sources.

### Process

Collected information is cleaned, normalized, classified,
and converted into structured data such as IOCs and TTPs.

### Analyze

Analysts correlate the collected information and identify
relationships between indicators, threat actors, malware,
and attack techniques.

### Share

Relevant intelligence is documented and shared in a structured
format so that it can be used by security teams.

### Apply

The resulting intelligence can be used for detection,
incident response, threat hunting, and improving security controls.

For this project, the workflow will be applied to ransomware intelligence:

**Ransomware information → IOC collection → IOC processing
→ MITRE ATT&CK mapping → Threat analysis**

---

## 11. Recommended Reading

The recommended reading for Week 1 includes the ENISA Threat Landscape
Report.

ENISA Threat Landscape reports provide information about the current
cyber threat landscape and different categories of cyber threats.

This source will be used to support the understanding and
classification of cyber threats.

---

## 12. Conclusion

Week 1 establishes the theoretical foundation for the project.

The main results of this week are:

1. A glossary of key CTI terms.
2. A classification of different cyber threats.
3. A list of relevant threat intelligence sources.
4. An understanding of IOCs and TTPs.
5. An introduction to MITRE ATT&CK.
6. An application of these concepts to the LockBit ransomware
   case study.

The knowledge obtained in Week 1 will be used in Week 2 to collect
real threat intelligence and in Week 3 to process and analyze
the collected indicators.

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

5. ENISA — Threat Landscape  
   https://www.enisa.europa.eu/topics/cyber-threats
