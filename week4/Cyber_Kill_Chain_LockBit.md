# Week 4 — Cyber Kill Chain Analysis: LockBit Ransomware

## 1. Introduction

This week focuses on analyzing a real-world cyberattack using the Cyber Kill Chain model and mapping each stage to corresponding MITRE ATT&CK techniques.

The case study for this analysis is LockBit ransomware.

The Cyber Kill Chain provides a high-level model of how a cyberattack progresses through different stages. MITRE ATT&CK provides a more detailed description of the tactics and techniques used by attackers.

The seven stages of the Cyber Kill Chain are:

1. Reconnaissance
2. Weaponization
3. Delivery
4. Exploitation
5. Installation
6. Command and Control
7. Actions on Objectives

---

## 2. LockBit Ransomware

LockBit is a ransomware family that has been used in real-world cyberattacks.

LockBit operates using a Ransomware-as-a-Service (RaaS) model, where different affiliates may use different techniques to gain access to victim environments.

The attack can include gaining initial access, executing malicious code, establishing persistence, moving through the network, disabling security controls, and encrypting data.

This analysis uses documented LockBit behavior to demonstrate how a ransomware attack can be mapped to the Cyber Kill Chain and MITRE ATT&CK.

---

## 3. Cyber Kill Chain and MITRE ATT&CK

The Cyber Kill Chain is used to describe the overall progression of a cyberattack.

MITRE ATT&CK is used to identify specific attacker techniques associated with different stages of the attack.

In this project:

- Cyber Kill Chain shows the **stage of the attack**.
- MITRE ATT&CK shows the **technique used by the attacker**.

Using both frameworks allows the attack to be analyzed at two levels: the overall attack lifecycle and the specific technical actions performed by the attacker.

---

## 4. Attack Flow

The LockBit attack can be represented using the following Cyber Kill Chain sequence:

```text
Reconnaissance
      ↓
Weaponization
      ↓
Delivery
      ↓
Exploitation
      ↓
Installation
      ↓
Command and Control
      ↓
Actions on Objectives

## 5. Stage 1 — Reconnaissance

Reconnaissance is the first stage of the Cyber Kill Chain.

During this stage, the attacker collects information about the target environment. The goal is to identify potential systems, services, vulnerabilities, and possible entry points.

For a LockBit attack, network and service discovery can help attackers understand the target environment and identify systems that may be useful for further operations.

### MITRE ATT&CK Mapping

**T1046 — Network Service Discovery**

This technique is used to identify network services and systems available in the target environment.

The information collected during this stage can help the attacker decide how to proceed with the attack.

### Defensive Controls

Organizations can reduce the risk of reconnaissance by:

- Monitoring unusual network scanning activity
- Restricting unnecessary network services
- Using firewalls
- Segmenting internal networks
- Monitoring publicly exposed systems
- Reviewing the organization's external attack surface

### Summary

The Reconnaissance stage helps the attacker understand the target environment before continuing to the next stages of the attack.

**Cyber Kill Chain:** Reconnaissance

**MITRE ATT&CK:** T1046 — Network Service Discovery
