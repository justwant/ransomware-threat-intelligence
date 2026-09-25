# Week 2 — Data Collection Process

## Project Topic

Ransomware Threat Intelligence and IOC Analysis

### Case Study: LockBit 3.0

---

## 1. Objective

The objective of Week 2 is to collect publicly available Cyber Threat Intelligence related to ransomware.

The collected information will be used for further processing and analysis during Week 3.

The main data collection sources are:

- VirusTotal
- Shodan
- Maltego
- MITRE ATT&CK
- Public cybersecurity reports

---

## 2. Data Collection Methodology

The data collection process follows these steps:

1. Identify the target ransomware.
2. Identify relevant threat intelligence sources.
3. Collect publicly available information.
4. Record the source of each piece of information.
5. Classify the collected information.
6. Prepare the data for processing in Week 3.

The project focuses on passive and publicly available information.

No unauthorized access or active exploitation is performed.

---
## 3. VirusTotal Analysis

A LockBit 3.0 sample was analyzed using VirusTotal.

SHA-256:

80e8defa5377018b093b5b90de0f2957f7062144c83a09a56bba1fe4eda932ce

VirusTotal results:

- 58 of 64 security vendors detected the file as malicious.
- File type: PE executable (EXE).
- File size: 162 KB.
- Popular threat label: ransomware.lockbit/packed2.
- Threat categories: ransomware and trojan.
- Family labels include LockBit.

The result confirms that the analyzed sample is associated with LockBit ransomware.

![VirusTotal analysis](virustotal-lockbit.png)

### Data to Collect

The following types of information may be collected:

- File hashes
- Domains
- IP addresses
- URLs
- Detection information
- Related files
- Threat intelligence relationships

### Source

VirusTotal:

https://www.virustotal.com/

---

## 4. Shodan Analysis

A Shodan search was performed using the keyword "LockBit".

The search returned one publicly indexed host:

- IP address: 20.230.148.134
- Location: United States, Moses Lake
- Operating system: Windows 11
- Service: Remote Desktop Protocol (RDP)
- Certificate Common Name: lockbit-demo
- NetBIOS name: lockbit-demo

The result shows publicly available infrastructure containing LockBit-related identifiers. 
The Shodan result alone does not prove that the IP address belongs to the LockBit ransomware group.

![Shodan search result](shodan-lockbit.png)

### Data to Collect

Potential information includes:

- IP addresses
- Open ports
- Network services
- Service banners
- Host information
- Geographic information

Only publicly available information will be used.

### Source

Shodan:

https://www.shodan.io/

---

## 5. Maltego

Maltego is an OSINT and link-analysis platform that can be used to visualize relationships between entities.

For this project, Maltego will be used to represent relationships between entities such as:

- Domains
- IP addresses
- URLs
- Organizations
- Malware
- Threat actors

The purpose is to understand relationships between collected intelligence rather than to perform unauthorized activity.

---

## 6. Source Mapping

All collected information will be recorded together with its source.

| Source | Data Type | Purpose |
|---|---|---|
| VirusTotal | Hashes, domains, URLs, IPs | IOC investigation |
| Shodan | IPs, ports, services | Infrastructure research |
| Maltego | Entity relationships | Link analysis |
| MITRE ATT&CK | TTPs | Adversary behavior analysis |
| Security Reports | Threat information | Context and validation |

---

## 7. Data Collection Log

| ID | Source | Indicator/Data | Type | Relevance |
|---|---|---|---|---|
| IOC-001 | VirusTotal | `80e8defa5377018b093b5b90de0f2957f7062144c83a09a56bba1fe4eda932ce` | SHA-256 Hash | LockBit-related malware sample |
| IOC-002 | VirusTotal | `ransomware.lockbit/packed2` | Threat Label | LockBit ransomware classification |
| IOC-003 | Shodan | `20.230.148.134` | IP Address | Publicly indexed host |
| IOC-004 | Shodan | RDP / Windows 11 / `lockbit-demo` | Host Information | LockBit-related identifiers |
| IOC-005 | Maltego | `lockbit.com` → IP entity | Relationship | Link analysis |

---

## 8. Evidence

Screenshots will be collected from the tools used during the investigation.

Evidence will include:

- VirusTotal search results
- Shodan search results
- Maltego relationship graph
- Source mapping table

Screenshots will be stored in the project repository.

---

## 9. Data Preparation for Week 3

After collection, the gathered information will be prepared for processing.

The next stage will include:

- IOC normalization;
- IOC classification;
- correlation of indicators;
- importing relevant data into MISP;
- mapping indicators to threat intelligence context.

---

## 10. Conclusion

Week 2 focuses on collecting publicly available Cyber Threat Intelligence from multiple sources.

The collected data will provide the foundation for IOC processing and correlation in Week 3.

The overall workflow is:

**Collect → Validate → Classify → Process → Analyze**
