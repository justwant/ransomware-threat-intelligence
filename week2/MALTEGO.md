# Maltego OSINT Collection

## Objective

The objective of this activity was to use Maltego to collect and visualize publicly available information related to the ransomware threat intelligence investigation.

## Initial Entity

The investigation started with the domain:

**lockbit.com**

A Domain entity was added to the Maltego graph.

## Transform Used

The following Transform was used:

**To DNS Name [SecurityTrails]**

The Transform was used to identify DNS names associated with the selected domain.

## Results

The Maltego graph returned several DNS names connected to the domain, including:

- vpn.lockbit.com
- testing.lockbit.com
- www.mail.lockbit.com
- www.vpn.lockbit.com
- test.lockbit.com
- mail.lockbit.com

These results demonstrate how Maltego can visualize relationships between a domain and related DNS entities.

## CTI Relevance

DNS information can be useful during Cyber Threat Intelligence collection because it can help analysts identify related infrastructure and expand an investigation from an initial domain to additional network entities.

The results can be correlated with information collected from other OSINT sources, such as VirusTotal and Shodan.

## Evidence

![Maltego DNS Graph](screenshots/maltego_dns.png)
