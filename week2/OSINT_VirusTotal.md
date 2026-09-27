# Week 2 — OSINT Data Collection: VirusTotal

## 1. Objective

The objective of this task is to collect publicly available threat intelligence related to ransomware using VirusTotal.

VirusTotal was used to investigate a suspicious file and collect technical indicators such as:

- File hash
- Malware classification
- Security vendor detections
- Contacted domains
- Contacted IP addresses
- Related files
- Execution parents
- File relationships

The collected information can later be processed and analyzed in MISP.

---

## 2. Investigated Sample

The investigated file was:

**File name:** builder.exe

**SHA-256:**

`a736269f5f3a9f2e11dd776e352e1801bc28bb699e47876784b8ef761e0062db`

VirusTotal showed:

**56 / 60 security vendors flagged this file as malicious.**

The VirusTotal page also showed the following threat information:

- Threat category: ransomware
- Threat category: trojan
- Popular threat label: ransomware.lockbit/blackmatter
- Family labels: lockbit, blackmatter, zeroaccess

This indicates that the sample is associated with ransomware-related activity according to the VirusTotal classification and vendor detections.

---

## 3. Security Vendor Detections

VirusTotal showed multiple antivirus detections for the sample.

Examples included:

- Trojan/Win.FS.C5242625
- RansomWare:Win/Lockbit.x1glab
- Trojan.Ransom.LockBit
- Ransom:Win32/BlackMatter
- Win.Ransomware.LockBit

The high number of detections provides strong evidence that the file is considered malicious by multiple security vendors.

---

## 4. Contacted Domains

VirusTotal identified several domains contacted by the sample.

Examples:

- google.com
- microsoft.com
- time.windows.com
- sectigo.com
- crt.sectigo.com
- query.prod.cms.rt.microsoft.com

The contacted-domain information can be used as part of behavioral analysis.

Important: a contacted domain is not automatically malicious. Some domains may belong to legitimate services such as Microsoft, Google, or certificate infrastructure.

---

## 5. Contacted IP Addresses

VirusTotal identified multiple contacted IP addresses.

Examples:

- 104.112.185.183
- 104.86.182.43
- 108.177.9.100
- 108.177.9.101
- 108.177.9.102
- 108.177.9.113
- 108.177.9.138
- 108.177.9.139
- 151.101.22.172
- 152.195.19.97

These IP addresses are technical indicators extracted from the sample's observed behavior.

They can be investigated further during the analysis stage.

---

## 6. Related Files

VirusTotal also showed related files and execution parents.

Examples of related files included:

- LockBit-main.zip
- LockBit-Black-Builder-main.zip
- LockBit30.7z
- Lockbit3.0.rar
- lb.exe
- redirect.pdf.exe.dll

These relationships provide additional information about files associated with the investigated sample.

---

## 7. Collected IOCs

The following types of indicators were collected:

| IOC Type | Example |
|---|---|
| SHA-256 | a736269f5f3a9f2e11dd776e352e1801bc28bb699e47876784b8ef761e0062db |
| Domain | google.com |
| Domain | microsoft.com |
| Domain | sectigo.com |
| IP address | 104.112.185.183 |
| IP address | 104.86.182.43 |
| File name | builder.exe |
| Related file | LockBit-main.zip |
| Related file | LockBit30.7z |

---

## 8. Initial Findings

The VirusTotal investigation produced several types of threat intelligence.

The main findings were:

1. The investigated file was detected as malicious by 56 of 60 security vendors.
2. VirusTotal associated the sample with ransomware-related classifications.
3. The sample was associated with LockBit/BlackMatter labels.
4. Multiple contacted domains and IP addresses were identified.
5. Several related files were identified.
6. These indicators can be used for further CTI processing and analysis.

The collected information will be used in the next stages of the project.

---

## 9. Evidence

The following screenshots document the VirusTotal investigation:

- VirusTotal detection results
- Threat classification
- Contacted domains
- Contacted IP addresses
- Related files and execution parents

---

## 10. Next Step

The collected indicators will be combined with information from other OSINT sources such as Shodan and Maltego.

The next stage will be to create a data source mapping and prepare the collected intelligence for further analysis.
