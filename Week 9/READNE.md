# Week 9 — Atomic Red Team: Introduction to Atomic Tests

## 1. Objective

The objective of this assignment was to explore Atomic Red Team, perform a controlled simulation of PowerShell command execution, collect Windows event logs, and analyze the results using the ELK Stack.

The main focus was MITRE ATT&CK technique **T1059.001 — PowerShell**.

## 2. Tools and Technologies

The following tools were used:

- **Atomic Red Team** — version 2.3.0
- **PowerShell** — Windows PowerShell 5.1
- **Winlogbeat** — version 9.5.6
- **Elasticsearch** — version 9.5.5
- **Kibana** — for event visualization and analysis
- **Windows Event Logs** — for collecting PowerShell activity

## 3. Atomic Red Team Installation

Atomic Red Team was installed using the PowerShell module `Invoke-AtomicRedTeam`.

The Atomic Red Team repository was also downloaded to examine available test definitions.

The selected scenario was:

- **Technique:** T1059.001
- **Name:** PowerShell
- **Atomic Test:** #17 — PowerShell Command Execution

The selected test demonstrates how an obfuscated PowerShell command can execute a command and display the message:

`Hello, from PowerShell!`

**Screenshot 1 — Atomic Test #17 on GitHub**

<img width="1412" height="656" alt="01_Atomic_Test_17_GitHub_description" src="https://github.com/user-attachments/assets/3ec9016c-7105-43f4-88e4-a5c04d18efb5" />
<img width="923" height="941" alt="02_Winlogbeat_Config_OK" src="https://github.com/user-attachments/assets/ab3b2dfb-8368-4efb-ad81-4758b78e9afd" />
<img width="923" height="941" alt="02_Winlogbeat_Config_OK" src="https://github.com/user-attachments/assets/ce0af6fe-6604-421f-a05e-db3a8b7ae8f1" />


## 4. ELK Stack Configuration

The ELK Stack was used to collect and analyze Windows event logs.

Elasticsearch was accessible through `localhost:9200`, and Kibana was accessible through `localhost:5601`.

A separate Elasticsearch index was created:

`atomic-red-team-lab`

Winlogbeat 9.5.6 was installed and configured to collect the following Windows event logs:

- Security
- Windows PowerShell
- Microsoft-Windows-PowerShell/Operational
- Microsoft-Windows-Sysmon/Operational (if available)

The Winlogbeat configuration was validated successfully using:

`winlogbeat.exe test config -c winlogbeat.yml -e`

The validation returned `Config OK`.

**Screenshot 2 — Winlogbeat Configuration Validation**

<img width="923" height="941" alt="02_Winlogbeat_Config_OK" src="https://github.com/user-attachments/assets/a14839ac-822d-47a8-be2d-19991f20d6eb" />


## 5. Windows Event Collection

Winlogbeat successfully connected to Elasticsearch and started forwarding Windows events.

The following Winlogbeat data stream was created:

`.ds-winlogbeat-9.5.6-2026.11.13-000001`

The collected events were displayed in Kibana using a dedicated Data View named `Atomic Red Team`.

**Screenshot 3 — Windows Events in Kibana**

<img width="1911" height="897" alt="03_Kibana_Windows_events" src="https://github.com/user-attachments/assets/bde67f58-b12d-4443-86bf-fb7eb7f48579" />


## 6. PowerShell Script Block Logging

PowerShell Script Block Logging was enabled to record executed PowerShell script blocks.

The following registry setting was configured:

`HKLM\SOFTWARE\Policies\Microsoft\Windows\PowerShell\ScriptBlockLogging`

The value `EnableScriptBlockLogging` was set to `1`.

This enabled Windows to generate PowerShell Script Block Logging events.

The main event analyzed in this assignment was:

**Event ID 4104 — Script Block Logging**

**Screenshot 4 — PowerShell Event ID 4104 in Kibana**
<img width="1915" height="912" alt="05_Atomic_test_command_detected" src="https://github.com/user-attachments/assets/68ea8944-8129-4240-ae75-4222e1f8fb6f" />
<img width="1915" height="912" alt="05_Atomic_test_command_detected" src="https://github.com/user-attachments/assets/6430baa7-a3ec-4ef9-9282-fae997635602" />
<img width="1915" height="912" alt="05_Atomic_test_command_detected" src="https://github.com/user-attachments/assets/95cc393a-2ee8-4a4f-8657-a4add5ee7369" />

<img width="1898" height="836" alt="04_PowerShell_Event_4104" src="https://github.com/user-attachments/assets/7eba2918-1b96-4c49-bdc6-238ffbaf00bc" />

## 7. Controlled Test Execution

The behavior of Atomic Test #17 was manually reproduced in a controlled Windows environment.

The following PowerShell command was used:

```powershell
$command = 'Invoke-Expression ("Write-Host ''Hello, from PowerShell!''")'
$encoded = [Convert]::ToBase64String([Text.Encoding]::Unicode.GetBytes($command))

Start-Process powershell.exe -ArgumentList "-NoProfile -EncodedCommand $encoded" -Wait
```

The command was executed through PowerShell using the `-EncodedCommand` parameter.

The expected output was:

`Hello, from PowerShell!`

**Important:** The original Atomic Test was not executed through the `Invoke-AtomicTest` command. Instead, its command-execution behavior was manually reproduced using a controlled PowerShell simulation.

**Screenshot 5 — PowerShell Command Execution**

<img width="1915" height="912" alt="05_Atomic_test_command_detected" src="https://github.com/user-attachments/assets/836401ac-9a48-4549-8508-765a0df96757" />


## 8. SIEM Analysis and Results

After executing the controlled test, Kibana Discover was used to search for PowerShell Script Block Logging events.

The following KQL query was used:

```text
event.code: "4104"
```

To identify the specific test activity, the following query was applied:

```text
event.code: "4104" AND powershell.file.script_block_text: "*Hello, from PowerShell!*"
```

The query returned **9 matching documents**.

The events contained references to:

- `Start-Process`
- `Invoke-Expression`
- `Write-Host`
- `Hello, from PowerShell!`

These results confirmed that Windows recorded the controlled PowerShell activity and that Winlogbeat successfully forwarded the events to Elasticsearch.

**Screenshot 6 — Detection of the Test Command in Kibana**

<img width="1915" height="912" alt="Снимок экрана 2026-11-14 000307" src="https://github.com/user-attachments/assets/af2b910a-d0d0-42c8-ac4f-5dabb39ea710" />


## 9. MITRE ATT&CK Mapping

| Attribute | Description |
|---|---|
| Tactic | Execution |
| Technique ID | T1059.001 |
| Technique Name | PowerShell |
| Data Source | Windows Event Logs |
| Event ID | 4104 |
| SIEM | Elasticsearch and Kibana |
| Detection Method | PowerShell Script Block Logging |

## 10. Conclusion

This assignment demonstrated how PowerShell activity can be monitored using Windows Event Logs and analyzed through the ELK Stack.

Winlogbeat successfully collected Windows events and forwarded them to Elasticsearch. Kibana was then used to identify Event ID 4104 records containing the test command.

The experiment demonstrated the importance of PowerShell Script Block Logging for detecting suspicious command execution.

Although the original Atomic Test was not executed through the Atomic Red Team framework, its command-execution behavior was manually reproduced for controlled monitoring and analysis.

## 11. References

- [Atomic Red Team — GitHub Repository](https://github.com/redcanaryco/atomic-red-team)
- [Invoke-AtomicRedTeam — GitHub Repository](https://github.com/redcanaryco/invoke-atomicredteam)
- [MITRE ATT&CK — T1059.001 PowerShell](https://attack.mitre.org/techniques/T1059/001/)
- [Elastic Winlogbeat Documentation](https://www.elastic.co/guide/en/beats/winlogbeat/current/index.html)
- [Microsoft — PowerShell Logging](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_logging)
