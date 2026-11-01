# Assignment 8 — Creating a Plan to Emulate an Attacker's Action

## 1. Objective

The objective of this assignment is to develop a safe and simple adversary emulation plan based on MITRE ATT&CK.

The scenario models selected attacker behaviors through three stages:

**Initial Access → Persistence → Data Exfiltration**

The purpose is to understand attacker behavior, map activities to MITRE ATT&CK techniques, and identify the telemetry and defensive detections that should be generated during the emulation.

---

## 2. Adversary Emulation

Adversary emulation is a structured exercise that reproduces selected attacker behaviors in a controlled environment.

The plan is based on threat intelligence and MITRE ATT&CK. It is designed to evaluate visibility, detection, and response rather than to perform an unrestricted penetration test.

---

## 3. Scope and Rules of Engagement

The emulation is limited to a controlled laboratory environment.

- Only authorized test systems are included.
- No real external systems are targeted.
- No real sensitive data is used.
- The activities are simulated for educational and defensive purposes.
- The emulation must not affect systems outside the laboratory environment.

---

## 4. Stage 1 — Initial Access

### Scenario

The simulated attacker attempts to obtain initial access to a target system through phishing.

### MITRE ATT&CK

**T1566 — Phishing**

The technique represents the use of phishing to deliver malicious content or trick a user into performing an action that provides an attacker with access.

### Expected Telemetry

The following evidence may be generated:

- Email security logs
- Phishing detection alerts
- User interaction events
- Endpoint security events

### Defensive Detection

A defender should monitor suspicious emails, malicious attachments or links, and unusual user activity associated with phishing.

---

## 5. Stage 2 — Persistence

### Scenario

After obtaining initial access, the simulated attacker attempts to maintain access to the system by using a Windows service.

### MITRE ATT&CK

**T1543.003 — Windows Service**

The technique represents the use of a Windows service for maintaining execution or persistence.

### Expected Telemetry

The following evidence may be generated:

- Windows service creation events
- Process creation logs
- Windows Event Logs
- Endpoint security alerts

### Defensive Detection

A defender should monitor the creation of new or unusual Windows services and correlate service creation with suspicious process activity.

---

## 6. Stage 3 — Data Exfiltration

### Scenario

The simulated attacker attempts to transfer selected test data from the compromised system to an external destination.

### MITRE ATT&CK

**T1041 — Exfiltration Over C2 Channel**

This technique represents transferring collected data through an existing command-and-control channel.

### Expected Telemetry

The following evidence may be generated:

- Network connection logs
- Firewall logs
- Proxy logs
- Endpoint network telemetry
- Unusual outbound traffic

### Defensive Detection

A defender should investigate unusual outbound connections, unexpected data transfers, and abnormal network communication from the affected host.

---

## 7. ATT&CK Mapping

| Stage | Simulated Activity | MITRE ATT&CK |
|---|---|---|
| Initial Access | Phishing | T1566 — Phishing |
| Persistence | Windows Service | T1543.003 — Windows Service |
| Data Exfiltration | Transfer data through C2 | T1041 — Exfiltration Over C2 Channel |

---

## 8. Expected Attack Flow

The emulation follows this simplified sequence:

**Initial Access → Persistence → Data Exfiltration**

1. The attacker obtains initial access through phishing.
2. The attacker establishes persistence using a Windows service.
3. The attacker transfers selected test data through a C2 channel.
4. Defensive monitoring is used to identify the expected telemetry.

---

## 9. Success Criteria

The emulation is considered successful if:

- The three stages are clearly defined.
- Each stage is mapped to a MITRE ATT&CK technique.
- Expected telemetry is identified.
- Possible defensive detections are identified.
- The activities remain within the authorized laboratory scope.

---

## 10. Defensive Perspective

The main purpose of the emulation plan is to understand what evidence an attacker would generate and whether defenders could detect these activities.

The plan can help security teams evaluate visibility, detection capabilities, and response procedures.

---

## 11. Conclusion

This assignment demonstrates how a threat scenario can be converted into a structured and controlled adversary emulation plan.

The scenario consists of three stages: Initial Access, Persistence, and Data Exfiltration. Each stage is mapped to a corresponding MITRE ATT&CK technique, and expected telemetry and defensive detections are identified.

The plan provides a safe and repeatable way to study attacker behavior without performing an unrestricted penetration test.

---

## 12. References

- MITRE ATT&CK — https://attack.mitre.org/
- MITRE Engenuity — Adversary Emulation resources
- MITRE CALDERA Documentation
- Course Lecture 8 — Creating a Plan to Emulate an Attacker's Action
