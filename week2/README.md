# Week 2 — Data Collection Process

Week 2 focuses on OSINT data collection using VirusTotal, Shodan, and Maltego.

| Source | Data Collected | Purpose |
|---|---|---|
| VirusTotal | File hashes, malware detections, domains, IP addresses, related files | Malware and IOC analysis |
| Shodan | IP addresses, open ports, services, hostnames, technologies | Infrastructure research |
| Maltego | Domains and DNS relationships | Link analysis |

---

## 7. Data Collection Log

| ID | Source | Indicator/Data | Type | Relevance |
|---|---|---|---|---|
| IOC-001 | VirusTotal | `a736269f5f3a9f2e11dd776e352e1801bc28bb699e47876784b8ef761e0062db` | SHA-256 Hash | File identified as ransomware-related |
| IOC-002 | VirusTotal | `ransomware.lockbit/blackmatter` | Threat Label | LockBit/BlackMatter classification |
| IOC-003 | Shodan | `192.185.176.209` | IP Address | Publicly indexed host |
| IOC-004 | Shodan | Ports 21, 53, 80, 110, 443, 465, 587, 995, 3306 | Open Ports | Shows publicly exposed network services |
| IOC-005 | Maltego | `lockbit.com` | Domain | Starting point for DNS relationship analysis |
| IOC-006 | Maltego | `vpn.lockbit.com`, `test.lockbit.com`, `mail.lockbit.com` | DNS Names | Related DNS entities returned by the Transform |

---

## 8. Evidence

Evidence was collected from the three OSINT tools used during the investigation.

The evidence includes:

- VirusTotal malware analysis screenshots
- Shodan host and service information
- Maltego DNS relationship graph

Screenshots are stored in the project repository.

---

## 9. Data Preparation for Week 3

The collected information will be prepared for further CTI processing.

The next stage will include:

- IOC normalization;
- IOC classification;
- correlation of indicators;
- importing relevant indicators into MISP;
- analysis of relationships between indicators.

---

## 10. Conclusion

Week 2 demonstrated OSINT data collection using VirusTotal, Shodan, and Maltego.

VirusTotal provided malware and IOC information, Shodan provided infrastructure information, and Maltego provided relationships between a domain and related DNS entities.

The collected information will be used as the basis for IOC processing and correlation in Week 3.

**Collect → Validate → Classify → Process → Analyze**
