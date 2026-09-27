# Shodan OSINT Data Collection

## Objective

Shodan was used as an OSINT source to collect information about publicly accessible Internet infrastructure.

The purpose of this activity is to demonstrate how Shodan can provide technical information that can be used during Cyber Threat Intelligence (CTI) investigations.

## Search Query

The following search query was used:

`apache`

## Search Results

The Shodan search returned a large number of Internet-connected hosts associated with Apache web servers.

The search results provided information such as:

- IP addresses
- Hostnames
- Countries and cities
- Organizations
- Autonomous System Numbers (ASN)
- Open network ports
- Web server information
- HTTP and SSL/TLS information

### Search Results

![Shodan Apache Search Results](shodan_apache_results.png)

## Host Analysis

One Shodan result was opened to examine the technical information available for a specific host.

The following information was observed:

- Hostnames: `prodns.com.br`, `srv36.prodns.com.br`
- Country: United States
- City: Atlanta
- Organization: HostGator.com LLC
- ASN: AS19871
- Web server: Apache HTTP Server
- Multiple open ports were listed, including ports 21, 53, 80 and 443.
- Port 21 was identified as an FTP service running Pure-FTPd.

### Host Details

![Shodan Host Details](shodan_host_details.png)

## CTI Relevance

Shodan can be used as an OSINT source to identify publicly exposed Internet services and infrastructure.

This information can help security analysts understand external attack surfaces and identify infrastructure that may require further investigation.

For this project, Shodan is used as one of the OSINT sources in the ransomware-focused Cyber Threat Intelligence workflow.

Shodan results alone do not prove that a particular host is associated with ransomware or LockBit. Additional intelligence sources are required to establish such a relationship.

## Conclusion

The Shodan collection demonstrated how publicly available information about Internet-connected infrastructure can be collected and documented as part of a Cyber Threat Intelligence investigation.
