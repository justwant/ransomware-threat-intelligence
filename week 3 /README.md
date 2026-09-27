# Week 3 — LockBit IOC Analysis

## Objective

The objective of Week 3 was to analyze the LockBit ransomware Indicators of Compromise (IOCs) collected during the previous week and organize them in MISP for further threat intelligence analysis.

The main tasks were:
- Create a MISP event for LockBit IOC analysis.
- Add the collected IOCs to MISP.
- Organize the indicators by category and type.
- Use MISP filtering and correlation features.
- Analyze relationships between the LockBit events.

---

## 1. MISP Event Creation

A new MISP event was created with the name:

**Week 3 - LockBit IOC Analysis**

The event was configured with a Medium threat level and was used to store the collected LockBit-related indicators.

![MISP Event](Screenshots/01_MISP_Event.png)

---

## 2. IOC Collection and Enrichment

The following indicators were added to the MISP event:

| IOC Type | IOC |
|---|---|
| Hostname | mail.lockbit.com |
| Hostname | test.lockbit.com |
| Hostname | vpn.lockbit.com |
| Domain | lockbit.com |
| IP Address | 192.185.176.209 |
| SHA-256 | Collected file hash |

The indicators were added using appropriate MISP categories and types. Additional comments were used to record the source or context of the indicators.

![IOC Attributes](Screenshots/02_LockBit_IOCs.png)

---

## 3. IOC Filtering

MISP filtering was used to search for specific LockBit-related indicators.

For example, searching for `lockbit.com` displayed the related domain and hostname indicators stored in the event.

This demonstrated how MISP can be used to quickly locate specific indicators inside a larger collection of threat intelligence data.

![IOC Filtering](Screenshots/03_Filtered_IOCs.png)

---

## 4. Event Correlation

The MISP Event Graph was used to examine relationships between the created events.

The graph shows the connection between:

**Week 3 - LockBit IOC Analysis**

and

**LockBit Related Infrastructure**

The relationship was established through the `lockbit.com` attribute.

![Event Correlation Graph](Screenshots/04_Correlation_Graph.png)

---

## 5. Results

During Week 3, I successfully:

- Created a MISP event for LockBit IOC analysis.
- Added 6 IOC attributes.
- Added hostnames, a domain, an IP address, and a SHA-256 hash.
- Used MISP filtering to search for specific indicators.
- Created a relationship between related LockBit events.
- Visualized the relationship using the MISP Event Graph.

---

## Conclusion

Week 3 focused on organizing and analyzing the IOC data collected during the previous OSINT activities.

MISP was used to centralize the indicators, add contextual information, search through the collected data, and visualize relationships between related events.

This completed the IOC analysis stage of the project and prepared the collected threat intelligence for further analysis.
