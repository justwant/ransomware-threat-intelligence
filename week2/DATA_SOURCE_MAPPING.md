# Data Source Mapping

## Purpose

The purpose of this data source mapping is to show how different OSINT and Cyber Threat Intelligence sources contribute to the ransomware investigation.

The project uses three main sources:

- VirusTotal
- Shodan
- Maltego

Each source provides different types of information that can be combined during CTI analysis.

## Data Source Mapping

| Data Source | Data Collected | Main Purpose | CTI Output |
|---|---|---|---|
| VirusTotal | File hashes, malware detections, contacted domains, IP addresses, related files | Analyze suspicious files and identify technical indicators | IOCs such as hashes, domains and IP addresses |
| Shodan | IP addresses, open ports, services, hostnames, organizations, web technologies | Identify publicly exposed infrastructure | Infrastructure information and exposed services |
| Maltego | Domains, DNS names and relationships between entities | Visualize relationships and expand the investigation | Relationship graph and related infrastructure |

## 1. VirusTotal

VirusTotal was used to analyze a suspicious file associated with the ransomware investigation.

The collected information included:

- Malware detection results
- File hash
- Contacted domains
- Contacted IP addresses
- Related files
- Execution parents and children

This information can be used to identify Indicators of Compromise (IOCs).

### Example

VirusTotal showed relationships between the analyzed file and domains, IP addresses and other files.

These indicators can later be used for correlation and further analysis.

## 2. Shodan

Shodan was used to collect information about Internet-exposed infrastructure.

The collected information included:

- Hostnames
- IP address information
- Open TCP ports
- Network organization
- ISP
- ASN
- Web technologies
- Exposed services

For example, the Shodan result showed services such as FTP, DNS, HTTP, HTTPS and MySQL.

This information helps analysts understand what services and technologies are exposed to the Internet.

## 3. Maltego

Maltego was used to visualize relationships between domains and DNS entities.

The investigation started with:

**lockbit.com**

A DNS-related Transform was then used to identify related DNS names.

The graph returned DNS entities such as:

- vpn.lockbit.com
- testing.lockbit.com
- www.mail.lockbit.com
- www.vpn.lockbit.com
- test.lockbit.com
- mail.lockbit.com

Maltego therefore provides a visual representation of relationships that can help expand an investigation.

## Correlation Between Sources

The three sources provide complementary information.

The basic workflow is:

**VirusTotal → Shodan → Maltego**

VirusTotal provides technical indicators such as hashes, domains and IP addresses.

Shodan provides information about Internet-exposed infrastructure and services.

Maltego helps visualize relationships between domains and other entities.

The information collected from these sources can be combined for further CTI analysis.

## CTI Analysis Workflow

The data source mapping can be represented as:

**Collect → Normalize → Correlate → Analyze → Report**

### Collect

Collect technical indicators and infrastructure information from VirusTotal, Shodan and Maltego.

### Normalize

Organize the collected data into consistent categories such as:

- Hash
- Domain
- IP address
- DNS name
- Port
- Service

### Correlate

Compare indicators and identify relationships between files, domains, IP addresses and infrastructure.

### Analyze

Use the relationships and indicators to understand the potential threat infrastructure.

### Report

Document the findings and preserve the relevant evidence for further investigation.

## Conclusion

Different CTI sources provide different types of information.

VirusTotal is useful for malware and IOC analysis.

Shodan is useful for Internet-exposed infrastructure analysis.

Maltego is useful for relationship visualization and investigation expansion.

Combining these sources provides a more structured approach to ransomware-related CTI analysis.
