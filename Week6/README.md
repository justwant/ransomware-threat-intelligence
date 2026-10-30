# Week 6 — MITRE ATT&CK Framework

## 1. MITRE ATT&CK Framework

During Week 6, I studied the MITRE ATT&CK Framework and focused on the technique **T1046 — Network Service Scanning**.

### Selected Technique

| Field | Value |
|---|---|
| **Tactic** | Discovery |
| **Technique** | T1046 — Network Service Scanning |
| **Tool** | Nmap |
| **Environment** | Ubuntu Virtual Machine |
| **Target** | `127.0.0.1` |

**T1046 — Network Service Scanning** is a technique used to identify open ports and network services on a target system.

---

## 2. Network Service Scanning Simulation

The scanning activity was performed in a controlled laboratory environment using Nmap.

### Command Used

```bash
nmap -sT -p 1-1000 127.0.0.1
```

### Result

```text
Not shown: 999 closed tcp ports (conn-refused)

PORT    STATE SERVICE
631/tcp open  ipp
```

The scan checked 1000 TCP ports:

- 999 ports were closed.
- `631/tcp` was open.
- The detected service was **IPP (Internet Printing Protocol)**.

This demonstrates how Network Service Scanning can be used to identify available network services on a host.

---

## 3. Traffic Analysis with tcpdump

To observe the network traffic generated during the scan, I used `tcpdump`.

### Command Used

```bash
sudo tcpdump -i any -nn 'tcp'
```

- The `-i any` option captures traffic from all available network interfaces.
- The `-nn` option prevents hostname and service-name resolution.

During the Nmap scan, tcpdump captured TCP connection attempts to different ports.

### Example

```text
127.0.0.1.xxxxx > 127.0.0.1.80: Flags [S]
127.0.0.1.80 > 127.0.0.1.xxxxx: Flags [R.]
```

- `[S]` represents a TCP SYN packet used to initiate a connection.
- `[R.]` represents a TCP reset, indicating that the destination port is closed.

The tcpdump capture provided network-level evidence of the scanning activity.

---

## 4. MITRE ATT&CK Mapping

The activity was mapped to:

- **Tactic:** Discovery
- **Technique:** T1046 — Network Service Scanning

### Attack Flow

```text
Nmap
  ↓
TCP Port Scanning
  ↓
Connection Attempts
  ↓
Port 631 Discovered
  ↓
T1046 — Network Service Scanning
  ↓
Discovery
```

---

## 5. Evidence

### Nmap Scan

The Nmap scan demonstrated that 1000 TCP ports were checked and port 631 was identified as an open service.

**Screenshot:**

<img width="845" height="227" alt="Снимок экрана 2026-10-31 010139" src="https://github.com/user-attachments/assets/7e2da211-350e-4977-b88d-f569ebeeade7" />


### tcpdump Capture

The tcpdump capture demonstrated TCP connection attempts to different ports during the scanning activity.

**Screenshot:**

![Uploading Снимок экрана 2026-10-31 010006.png…]()


---

## 6. MITRE CAR — SIEM Implementation

The second part of the assignment focuses on the **MITRE Cyber Analytics Repository (CAR)**.

The objective is to select an analytic from MITRE CAR, implement its detection logic in the ELK stack using Elasticsearch and Kibana, and map the analytic to the corresponding MITRE ATT&CK technique.

**Status:** 🚧 In progress.

---

## 7. Conclusion

During Week 6, I studied the MITRE ATT&CK Framework and simulated **T1046 — Network Service Scanning** in an Ubuntu virtual machine.

Nmap was used to scan TCP ports from 1 to 1000. The scan identified `631/tcp` as an open IPP service.

Tcpdump was used to observe the TCP connection attempts generated during the scanning process.

The activity was mapped to the **Discovery** tactic and the **T1046 — Network Service Scanning** technique.

**Next step:** implement a MITRE CAR analytic in Elasticsearch and Kibana.
