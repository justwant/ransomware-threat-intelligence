# Threat Classification and Sources

## Introduction

Cyber threats can be classified into different categories based on
their purpose, behavior, and potential impact on an organization.

For this project, the classification focuses on common cyber threats
that are relevant to Cyber Threat Intelligence and ransomware research.

---

## 1. Ransomware

**Description:**  
Ransomware is a type of malware that prevents victims from accessing
their data or systems and is commonly used to demand a ransom.

**Examples of intelligence sources:**
- MITRE ATT&CK
- ENISA Threat Landscape
- CISA security guidance
- VirusTotal
- Security research reports

**Relevant CTI data:**
- Malware hashes
- IP addresses
- Domains
- URLs
- Attack techniques
- Threat actor information

**Project relevance:**  
Ransomware is the main threat category investigated in our project,
with LockBit used as the case study.

---

## 2. Malware

**Description:**  
Malware is malicious software designed to perform unauthorized or
harmful actions on a computer system or network.

**Examples of intelligence sources:**
- VirusTotal
- Malware analysis reports
- MITRE ATT&CK
- Security research organizations
- Threat intelligence feeds

**Relevant CTI data:**
- File hashes
- Malware samples
- File names
- Domains
- IP addresses
- Behavioral information

---

## 3. Phishing

**Description:**  
Phishing is a social engineering technique in which attackers use
fraudulent messages or websites to deceive victims.

**Examples of intelligence sources:**
- Security reports
- Email security systems
- Threat intelligence feeds
- OSINT sources

**Relevant CTI data:**
- Malicious URLs
- Domains
- Email addresses
- IP addresses
- Message indicators

---

## 4. Credential Theft

**Description:**  
Credential theft involves obtaining usernames, passwords, tokens,
or other authentication information without authorization.

**Examples of intelligence sources:**
- Security incident reports
- Authentication logs
- Threat intelligence feeds
- MITRE ATT&CK

**Relevant CTI data:**
- Suspicious login activity
- Compromised accounts
- Malicious tools
- IP addresses
- Attack techniques

---

## 5. Exploitation of Vulnerabilities

**Description:**  
Attackers can exploit weaknesses in software, operating systems,
applications, or network services to gain unauthorized access or
perform malicious actions.

**Examples of intelligence sources:**
- MITRE ATT&CK
- CVE databases
- Vendor security advisories
- CISA
- Security research reports

**Relevant CTI data:**
- CVE identifiers
- Vulnerable software versions
- Exploit information
- IP addresses
- Attack techniques

---

## 6. DDoS

**Description:**  
A Distributed Denial-of-Service (DDoS) attack attempts to make a
service or system unavailable by generating a large amount of traffic
or requests.

**Examples of intelligence sources:**
- Network monitoring systems
- Security reports
- Threat intelligence feeds
- Internet infrastructure data

**Relevant CTI data:**
- Source IP addresses
- Network traffic
- Target information
- Attack patterns

---

## Threat Sources

Threat intelligence can come from different types of sources.

| Source | Type of information |
|---|---|
| **MITRE ATT&CK** | Adversary tactics and techniques |
| **ENISA Threat Landscape** | Information about major cyber threat trends and threat categories |
| **CISA** | Security guidance, alerts, and information about vulnerabilities and threats |
| **VirusTotal** | Malware analysis, file hashes, URLs, domains, and detection results |
| **Shodan** | Information about internet-connected hosts, services, ports, and infrastructure |
| **Maltego** | Relationships between entities such as domains, IP addresses, and infrastructure |
| **Security Research Reports** | Malware analysis, threat actor activity, campaigns, and technical indicators |
| **Internal Security Logs** | Authentication, network, endpoint, and other activity observed inside an organization |

---

## Classification Summary

| Threat | Main purpose / impact | Example sources |
|---|---|---|
| Ransomware | Data encryption, disruption, and extortion | MITRE ATT&CK, ENISA, CISA, VirusTotal |
| Malware | Unauthorized or harmful activity | VirusTotal, MITRE ATT&CK, research reports |
| Phishing | Deception and information theft | Security reports, OSINT, threat feeds |
| Credential Theft | Obtaining authentication information | Logs, MITRE ATT&CK, threat feeds |
| Vulnerability Exploitation | Unauthorized access or execution | CVE databases, CISA, MITRE ATT&CK |
| DDoS | Service disruption | Network monitoring, security reports |

---

## Application to the LockBit Case Study

Our project focuses on ransomware, specifically LockBit.

LockBit is therefore classified primarily as a ransomware threat.
The investigation can use different CTI sources to collect information
about malware, infrastructure, indicators, and attacker behavior.

The information collected during later project stages can include:

- IP addresses
- Domains
- URLs
- File hashes
- Malware information
- Threat actor information
- Tactics and techniques

These indicators can later be processed and analyzed as part of the
Week 2 and Week 3 activities.

---

## Conclusion

Different cyber threats require different types of intelligence
sources. Using multiple sources allows analysts to collect technical
indicators, understand attacker behavior, and obtain additional
context about a threat.

For this project, the main focus is ransomware intelligence and the
LockBit case study.
