# Week 7 — Using MITRE CAR

## 1. MITRE Cyber Analytics Repository (CAR)

During Week 7, I studied the **MITRE Cyber Analytics Repository (CAR)** and learned how analytics can be used to detect suspicious activity in a SIEM.

MITRE CAR provides analytic models that can be mapped to **MITRE ATT&CK techniques**.

For this assignment, I selected:

- **CAR Analytic:** CAR-2021-01-001 — Identifying Port Scanning Activity
- **ATT&CK Technique:** T1046 — Network Service Discovery
- **Tactic:** Discovery
- **SIEM:** Elasticsearch and Kibana
- **Environment:** Ubuntu Virtual Machine / ELK

---

## 2. Selected CAR Analytic

The selected analytic is **CAR-2021-01-001 — Identifying Port Scanning Activity**.

The purpose of this analytic is to identify possible port scanning activity by counting the number of unique destination ports contacted by each source IP address.

The detection logic is based on the following principle:

```text
Source IP
    ↓
Count unique destination ports
    ↓
If unique ports > 5

    ↓
Potential Port Scanning Activity
```

The original CAR logic uses the number of distinct destination ports for each source IP and identifies activity when the number exceeds a threshold.

---

## 3. Network Events

For the SIEM implementation, I created network connection events and imported them into the Elasticsearch index:

```text
threat-hunting-lab
```

The events contained the following fields:

```text
event.category
event.action
source.ip
destination.ip
destination.port
network.transport
```

The source IP used in the test was:

```text
10.0.2.15
```


The destination IP was:

```text
10.0.2.20
```

The destination ports used for the simulation were:

```text
21
22
23
25
53
80
443
```

Therefore, the source generated connections to **7 unique destination ports**.

---

## 4. Implementing the CAR Analytic in Elasticsearch

The CAR detection logic was implemented in Elasticsearch using an aggregation query.

The query groups network events by source IP, calculates the number of unique destination ports, and applies a threshold of greater than 5.

```json
POST threat-hunting-lab/_search
{

  "size": 0,
  "query": {
    "term": {
      "event.category": "network"
    }
  },
  "aggs": {
    "scanning_sources": {
      "terms": {
        "field": "source.ip.keyword"
      },
      "aggs": {
        "unique_ports": {
          "cardinality": {
            "field": "destination.port"
          }
        },
        "port_scan_threshold": {
          "bucket_selector": {
            "buckets_path": {
              "pcount": "unique_ports"
            },
            "script": "params.pcount > 5"
          }
        }
      }
    }
  }
}
```

The `cardinality` aggregation calculates the number of unique destination ports.


The `bucket_selector` applies the detection threshold:

```text
pcount > 5
```

This means that a source IP is identified as a potential port scanner when it connects to more than five unique destination ports.

---

## 5. Detection Result

The Elasticsearch query successfully detected the scanning source.

The result was:

| Parameter | Value |
|---|---|
| Source IP | 10.0.2.15 |
| Network events | 7 |
| Unique destination ports | 7 |
| Detection threshold | > 5 |
| Result | Potential Port Scanning Activity |

The source IP `10.0.2.15` contacted seven different destination ports.

Since:

```text
7 > 5
```


the detection condition was satisfied.

### Screenshot — Detection Query

<img width="757" height="622" alt="Снимок экрана 2026-11-01 233852" src="https://github.com/user-attachments/assets/b7fd0d17-fb23-4fa9-a649-a600321fce94" />


---

## 6. Detection Result in Elasticsearch

The Elasticsearch response showed:

```json
"key": "10.0.2.15",
"doc_count": 7,
"unique_ports": {
    "value": 7
}
```

This confirms that the source IP `10.0.2.15` generated seven network events involving seven unique destination ports.

### Screenshot — Detection Result

<img width="865" height="612" alt="Снимок экрана 2026-11-01 233908" src="https://github.com/user-attachments/assets/24a60e4c-6054-41b5-8743-4670e3e41e50" />


---

## 7. Kibana Visualization

A Kibana visualization was created to display the detection result.


The visualization is named:

```text
CAR-2021-01-001 - Port Scanning Detection
```

The visualization uses:

- **Horizontal axis:** `source.ip.keyword`
- **Metric:** Unique count of `destination.port`

The visualization shows:

```text
10.0.2.15 → 7 unique destination ports
```

This provides a visual representation of the CAR analytic result in the SIEM.

### Screenshot — Kibana Visualization

<img width="1183" height="471" alt="Снимок экрана 2026-11-01 233941" src="https://github.com/user-attachments/assets/012f976b-31e4-4b2e-bcb7-e515a557e30e" />


---

## 8. MITRE ATT&CK Mapping

The CAR analytic was mapped to the following MITRE ATT&CK technique:

- **Tactic:** Discovery
- **Technique:** T1046 — Network Service Discovery

- **CAR Analytic:** CAR-2021-01-001 — Identifying Port Scanning Activity

The relationship can be represented as:

```text
Network Connection Events
          ↓
     Source IP
          ↓
Unique Destination Ports
          ↓
      > 5 Ports
          ↓
CAR-2021-01-001
          ↓
T1046 — Network Service Discovery
          ↓
       Discovery
```

---

## 9. Conclusion

During Week 7, I studied the MITRE Cyber Analytics Repository (CAR) and selected **CAR-2021-01-001 — Identifying Port Scanning Activity**.

The analytic was implemented in the ELK stack using Elasticsearch and Kibana.

The detection logic counted unique destination ports for each source IP and applied a threshold of more than five ports.

During the test, source IP `10.0.2.15` contacted seven unique destination ports. Since 7 > 5, the activity was detected as potential port scanning activity.


The analytic was mapped to **T1046 — Network Service Discovery** under the **Discovery** tactic.

This exercise demonstrated how a MITRE CAR analytic can be implemented in a SIEM to detect suspicious network activity.
