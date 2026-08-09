# Sophos Endpoint SOC Investigation Lab

![Sophos](https://img.shields.io/badge/Sophos-Endpoint-0A5CA8?style=for-the-badge&logo=sophos&logoColor=white)
![Windows](https://img.shields.io/badge/Windows-Endpoint-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![Active Directory](https://img.shields.io/badge/Active%20Directory-Lab-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![SOC](https://img.shields.io/badge/SOC-Investigation-111827?style=for-the-badge)
![Threat Analysis](https://img.shields.io/badge/Threat-Analysis-7C3AED?style=for-the-badge)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE%20ATT%26CK-Framework-EF4444?style=for-the-badge)

A home-lab project focused on understanding how **Sophos Endpoint and Sophos Central** protect Windows endpoints, generate security telemetry, and support SOC-style investigation and response.

Rather than simply testing whether Sophos can block a file, this lab focuses on understanding **how the platform detects, prevents, explains, and responds to security events** from the endpoint through the centralized console.

---

## 🎯 Lab Objective

The main objective of this lab is to understand Sophos from a **defender and SOC analyst perspective**.

The lab explores:

- How Sophos Endpoint protects Windows workstations
- How Sophos Central receives and presents security events
- How malware and potentially unwanted applications are detected
- How Threat Analysis Center detections can be investigated
- How Threat Graphs and threat lineage provide investigation context
- What endpoint, process, file, user, and host information is available during an investigation
- How Sophos responds by blocking or cleaning detected threats
- How multiple endpoint security controls can provide defense in depth
- How endpoint protection fits into a realistic Active Directory environment

The goal is not to generate as many alerts as possible. The goal is to **understand the security workflow behind the alerts**.

---

## 🏢 Lab Environment

The lab was built around a Windows-based Active Directory environment to make the endpoint testing closer to a small enterprise scenario.

### Environment

- Windows Server domain controller
- Active Directory domain
- Multiple organizational departments and user accounts
- Windows 10 endpoint joined to the domain
- Sophos Endpoint installed on the Windows endpoint
- Sophos Central used for centralized monitoring and investigation
- Controlled security test files and test pages from industry security-testing resources

Sophos Endpoint was deployed to the Windows endpoint using the Sophos Central installer, allowing the endpoint to be managed from the centralized Sophos environment.

The Active Directory users were then used as the identities behind different controlled security tests, allowing the investigation to consider **who was using the endpoint, which department they belonged to, what was detected, and how Sophos responded**.

---

## 🔐 Why Active Directory Was Included

Using individual local test accounts would demonstrate basic endpoint detection, but an enterprise endpoint does not exist in isolation.

The Active Directory environment adds useful investigation context:

**User → Department → Endpoint → Security Event → Detection → Investigation → Response**

For example, a malware test associated with a Finance user can be investigated differently from a test performed by an HR or Sales user because the investigation can include the affected identity and business context.

This makes the lab closer to the type of environment a SOC analyst would encounter in an organization.

---

## 🛡️ What Sophos Is Being Used For

Sophos Endpoint provides protection for managed workstations against threats such as malware, risky files and websites, and malicious network activity. 1

In this lab, the platform was explored from several angles:

### Endpoint Protection

Testing how the endpoint reacts when a controlled security test is introduced.

### Centralized Monitoring

Using Sophos Central to review security information from the managed endpoint.

### Threat Analysis

Using Threat Analysis Center to examine detections and their associated information.

### Threat Graph Investigation

Using Threat Graphs to understand how a detected threat developed and which processes or files were involved. Sophos describes Threat Graphs as a way to investigate the origin and progression of malware activity. 2

### Threat Lineage

Reviewing the process chain associated with a detection to understand what led to the security event. 3

### Response

Reviewing the protection action taken by Sophos, including blocking or cleaning detected threats.

---

## 🔎 Investigation Approach

Each investigation follows a simple SOC workflow:

```text
Controlled Test
      ↓
Endpoint Activity
      ↓
Sophos Detection / Prevention
      ↓
Sophos Central
      ↓
Detection / Threat Graph / Lineage
      ↓
Evidence Collection
      ↓
Analysis
      ↓
Response
      ↓
Investigation Closure
