# Week 5 — Threat Hunting: Suspicious PowerShell Activity

## 1. Hunting Scenario

This threat hunting scenario focuses on detecting suspicious PowerShell activity that may indicate attacker execution or defense evasion during a ransomware attack.

The scenario is related to the LockBit ransomware case study. PowerShell is investigated because attackers may use it to execute commands, run scripts, bypass security controls, or perform other malicious actions.

---

## 2. Hypothesis

The hypothesis is:

> An attacker associated with a ransomware attack may use suspicious PowerShell activity during execution or defense evasion.

The hunt will focus on PowerShell processes that use suspicious command-line parameters such as encoded commands, hidden execution, or execution policy bypass.

The objective is to determine whether the available endpoint telemetry contains activity that matches these indicators.

---

## 3. Why the Activity Is Suspicious

PowerShell activity is not inherently malicious, but certain command-line parameters can indicate suspicious execution.

The following indicators were selected for the hunt:

- `-EncodedCommand` — indicates that the PowerShell command is supplied in encoded form.
- `-NoP` — starts PowerShell without loading the user profile.
- `-W Hidden` — attempts to run the PowerShell window in hidden mode.
- `-ExecutionPolicy Bypass` — starts PowerShell while bypassing the configured execution policy.

The combination of these parameters can indicate an attempt to execute commands while reducing visibility or bypassing security controls.

The hunting scenario therefore searches for PowerShell processes containing these suspicious command-line parameters.

---

## 4. Data Source

The threat hunting was performed using Elasticsearch and Kibana in a local Docker environment.

The dataset contains controlled laboratory endpoint telemetry representing process execution events. The events include:

- Process name
- Process command line
- Parent process
- Host name
- User name
- Timestamp
- Event action

The dataset was created specifically for this training exercise. It does not represent real LockBit victim telemetry or a real-world compromised system.

The telemetry was used to demonstrate a hypothesis-driven hunting workflow in ELK.

---

## 5. Hunt Query

The first query was used to identify all PowerShell process executions:

`process.name : "powershell.exe"`

This query returned 3 PowerShell events in the laboratory dataset.

The second query was used to identify PowerShell activity containing suspicious command-line parameters:

`process.name : "powershell.exe" AND process.command_line : ("-EncodedCommand" OR "-ExecutionPolicy Bypass" OR "-nop" OR "-hidden")`

This query returned 2 events matching the defined hunting criteria.

The queries were executed in Kibana Discover using KQL (Kibana Query Language).

---

## 6. Query Execution

The hunting queries were executed in Kibana Discover.

The following steps were performed:

1. The `threat-hunting-lab` data view was selected.
2. The time range was changed to include the laboratory events.
3. The initial query was executed to identify PowerShell processes.
4. The second query was executed to identify suspicious PowerShell command-line parameters.
5. The resulting events were reviewed individually.

The initial query identified 3 PowerShell events.

The suspicious activity query reduced the results to 2 events that matched the defined hunting criteria.

Screenshots of the executed queries and their results are included as evidence of the hunting process.

---

## 7. Results

The suspicious activity query returned two events matching the hunting criteria.

### Event 1 — WIN-LAB-02

- Host: `WIN-LAB-02`
- User: `admin`
- Process: `powershell.exe`
- Parent process: `winword.exe`
- Command line: `powershell.exe -NoP -NonI -W Hidden -EncodedCommand TRAINING-LAB-ENCODED`
- Event action: `process-start`

The event contains several suspicious indicators: encoded PowerShell execution, hidden window execution, and execution without the normal PowerShell profile. The parent process is `winword.exe`, which makes the activity more suspicious in the context of a threat hunting investigation.

### Event 2 — WIN-LAB-03

- Host: `WIN-LAB-03`
- User: `admin`
- Process: `powershell.exe`
- Parent process: `explorer.exe`
- Command line: `powershell.exe -ExecutionPolicy Bypass -File C:\Users\Public\update.ps1`
- Event action: `process-start`

The event contains the `-ExecutionPolicy Bypass` parameter and executes a PowerShell script from the `C:\Users\Public\` directory. These characteristics matched the hunting criteria.

---

## 8. Analysis

The hunting results show that two PowerShell events matched the defined suspicious activity criteria.

The first event on `WIN-LAB-02` is the stronger detection. PowerShell was launched by `winword.exe` and used `-NoP`, `-NonI`, `-W Hidden`, and `-EncodedCommand`. The combination of a Microsoft Word parent process with encoded and hidden PowerShell execution is highly suspicious in an endpoint hunting scenario.

The second event on `WIN-LAB-03` used `-ExecutionPolicy Bypass` to execute a PowerShell script from `C:\Users\Public\`. This behavior may indicate an attempt to execute a script while bypassing normal PowerShell execution policy restrictions.

These events do not by themselves prove that a ransomware infection occurred. They are suspicious indicators that would require additional investigation, such as reviewing the parent process, user activity, network connections, downloaded files, and other endpoint events.

The results demonstrate how hypothesis-driven hunting can identify potentially malicious PowerShell activity from endpoint telemetry.

---

## 9. Hypothesis Validation

The hunting results support the hypothesis that an attacker may use suspicious PowerShell activity during execution or defense evasion.

The initial query identified 3 PowerShell process executions. The second query identified 2 events containing suspicious command-line parameters.

The most significant event was observed on `WIN-LAB-02`, where PowerShell was launched by `winword.exe` with hidden execution and an encoded command.

The event on `WIN-LAB-03` also matched the hypothesis because PowerShell was executed with `-ExecutionPolicy Bypass`.

Therefore, the hypothesis is considered supported within the controlled laboratory dataset.

However, the results do not confirm a real LockBit infection. The dataset was created for the training exercise, so further endpoint and network investigation would be required to establish a real compromise.

---

## 10. Defensive Recommendations

Based on the hunting results, the following defensive measures are recommended:

- Monitor PowerShell process creation and command-line arguments.
- Detect the use of `-EncodedCommand`, `-ExecutionPolicy Bypass`, hidden execution, and other suspicious PowerShell parameters.
- Monitor unusual parent-child process relationships, especially Office applications spawning PowerShell.
- Enable detailed PowerShell logging, including Script Block Logging and Module Logging where appropriate.
- Investigate PowerShell scripts executed from unusual locations such as `C:\Users\Public\`.
- Correlate PowerShell events with authentication, network, file, and endpoint security telemetry.
- Use MITRE ATT&CK technique `T1059.001 — PowerShell` to classify and track suspicious PowerShell activity.

---

## 11. References

1. Microsoft Security — Threat Hunting Guide  
   https://learn.microsoft.com/en-us/security/operations/advanced-hunting-overview

2. MITRE ATT&CK — T1059.001: PowerShell  
   https://attack.mitre.org/techniques/T1059/001/

3. Elastic Documentation — Kibana Query Language (KQL)  
   https://www.elastic.co/docs/reference/query-languages/kql

4. Elastic Documentation — Discover  
   https://www.elastic.co/docs/explore-analyze/discover

5. LockBit 3.0 — MITRE ATT&CK  
   https://attack.mitre.org/software/S1202/
